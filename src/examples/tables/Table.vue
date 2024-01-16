<script setup>
defineProps({
  headers: {
    type: Array,
    default: () => ["Author", "Function", "Status", "Employed", "Action"],
  },
  rows: {
    type: Array,
    required: true,
    image: String,
    name: String,
    email: String,
    position: {
      type: Array,
      default: () => [],
    },
    status: Boolean,
    date: String,
    action: {
      type: Object,
      label: String,
      route: String,
    },
  },
});
</script>
<template>
  <section class="pt-2 mt-2">
    <div style="margin: 80px">
      <div class="row justify-content-center">
        <div class="col-lg-12">
          <div class="card">
            <div class="table-responsive">
              <table class="table align-items-center mb-0">
                <thead>
                  <tr>
                    <th
                      v-for="(header, index) in headers"
                      :key="header"
                      class="text-uppercase text-dark text-center font-weight-bolder opacity-10"
                      :class="{ 'ps-2': index == 1, 'text-center': index > 1 }"
                    >
                      {{ header }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="(
                      {
                        image,
                        name,
                        email,
                        position: [label1, label2],
                        status,
                        date,
                        action: { label, route },
                      },
                      index
                    ) of rows"
                    :key="index"
                  >
                    <td>
                      <div class="d-flex px-2 py-1">
                        <div>
                          <img :src="image" class="avatar avatar-sm me-3" />
                        </div>
                        <div class="d-flex flex-column justify-content-center">
                          <h6 class="mb-0 text-sm">{{ name }}</h6>
                          <p class="text-xs text-secondary mb-0">
                            {{ email }}
                          </p>
                        </div>
                      </div>
                    </td>
                    <td>
                      <p class="text-sm font-weight-bold mb-0">{{ label1 }}</p>
                      <p class="text-sm text-secondary mb-0">{{ label2 }}</p>
                    </td>
                    <td class="align-middle text-center text-sm">
                      <span
                        class="text-sm"
                        :class="status ? 'badge-dark' : 'badge-danger'"
                        >{{ status ? "ONLINE" : "OFFLINE" }}</span
                      >
                    </td>
                    <td class="align-middle text-center">
                      <span class="text-secondary text-sm font-weight-bold">{{
                        date
                      }}</span>
                    </td>
                    <td class="align-middle text-center">
                      <a
                        :href="route"
                        class="text-secondary font-weight-bold text-sm "
                        data-toggle="tooltip"
                        data-original-title="Edit user"
                      >
                        {{ label }}
                      </a>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
