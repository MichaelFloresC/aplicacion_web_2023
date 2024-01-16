<script setup>
import { onMounted } from "vue";
//Vue Material Kit 2 components
import MaterialButton from "@/components/MaterialButton.vue";
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialTextArea from "@/components/MaterialTextArea.vue";

// image
import bgContact from "@/assets/img/examples/blog2.jpg";

// tooltip
import setTooltip from "@/assets/js/tooltip";

// store
import { useAppStore } from "@/stores";
const store = useAppStore();

onMounted(() => {
  setTooltip(store.bootstrap);
});
</script>
<template>
  <section class="py-lg-5">
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="card box-shadow-xl overflow-hidden mb-5">
            <div class="row">
              <div
                class="col-lg-5 position-relative bg-cover px-0"
                :style="{ backgroundImage: `url(${bgContact})` }"
                loading="lazy"
              >
                <div
                  class="z-index-2 text-center d-flex h-100 w-100 d-flex m-auto justify-content-center"
                >
                  <div class="mask bg-gradient-dark opacity-8"></div>
                  <div
                    class="p-5 ps-sm-8 position-relative text-start my-auto z-index-2"
                  >
                    <h3 class="text-white">Información del contacto</h3>
                    <p class="text-white opacity-8 mb-4">
                      Complete el formulario y nuestro equipo se comunicará con usted dentro de
                      24 horas.
                    </p>
                    <div class="d-flex p-2 text-white">
                      <div>
                        <i class="fas fa-phone text-sm"></i>
                      </div>
                      <div class="ps-3">
                        <span class="text-sm opacity-8">(+54) 698421</span>
                      </div>
                    </div>
                    <div class="d-flex p-2 text-white">
                      <div>
                        <i class="fas fa-envelope text-sm"></i>
                      </div>
                      <div class="ps-3">
                        <span class="text-sm opacity-8"
                          >mistitours@gmail.com</span
                        >
                      </div>
                    </div>
                    <div class="d-flex p-2 text-white">
                      <div>
                        <i class="fas fa-map-marker-alt text-sm"></i>
                      </div>
                      <div class="ps-3">
                        <span class="text-sm opacity-8"
                          >Santa Catalina, Cercado #1005</span
                        >
                      </div>
                    </div>
                    <div class="mt-4">
                      <MaterialButton
                        color="none"
                        size="lg"
                        class="btn-icon-only btn-link text-white mb-0"
                        data-toggle="tooltip"
                        data-placement="bottom"
                        data-original-title="Log in with Facebook"
                      >
                        <i class="fab fa-facebook"></i>
                      </MaterialButton>
                      <MaterialButton
                        color="none"
                        size="lg"
                        class="btn-icon-only btn-link text-white mb-0"
                        data-toggle="tooltip"
                        data-placement="bottom"
                        data-original-title="Log in with Twitter"
                      >
                        <i class="fab fa-twitter"></i>
                      </MaterialButton>
                      <MaterialButton
                        color="none"
                        size="lg"
                        class="btn-icon-only btn-link text-white mb-0"
                        data-toggle="tooltip"
                        data-placement="bottom"
                        data-original-title="Log in with Dribbble"
                      >
                        <i class="fab fa-dribbble"></i>
                      </MaterialButton>
                      <MaterialButton
                        color="none"
                        size="lg"
                        class="btn-icon-only btn-link text-white mb-0"
                        data-toggle="tooltip"
                        data-placement="bottom"
                        data-original-title="Log in with Instagram"
                      >
                        <i class="fab fa-instagram"></i>
                      </MaterialButton>
                    </div>
                  </div>
                </div>
              </div>
              <div class="col-lg-7">
                <form class="p-3" id="contact-form" method="post">
                  <div class="card-header px-4 py-sm-5 py-3">
                    <h2>¡Di hola!</h2>
                    <p class="lead">Nos gustaría hablar con usted.</p>
                  </div>
                  <div class="card-body pt-1">
                    <div class="row">
                      <div class="col-md-12 pe-2 mb-3">
                        <MaterialInput
                          class="input-group-static mb-4"
                          label="Mi nombre es"
                          type="text"
                          placeholder="Nombre completo"
                        />
                      </div>
                      <div class="col-md-12 pe-2 mb-3">
                        <MaterialInput
                          class="input-group-static mb-4"
                          label="Estoy buscando"
                          type="text"
                          placeholder="A donde deseas viajar"
                        />
                      </div>
                      <div class="col-md-12 pe-2 mb-3">
                        <MaterialTextArea
                          class="input-group-static mb-4"
                          placeholder="Quiero incluir en mi viaje..."
                          :rows="6"
                          >tu mensaje</MaterialTextArea
                        >
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6 text-end ms-auto">
                        <MaterialButton
                          variant="gradient"
                          color="success"
                          type="submit"
                          class="mb-0"
                          >Enviar Mensaje</MaterialButton
                        >
                      </div>
                    </div>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
