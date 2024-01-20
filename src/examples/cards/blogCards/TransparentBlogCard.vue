<script setup>
defineProps({
  image: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  action: {
    type: Object,
    route: String,
    color: String,
    label: String,
    default: () => ({
      route: "page-headers",
      color: "success",
      label: "Mostrar mas",
    }),
  },
});
</script>
<template>
  <div class="card card-plain">
    <div class="card-header p-0 position-relative">
      <a class="d-block blur-shadow-image">
        <img
          :src="image"
          :alt="title"
          class="img-fluid shadow border-radius-lg"
          loading="lazy"
        />
      </a>
    </div>
    <div class="card-body px-0">
      <h5>
        <a :href="action.route" class="text-dark font-weight-bold">{{
          title
        }}</a>
      </h5>
      <p>
        {{ description }}
      </p>
      <a
        href="http://localhost:4000/sections/page-sections/page-headers"
        class="text-sm icon-move-right"
        :class="`text-${action.color}`"
        >{{ action.label }}
        <i class="fas fa-arrow-right text-xs ms-1"></i>
      </a>
    </div>
  </div>
</template>
