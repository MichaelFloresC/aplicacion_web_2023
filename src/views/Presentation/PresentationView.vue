<script setup>
import { onMounted, onUnmounted } from "vue";

//example components
import NavbarDefault from "../..//examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../examples/footers/FooterDefault.vue";
import Header from "../../examples/Header.vue";
import FilledInfoCard from "../../examples/cards/infoCards/FilledInfoCard.vue";
import DefaultReviewCard from "@/examples/cards/reviewCards/DefaultReviewCard.vue";
import MaterialInput from "@/components/MaterialInput.vue";

//Vue Material Kit 2 components
import MaterialSocialButton from "@/components/MaterialSocialButton.vue";
import MaterialButton from "@/components/MaterialButton.vue";

// sections
import PresentationCounter from "./Sections/PresentationCounter.vue";
import PresentationPages from "./Sections/PresentationPages.vue";
import PresentationExample from "./Sections/PresentationExample.vue";
import data from "./Sections/Data/designBlocksData";
import BuiltByDevelopers from "./Components/BuiltByDevelopers.vue";
import PresentationInformation from "./Sections/PresentationInformation.vue";
import Posts from "../LandingPages/Author/Sections/AuthorPosts.vue";

//images
import presentBanner from "@/assets/img/present_banner.jpg";
import vueMkHeader from "@/assets/img/vue-mk-header.jpg";
import wavesWhite from "@/assets/img/waves-white.svg";
import logoBootstrap from "@/assets/img/logos/bootstrap5.jpg";
import logoTailwind from "@/assets/img/logos/icon-tailwind.jpg";
import logoVue from "@/assets/img/logos/vue.jpg";
import logoAngular from "@/assets/img/logos/angular.jpg";
import logoReact from "@/assets/img/logos/react.jpg";
import logoSketch from "@/assets/img/logos/sketch.jpg";

//hooks
const body = document.getElementsByTagName("body")[0];
onMounted(() => {
  body.classList.add("presentation-page");
  body.classList.add("bg-gray-200");
});
onUnmounted(() => {
  body.classList.remove("presentation-page");
  body.classList.remove("bg-gray-200");
});
</script>
<script>
import axios from "axios";
export default {
  data() {
 
        return {            
            dogs: [],
            newDog: {nombre:"Admin"},
            backend_server: 'http://127.0.0.1:3000'
        }
    },
    methods:{
        addDog(e){
            e.preventDefault(); 
            var config_request={'Content-Type': 'application/json','Access-Control-Allow-Origin': '*'}

            axios.post(this.backend_server + '/comentarios', this.newDog, { config_request })
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

            axios.delete(this.backend_server + '/comentarios/' + dog._id, {}, { config_request })
            .then(res => {                                         
                this.dogs.splice(this.dogs.indexOf(dog), 1);
            })
            .catch((error) => {
                console.log(error)
            });  
        }
    },
    created(){                
        axios.get(this.backend_server + "/comentarios")
        .then(res => {
            this.dogs = res.data;
            console.log(this.dogs);
        });
    }

}
</script>
<template>
  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault :sticky="true" />
      </div>
    </div>
  </div>
  <Header>
    <div
      class="page-header min-vh-75"
      :style="`background-image: url(${presentBanner})`"
      loading="lazy"
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-7 text-center mx-auto position-relative">
            <h1
              class="text-black pt-3 mt-n5 me-2"
              :style="{ display: 'inline-block ' }"
            >
              MISTI TOURS
            </h1>
            <p class="lead text-black px-5 mt-3" :style="{ fontWeight: '500' }">
              Comienza nuevas aventuras con todo preparado para ti
            </p>
          </div>
        </div>
      </div>
    </div>
  </Header>

  <div class="card card-body blur shadow-blur mx-3 mx-md-4 mt-n6">
    <PresentationCounter />
    <Posts />

    <section class="py-7">
      <div class="container">

      <div class="row">
        <div class="col-lg-6 mx-auto text-center">
          <h2 class="mb-0">Comentarios</h2>
          <h2 class="text-gradient text-success mb-3">
            
          </h2>
          <p class="lead">
           
          </p>
        </div>
      </div>

      <h5>Agregar Comentario</h5>
      <br>
      <form id="contact-form" method="post" autocomplete="off" v-on:submit='addDog'>
        
        <div class="row align-items-center">
                      <div class="col-md-8">

                        <div class="row justify-space-between py-2">
                          <div class="col-lg-12 mx-auto">
                            <div class="input-group input-group-static">
                              <input class="form-control" 
                              type="text" 
                              v-model="newDog.comentario"
                              placeholder="Agrege aqui su comentario">
                            </div>
                          </div>
                        </div>

                      </div>
                      <div class="col-md-2 ps-md-2">
                       
                        <div class="row justify-space-between py-2">
                          <div class="col-lg-12 mx-auto">
                            <div class="input-group input-group-static">
                              <input class="form-control" 
                              type="text" 
                              v-model="newDog.correo"
                              placeholder="Correo">
                            </div>
                          </div>
                        </div>

                      </div>
                      <div class="col-md-2 ps-md-2">
                        <select v-model="newDog.calificacion" >
                          <option disabled selected>Selecciona una opción</option>
                          <option value="1">1 estrella</option>
                          <option value="2">2 estrellas</option>
                          <option value="3">3 estrellas</option>
                          <option value="4">4 estrellas</option>
                          <option value="5">5 estrellas</option>
                        </select>
                      </div>
                    </div>
                    <div class="py-3">
                      <MaterialButton variant="gradient" color="primary" class="mb-0">
                        Agregar Comentario
                      </MaterialButton>
                  </div>
        </form>
      

      <ul style="list-style: none;">
        <li v-for="comment in dogs" :key="comment._id"   >
          <div class="row align-items-center">
            <div class="col-md-10">
              <DefaultReviewCard
                    :name="comment.nombre"
                    :date="comment.correo"
                    :review="comment.comentario"
                    :rating="comment.calificacion"
                    />
            </div>
            <div class="col-md-2"> 
              <MaterialButton variant="contained" color="light" class="w-auto me-2 text-danger px-3 mb-0" v-on:click='deleteDog(comment )'>
              <i class="far fa-trash-alt me-2" aria-hidden="true"></i>
                Borrar
              </MaterialButton>
            </div>
          </div>

         
        </li>
      </ul>


</div>
</section>


  </div>
  <DefaultFooter />
</template>
