<script setup>
import { onMounted } from "vue";

//example components
import DefaultNavbar from "@/examples/navbars/NavbarDefault.vue";
import DefaultFooter from "@/examples/footers/FooterDefault.vue";

//image
import image from "@/assets/img/illustrations/illustration-signin.jpg";

//material components
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialTextArea from "@/components/MaterialTextArea.vue";
import MaterialButton from "@/components/MaterialButton.vue";

// material-input
import setMaterialInput from "@/assets/js/material-input";
onMounted(() => {
  setMaterialInput();
});
</script>
<template>
  <div class="align-items-center " 
  style="backgroundImage:url('https://perutherichestcountry.peru.travel/Contenido/Destino/Imagen/nl/154/1.1/Principal/shutterstock_306747452.jpg')"
      loading="lazy">

      <div class="container">
        <div class="row">

          <div
            class="mt-12 col-xl-5 col-lg-6 col-md-7 d-flex flex-column ms-auto me-auto ms-lg-auto "
          >
            <div
              class="card d-flex blur justify-content-center shadow-lg my-sm-0 my-sm-6 mt-8 mb-5"
            >
              <div
                class="card-header p-0 position-relative mt-n4 mx-3 z-index-2 bg-transparent"
              >
                <div
                  class="bg-gradient-success shadow-success border-radius-lg p-3"
                >
                  <h3 class="text-white text-success mb-0">REGISTRARSE</h3>
                </div>
              </div>
              <div class="card-body">
                <p class="pb-3">
                  Ingrese sus datos completos
                </p>
                <form id="contact-form" method="post" autocomplete="off" v-on:submit='addDog'>
                  <div class="card-body">
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>USUARIO</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>


                      </div>
                      <div class="col-md-6 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>CONTRASEÑA</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>
                     
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>


                      </div>
                      <div class="col-md-6 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Apellido</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>
                     
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Correo</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>
                       
                      </div>
                      <div class="col-md-6 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Pais</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>

                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Ciudad</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>
                       
                      </div>
                      <div class="col-md-6 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Idioma</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="-">
                          </div>
                        </div>
                      </div>

                      </div>
                    </div>
                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <label>Otro Datos</label>
                      <textarea
                        id="message"
                        class="form-control"
                        :rows="2"
                        placeholder="Describe informacion adicional que no se haya registrado"
                        ></textarea
                      >
                    </div>

                  </div>
                  <div class="modal-footer justify-content-center">

                    <MaterialButton variant="gradient" color="success" class="mb-0"  data-bs-dismiss="modal">
                      Guardar cambios
                    </MaterialButton>
                </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
</div>
  <DefaultFooter />
</template>
