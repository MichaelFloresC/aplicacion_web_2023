<script setup>
// Vue Material Kit 2 component
import Header from "../../../../examples/Header.vue";
import DefaultNavbar from "../../../../examples/navbars/NavbarDefault.vue";
import MaterialButton from "@/components/MaterialButton.vue";
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialTextArea from "@/components/MaterialTextArea.vue";
import DefaultReviewCard from "@/examples/cards/reviewCards/DefaultReviewCard.vue";

// images
import team2 from "@/assets/img/team-2.jpg";
import team3 from "@/assets/img/team-3.jpg";
import team4 from "@/assets/img/team-4.jpg";
import image from "@/assets/img/nastuh.jpg";

</script>
<script>
import axios from "axios";
export default {
  data() {
 
        return {    
          datoEditado :{},        
            dogs: [],
            newDog: {},
            backend_server: 'http://127.0.0.1:3000'
        }
    },
    methods:{
      abrirModal(dato) {
          this.mostrarModal = true;
          this.datoEditado = { ...dato }; // Copiar el dato para editar
          console.log(this.mostrarModal);
          console.log(this.datoEditado);
        },
        addDog(e){
            e.preventDefault(); 
            var config_request={'Content-Type': 'application/json','Access-Control-Allow-Origin': '*'}

            axios.post(this.backend_server + '/tours', this.newDog, { config_request })
            .then(res => {                                         
                this.dogs.push(this.newDog);
                this.newDog = {};
            })
            .catch((error) => {
                console.log(error)
            });    
            
        },
        deleteDog(dog){
            var config_request={'Content-Type': 'application/json','Access-Control-Allow-Origin': '*'}

            axios.delete(this.backend_server + '/tours/' + dog._id, {}, { config_request })
            .then(res => {                                         
                this.dogs.splice(this.dogs.indexOf(dog), 1);
            })
            .catch((error) => {
                console.log(error)
            });  
        },
        updateDog(e){
            e.preventDefault();
            var config_request={'Content-Type': 'application/json','Access-Control-Allow-Origin': '*'}
            var id =this.datoEditado._id;
            delete this.datoEditado._id;
            axios.patch(this.backend_server + '/tours/' + id, this.datoEditado, { config_request })
            .then(res => {                                         
                this.dogs.splice(this.dogs.indexOf(this.datoEditado), 1,this.datoEditado);
                this.datoEditado = {};
                console.log(this.dogs);
            })
            .catch((error) => {
                console.log(error)
            });  
        }
    },
    
    created(){                
        axios.get(this.backend_server + "/tours")
        .then(res => {
            this.dogs = res.data;
            console.log(this.dogs);
        });
    }

}
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
        <h5 class="mb-0 ms-0" >Destinos Turisticos</h5>
      </div>
      <div class="col-6 text-end" >
    <!--<button class="btn mb-0 btn-success btn-md null null float-right btn btm-sm" >
          <i class="fas fa-user-plus me-2"  aria-hidden="true"></i> añadir Usuario 
        </button>-->
        <MaterialButton
          variant="gradient"
          color="success"
          data-bs-toggle="modal"
          data-bs-target="#exampleModal">
          <i class="fas fa-plane me-2"  aria-hidden="true"></i> añadir Destinos 
        </MaterialButton>
      </div>
    </div>
  </div>

<ul style="list-style: none;">
<li v-for="tour in dogs" :key="tour._id" >

  <section class="py-5">
    <div class="container">
      <div class="row align-items-center">

        <div class="col-lg-4 mt-lg-0 mt-5 ps-lg-0 ps-0">
          <img class="w-100 border-radius-md shadow-lg" :src=tour.url_image alt="Emma Roberts">
        </div>

        <div class="col-lg-6 my-auto">
          <h3>{{ tour.nombre_completo}}</h3>
          <p class="pe-5">
            {{ tour.detalle }}
          </p>
          <a href="javascript:;" class="text-success icon-move-right"
            >Reserva Ahora
            <i class="fas fa-arrow-right text-sm ms-1"></i>
          </a>
        </div>

        <div class="col-md-2"> 
          <MaterialButton variant="contained" color="light" class="w-auto me-2 px-3 mb-0" data-bs-toggle="modal" data-bs-target="#exampleModal2" v-on:click='abrirModal(tour)' >
                <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>
                Editar
              </MaterialButton>
              <br><br>
              <MaterialButton variant="contained" color="light" class="w-auto me-2 text-danger px-3 mb-0" v-on:click='deleteDog(tour)'>
              <i class="far fa-trash-alt me-2" aria-hidden="true"></i>
                Borrar
              </MaterialButton>
        </div>
        
      </div>
    </div>
  </section>
</li>
</ul>
  

</div>

 <!-- Modal #1-->
 <div
          class="modal fade"
          id="exampleModal"
          tabindex="-1"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">
                  Registrar
                </h5>
                <MaterialButton
                variant="outline" color="dark" size="sm"
                  class=" text-dark"
                  data-bs-dismiss="modal"
                  aria-label="Close">X
                </MaterialButton>
              </div>
              <div class="modal-body">

                <form id="contact-form" method="post" autocomplete="off" v-on:submit='addDog'>
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-9">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre completo del destino</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="newDog.nombre_completo"
                            >
                          </div>
                        </div>
                      </div>


                      </div>
                      <div class="col-md-3 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>codigo</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="newDog.nombre_corto"
                            >
                          </div>
                        </div>
                      </div>
                     
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-12">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>URL Imagen</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="newDog.url_image"
                            >
                          </div>
                        </div>
                      </div>
                       
                      </div>
                    </div>

                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <label>Detalle del destino</label>
                      <textarea
                        id="message"
                        class="form-control"
                        :rows="2"
                        placeholder="Describe el recorrido programado"
                        v-model="newDog.detalle"
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

<!-- Modal #2-->
<div
          class="modal fade"
          id="exampleModal2"
          tabindex="-1"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">
                  Actualizar
                </h5>
                <MaterialButton
                variant="outline" color="dark" size="sm"
                  class=" text-dark"
                  data-bs-dismiss="modal"
                  aria-label="Close">X
                </MaterialButton>
              </div>
              <div class="modal-body">

                <form id="contact-form" method="post" autocomplete="off" v-on:submit='updateDog'>
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-9">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre completo del destino</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="datoEditado.nombre_completo"
                            >
                          </div>
                        </div>
                      </div>


                      </div>
                      <div class="col-md-3 ps-md-2">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>codigo</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="datoEditado.nombre_corto"
                            >
                          </div>
                        </div>
                      </div>
                     
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-12">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>URL Imagen</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="datoEditado.url_image"
                            >
                          </div>
                        </div>
                      </div>
                       
                      </div>
                    </div>

                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <label>Detalle del destino</label>
                      <textarea
                        id="message"
                        class="form-control"
                        :rows="2"
                        placeholder="Describe el recorrido programado"
                        v-model="datoEditado.detalle"
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

</template>
