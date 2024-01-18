<script setup>
import { onMounted } from "vue";
// example components
import DefaultNavbar from "@/examples/navbars/NavbarDefault.vue";
import Header from "@/examples/Header.vue";
import MaterialBadge from "@/components/MaterialBadge.vue";

//Vue Material Kit 2 components
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialSwitch from "@/components/MaterialSwitch.vue";
import MaterialButton from "@/components/MaterialButton.vue";

// material-input
import setMaterialInput from "@/assets/js/material-input";
onMounted(() => {
  setMaterialInput();
});
</script>
<script>
export default {
  data() {
    return {
      usuario: '',
      password: '',
      mostrarDiv: false
    };
  },
  methods: {
    acceder() {
      console.log("usuario: "+this.usuario)
      console.log("contra: "+this.password)
      if(this.usuario=="admin"){
        this.$router.push('/');
        console.log("usuario admin aceptado")
      }
      else{
        this.mostrarDiv=!this.mostrarDiv;
        console.log("usuario no aceptado")
      }

    }
  }
}
</script>
<template>
  <Header>
    <div
      class="page-header align-items-start min-vh-100"
      :style="{
        backgroundImage:
          'url(https://perutherichestcountry.peru.travel/Contenido/Destino/Imagen/nl/154/1.1/Principal/shutterstock_306747452.jpg)'
      }"
      loading="lazy"
    >
      <span class="mask bg-gradient-dark opacity-2"></span>
      <div class="container my-auto">
        <div class="row">
          <div class="col-lg-4 col-md-8 col-12 mx-auto">
            <div class="card z-index-0 fadeIn3 fadeInBottom">
              <div
                class="card-header p-0 position-relative mt-n4 mx-3 z-index-2"
              >
                <div
                  class="bg-gradient-dark shadow-success border-radius-lg py-3 pe-1 "
                >
                  <h4
                    class="text-white font-weight-bolder text-center mt-2 mb-0"
                  >
                    MISTI TOURS
                  </h4>
                  <div class="row mt-3">
                    <div class="col-2 text-center ms-auto">
                      <a class="btn btn-link px-3" href="javascript:;">
                        <i class="fa fa-facebook text-white text-lg"></i>
                      </a>
                    </div>
                    <div class="col-2 text-center px-1">
                      <a class="btn btn-link px-3" href="javascript:;">
                        <i class="fa fa-github text-white text-lg"></i>
                      </a>
                    </div>
                    <div class="col-2 text-center me-auto">
                      <a class="btn btn-link px-3" href="javascript:;">
                        <i class="fa fa-google text-white text-lg"></i>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
              <div class="card-body">
                  <!--<MaterialInput 
                    id="usuario"
                    class="input-group-outline my-3"
                    :label="{ text: 'usuario', class: 'form-label' }"
                    type="email"
                    v-model="usuario"
                    <MaterialInput
                    id="password"
                    class="input-group-outline mb-3"
                    :label="{ text: 'contraseña', class: 'form-label' }"
                    type="password"
                    v-model="password"
                  />
                  />
                    -->
                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-outline mb-2">
                            <label class="form-label">usuario</label>
                            <input class="form-control" 
                            v-model="usuario"
                            type="text" >
                          </div>
                        </div>
                      </div>

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-outline mb-2">
                            <label class="form-label">contraseña</label>
                            <input class="form-control" 
                              v-model="password"
                              type="password" 
                              >
                          </div>
                        </div>
                      </div>

                  <MaterialSwitch
                    class="d-flex align-items-center mb-3"
                    id="rememberMe"
                    labelClass="mb-0 ms-3"
                    checked
                    >recordarme</MaterialSwitch
                  >

                  <div class="text-center" v-show="mostrarDiv">
                    <MaterialBadge size="sm" variant="gradient" color="danger">
                      Usuario o contraseña incorrectos
                    </MaterialBadge>
                  </div>

                  <div class="text-center">
                    <MaterialButton
                      class="my-4 mb-2"
                      variant="gradient"
                      color="dark"
                      fullWidth
                      @click="acceder()"
                      >Iniciar sesión</MaterialButton
                    >
                  </div>

                  <p class="mt-4 text-sm text-center">
                    ¿No tienes una cuenta?
                    <a
                      href="http://localhost:4000"
                      class="text-success text-gradient font-weight-bold"
                      >Registrate</a
                    >
                  </p>

              </div>
            </div>
          </div>
        </div>
      </div>
      
    </div>
  </Header>
</template>
