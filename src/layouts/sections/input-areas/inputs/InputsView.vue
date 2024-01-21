<script setup>
import { onMounted } from "vue";

// Sections components
import BaseLayout from "../../components/BaseLayout.vue";
import View from "../../components/View.vue";
import Header from "../../../../examples/Header.vue";
import DefaultNavbar from "../../../../examples/navbars/NavbarDefault.vue";
import MaterialButton from "@/components/MaterialButton.vue";


// Inputs page components
import InputStatic from "./components/InputStatic.vue";
import InputDynamic from "./components/InputDynamic.vue";
import inputOutlined from "./components/InputOutlined.vue";
import InputIcon from "./components/InputIcon.vue";
import InputSuccess from "./components/InputSuccess.vue";
import InputError from "./components/InputError.vue";
import InputDisabled from "./components/InputDisabled.vue";

// Inputs page components codes
import {
  inputStaticCode,
  inputOutlinedCode,
  inputDynamicCode,
  inputSuccessCode,
  inputIconCode,
  inputErrorCode,
  inputDisabledCode,
} from "./components/codes";

//nav-pills & material-input
import setNavPills from "@/assets/js/nav-pills";
import setMaterialInput from "@/assets/js/material-input";

import image from "@/assets/img/nastuh.jpg";


//hook
onMounted(() => {
  setNavPills();
  setMaterialInput();
});
</script>
<template>
    <DefaultNavbar  transparent/>
  <Header>
    <div
      class="page-header min-height-200"
      :style="{ backgroundImage: `url(${image})` }"
      loading="lazy"
    >
      <span class="mask bg-gradient-dark opacity-8"></span>
    </div>
  </Header>

  <div class="card">
  <div class="card-header border-bottom">
    <div class="user d-flex align-items-center" >
      <div class="col-6" >
        <h5 class="mb-0 ms-0" >Información del pago</h5>
      </div>
      <div class="col-6 text-end" >

      </div>
    </div>
  </div>
</div>

  <section class="py-5">
    <div class="container ">

  <div class="card bg-gradient-light">
    <div class="card-body">
      <h6 class="mb-0 ms-0" >Reserva a: RUTA DE SILLAR</h6>
      <h6 class="mb-0 ms-0" >Monto Total:</h6><h3 class="mb-0 ms-0" >S/. 150.00 SOLES</h3>

    </div>
  </div>

 <div class="card">
  <div class="card-body">
    <!----><!----><div>
    <p class="card-title-desc">Complete toda la información a continuación</p><div>
      <div class="form-check form-check-inline font-size-16">
      <input class="form-check-input" type="radio" name="paymentoptionsRadio" id="paymentoptionsRadio1">
      <label class="form-check-label font-size-13" for="paymentoptionsRadio1"><i class="fab fa-cc-mastercard me-1 font-size-20 align-top"></i> Tarjeta de crédito / débito</label>
      </div>
      <div class="form-check form-check-inline font-size-16">
        <input class="form-check-input" type="radio" name="paymentoptionsRadio" id="paymentoptionsRadio2">
        <label class="form-check-label font-size-13" for="paymentoptionsRadio2"><i class="fab fa-cc-paypal me-1 font-size-20 align-top"></i> Paypal / Yape</label>
      </div><div class="form-check form-check-inline font-size-16">
        <input class="form-check-input" type="radio" name="paymentoptionsRadio" id="paymentoptionsRadio3">
        <label class="form-check-label font-size-13" for="paymentoptionsRadio3"><i class="far fa-money-bill-alt me-1 font-size-20 align-top"></i> Efectivo</label>
        </div>
        </div>
        <h5 class="mt-5 mb-3 font-size-15">Para pago con tarjeta</h5><div class="p-4 border">
          <form class="">
            <div class="mb-0" id="input-group-2" role="group">

            <div class="row justify-space-between py-2">
                <div class="col-lg-12 mx-auto">
                    <div class="input-group input-group-static mb-4">
                        <label>Número de tarjeta</label>
                        <input class="form-control" 
                        type="text" 
                         placeholder="0000 0000 0000 0000"
                          >
                    </div>
                </div>
             </div>

            </div>
            <div class="row">
                      <div class="col-md-4">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre en la tarjeta</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="Name on Card">
                          </div>
                        </div>
                      </div>


                      </div>
                      <div class="col-md-4 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Fecha de caducidad</label>
                            <input class="form-control" 
                            type="text" 
                            placeholder="MM/YY"
                            >
                          </div>
                        </div>
                      </div>
                     
                      </div>

                      <div class="col-md-4 ps-md-2">

                        <div class="row justify-space-between py-2">
                          <div class="col-lg-12 mx-auto">
                            <div class="input-group input-group-static mb-4">
                              <label>CVV Code</label>
                              <input class="form-control" 
                              type="text" 
                              placeholder="Enter CVV Code"
                              >
                            </div>
                          </div>
                        </div>

                        </div>
              </div>

                        </form>
                        </div>
                        </div>
                                                <div class=" justify-space-end py-5">
        <MaterialButton
            variant="gradient"
            color="success"
            data-bs-toggle="modal"
            data-bs-target="#exampleModal">
            <i class="fas fa-plane me-2"  aria-hidden="true"></i> Realizar el Pago
        </MaterialButton>
      </div>
                        </div>

    </div>
      
  </div>
  </section>
</template>
