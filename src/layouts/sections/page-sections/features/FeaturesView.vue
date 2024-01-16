<script setup>
// Vue Material Kit 2 component
import Table from "@/examples/tables/Table.vue";
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


// table data
const tableData = {
  headers: ["Author", "Function", "Status", "Employed", "Action"],
  rows: [
    {
      image: team2,
      name: "John Michael",
      email: "john@creative-tim.com",
      position: ["Manager", "Organization"],
      status: true,
      date: "23/04/18",
      action: { label: "Edit", route: "/" },
    },
    {
      image: team3,
      name: "Alexa Liras",
      email: "alexa@creative-tim.com",
      position: ["Programator", "Developer"],
      status: false,
      date: "11/01/19",
      action: { label: "Edit", route: "/" },
    },
    {
      image: team4,
      name: "Laurent Perrier",
      email: "laurent@creative-tim.com",
      position: ["Executive", "Projects"],
      status: true,
      date: "19/09/17",
      action: { label: "Edit", route: "/" },
    },
    {
      image: team3,
      name: "Michael Levi",
      email: "michael@creative-tim.com",
      position: ["Programator", "Developer"],
      status: true,
      date: "24/12/08",
      action: { label: "Edit", route: "/" },
    },
    {
      image: team2,
      name: "Richard Gran",
      email: "richard@creative-tim.com",
      position: ["Manager", "Executive"],
      status: false,
      date: "04/10/21",
      action: { label: "Edit", route: "/" },
    },
    {
      image: team4,
      name: "Miriam Eric",
      email: "miriam@creative-tim.com",
      position: ["Programator", "Developer"],
      status: false,
      date: "14/09/20",
      action: { label: "Edit", route: "/" },
    },
  ],
};
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
  <Table v-bind="tableData" />
</div>

 <!-- Modal -->
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
                  color="none"
                  class="btn-close"
                  data-bs-dismiss="modal"
                  aria-label="Close">
                </MaterialButton>
              </div>
              <div class="modal-body">
                <p class="pb-3">
                  For further questions, including partnership opportunities,
                  please email hello@creative-tim.com or contact using our
                  contact form.
                </p>
                <form id="contact-form" method="post" autocomplete="off">
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-6">
                        <MaterialInput
                          class="input-group-static mb-4"
                          type="text"
                          label="Full Name"
                          placeholder="Full Name"
                        />
                      </div>
                      <div class="col-md-6 ps-md-2">
                        <MaterialInput
                          class="input-group-static mb-4"
                          type="email"
                          label="Email"
                          placeholder="hello@creative-tim.com"
                        />
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6">
                        <MaterialInput
                          class="input-group-static mb-4"
                          type="text"
                          label="Full Name"
                          placeholder="Full Name"
                        />
                      </div>
                      <div class="col-md-6 ps-md-2">
                        <MaterialInput
                          class="input-group-static mb-4"
                          type="email"
                          label="Email"
                          placeholder="hello@creative-tim.com"
                        />
                      </div>
                    </div>
                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <MaterialTextArea
                        id="message"
                        class="input-group-static mb-4"
                        :rows="3"
                        placeholder="Describe your problem in at least 250 characters"
                        >How can we help you?</MaterialTextArea
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
                </form>

              </div>
              <div class="modal-footer justify-content-between">
                <MaterialButton
                  variant="gradient"
                  color="dark"
                  data-bs-dismiss="modal">
                  Cancelar
                </MaterialButton>
                <MaterialButton variant="gradient" color="success" class="mb-0">
                  Guardar cambios
                </MaterialButton>
              </div>
            </div>
          </div>
        </div>

</template>
