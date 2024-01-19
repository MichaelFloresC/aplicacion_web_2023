<script setup>
// Vue Material Kit 2 component
import Header from "../../../../examples/Header.vue";
import DefaultNavbar from "../../../../examples/navbars/NavbarDefault.vue";
import MaterialButton from "@/components/MaterialButton.vue";
import MaterialInput from "@/components/MaterialInput.vue";
import MaterialTextArea from "@/components/MaterialTextArea.vue";

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
          mostrarModal: false, 
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
            console.log(this.newDog);
            
            axios.post(this.backend_server + '/usuarios', this.newDog, { config_request })
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

            axios.delete(this.backend_server + '/usuarios/' + dog._id, {}, { config_request })
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
            axios.patch(this.backend_server + '/usuarios/' + id, this.datoEditado, { config_request })
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
        axios.get(this.backend_server + "/usuarios")
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
        <h5 class="mb-0 ms-0" >Usuarios</h5>
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
          <i class="fas fa-user-plus me-2"  aria-hidden="true"></i> añadir Usuario 
        </MaterialButton>
      </div>
    </div>
  </div>
  
  <section class="pt-2 mt-2">
    <div style="margin: 80px">
      <div class="row justify-content-center">
        <div class="col-lg-12">
          <div class="card">
            <div class="table-responsive">
              <table class="table align-items-center mb-0">
                <thead>
                  <tr>
                    <th class="text-uppercase text-dark text-center font-weight-bolder opacity-10">
                      NOMBRES
                    </th>
                    <th class="text-uppercase text-dark text-center font-weight-bolder opacity-10">
                      CORREO
                    </th>
                    <th class="text-uppercase text-dark text-center font-weight-bolder opacity-10">
                      NACIONALIDAD
                    </th>
                    <th class="text-uppercase text-dark text-center font-weight-bolder opacity-10">
                      IDIOMA
                    </th>
                    <th class="text-uppercase text-dark text-center font-weight-bolder opacity-10">
                      ACCIONES
                    </th>

                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="usuario in dogs"
                    :key="usuario._id"
                  >
                    <td>
                      <div class="d-flex px-2 py-1">
                        <div>
                          <img :src="team2" class="avatar avatar-sm me-3" />
                        </div>
                        <div class="d-flex flex-column justify-content-center">
                          <h6 class="mb-0 text-sm">{{ usuario.nombre }} {{ usuario.apellido }}</h6>

                        </div>
                      </div>
                    </td>
                    <td>
                      <p class="text-xs text-secondary mb-0">
                            {{ usuario.correo }}
                      </p>
                    </td>
                    <td>
                      <p class="text-sm font-weight-bold mb-0">{{ usuario.pais }}</p>
                      <p class="text-sm text-secondary mb-0">{{ usuario.ciudad }}</p>
                    </td>
                    <!--<td class="align-middle text-center text-sm">
                      <span
                        class="text-sm"
                        :class="status ? 'badge-dark' : 'badge-danger'"
                        >{{ status ? "ONLINE" : "OFFLINE" }}</span
                      >
                    </td>-->
                    <td class="align-middle text-center">
                      <span class="text-secondary text-sm font-weight-bold">{{
                        usuario.idioma
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
                    <MaterialButton variant="contained" color="light" class="w-auto me-2 px-3 mb-0" data-bs-toggle="modal" data-bs-target="#exampleModal2" v-on:click='abrirModal(usuario)' >

                      <i class="fas fa-pencil-alt text-dark me-2" aria-hidden="true"></i>
                      Editar
                    </MaterialButton>
                    <MaterialButton variant="contained" color="light" class="w-auto me-2 text-danger px-3 mb-0" v-on:click='deleteDog(usuario)'>
                        <i class="far fa-trash-alt me-2" aria-hidden="true"></i>
                        Borrar
                    </MaterialButton>
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
                <p class="pb-3">
                  Ingrese los datos completos de los clientes asociados.
                </p>
                <form id="contact-form" method="post" autocomplete="off" v-on:submit='addDog'>
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="newDog.nombre"
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
                            v-model="newDog.apellido"
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
                            v-model="newDog.correo"
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
                            v-model="newDog.pais"
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
                            v-model="newDog.ciudad"
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
                            v-model="newDog.idioma"
                            placeholder="-">
                          </div>
                        </div>
                      </div>

                      </div>
                    </div>
                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <MaterialTextArea
                        id="message"
                        class="input-group-static mb-4"
                        :rows="2"
                        placeholder="Describe informacion adicional que no se haya registrado"
                        v-model="newDog.observaciones"
                        >Otro Datos</MaterialTextArea
                      >
                    </div>
                    <!--
                    <div class="row">
                      <div class="col-md-12 text-center">
                        <MaterialButton
                          variant="gradient"
                          color="success"
                          class="mt-3 mb-0"
                          >Send Message</MaterialButton
                        >
                      </div>
                    </div>-->
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
                <p class="pb-3">
                  Ingrese los datos completos de los clientes asociados.
                </p>
                <form id="contact-form" method="post" autocomplete="off" v-on:submit='updateDog'>
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-6">

                      <div class="row justify-space-between py-2">
                        <div class="col-lg-12 mx-auto">
                          <div class="input-group input-group-static mb-4">
                            <label>Nombre</label>
                            <input class="form-control" 
                            type="text" 
                            v-model="datoEditado.nombre"
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
                            v-model="datoEditado.apellido"
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
                            v-model="datoEditado.correo"
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
                            v-model="datoEditado.pais"
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
                            v-model="datoEditado.ciudad"
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
                            v-model="datoEditado.idioma"
                            placeholder="-">
                          </div>
                        </div>
                      </div>

                      </div>
                    </div>
                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <MaterialTextArea
                        id="message"
                        class="input-group-static mb-4"
                        :rows="2"
                        placeholder="Describe informacion adicional que no se haya registrado"
                        v-model="datoEditado.observaciones"
                        >Otro Datos</MaterialTextArea
                      >
                    </div>
                    <!--
                    <div class="row">
                      <div class="col-md-12 text-center">
                        <MaterialButton
                          variant="gradient"
                          color="success"
                          class="mt-3 mb-0"
                          >Send Message</MaterialButton
                        >
                      </div>
                    </div>-->
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
