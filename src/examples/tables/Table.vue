<script setup>nombre
defineProps({
  headers: {
    type: Array,
    default: () => ["Author", "Function", "Status", "Employed", "Action"],
  },
  rows: {
    type: Array,
    required: true,
    image: String,
    nombre: String,
    apellido: String,
    correo: String,
    pais: String,
    ciudad: String,
    idioma: String,
    observaciones: String,
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
                        nombre,
                        correo,
                        apellido,
                        pais,
                        ciudad,
                        idioma,
                        observaciones,
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
                          <h6 class="mb-0 text-sm">{{ nombre }} {{ apellido }}</h6>
                          <p class="text-xs text-secondary mb-0">
                            {{ correo }}
                          </p>
                        </div>
                      </div>
                    </td>
                    <td>
                      <p class="text-sm font-weight-bold mb-0">{{ pais }}</p>
                      <p class="text-sm text-secondary mb-0">{{ ciudad }}</p>
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
                        idioma
                      }}</span>
                    </td>
                    <td class="align-middle text-center">
                      <!--
                      <a
                        :href="route"
                        class="text-secondary font-weight-bold text-sm "
                        data-toggle="tooltip"
                        data-original-title="Edit user"
                      >
                        {{ label }}
                      </a>
-->
                      <a class="btn btn-link text-dark px-3 mb-0" href="javascript:;">
                        <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>Editar 
                      </a>

                      <a class="btn btn-link text-danger text-gradient px-3 mb-0" href="javascript:;">
                        <i class="far fa-trash-alt me-2" aria-hidden="true">
                      </i>Delete 
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
