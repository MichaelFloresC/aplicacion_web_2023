<script setup>
// example components
import TransparentBlogCard from "../../../../examples/cards/blogCards/TransparentBlogCard.vue";
import BackgroundBlogCard from "../../../../examples/cards/blogCards/BackgroundBlogCard.vue";

//Vue Material Kit 2 components
import post1 from "@/assets/img/examples/colca.jpg";
import post2 from "@/assets/img/examples/sillar.jpg";
import post3 from "@/assets/img/examples/campinia.jpg";
import post4 from "@/assets/img/examples/tours.jpg";
</script>
<template>
  <section class="py-3">
    <div class="container">
      <div class="row">
        <div class="col-lg-6">
          <h3 class="mb-5">Consulta nuestros paquetes mas solicitados</h3>
        </div>
      </div>
      <div class="row">
        <div class="col-lg-3 col-sm-6">
          <TransparentBlogCard
            :image="post1"
            title="COLCA FULL DAY"
            description="Visita el Cañón del Colca considerado el más profundo del mundo en solo un día. 
            Saliendo de Arequipa en un transporte turístico hasta llegar a Chivay (capital del valle del Colca) aprox. 06:00 am. Disfruta de un delicioso desayuno andino en el pueblo de Chivay y continuaremos en nuestro bus hasta llegar a la Cruz de Cóndor (punto más alto y profundo del Cañon)."
          />
        </div>
        <div class="col-lg-3 col-sm-6">
          <TransparentBlogCard
            :image="post2"
            title="RUTA DE SILLAR"
            description="El primer punto en el que nos detendremos será la Cantera de Añashuayco; al cual llegaremos en 45 minutos aprox. 
            Actualmente se encuentra en explotación, los canteros realizan sus labores desde muy temprano; en el lugar podremos apreciar un inmenso cañon con farallones (paredes de ignimbrita) que tienen varios metros de altura, formados por la extracción para la formación de los Sillares."
          />
        </div>
        <div class="col-lg-3 col-sm-6">
          <TransparentBlogCard
            :image="post3"
            title="CAMPIÑA TOUR"
            description="- Plaza de Armas , Centro Histórico - Mirador de Yanahuara - Puente Chilina - Mirador de Carmen Alto (Valle Chilina) 
            - Distrito de Cayma - Outlet Incalpaca y Zoológico - Distrito de Sachaca (Palacio de Goyeneche) - Balneario de Tingo - Vía Paisajista - Mansión Del Fundador (*) - Molino de Sabandia (*) - Andenes de Paucarpata - Parque Jurásico - Restaurant Tradición Arequipeña (Opcional)"
          />
        </div>
        <div class="col-lg-3 col-md-12 col-12">
          <BackgroundBlogCard
            :image="post4"
            title="Conoce mas destinos turisticos"
            description="Revisa nuestro catalogo completo"
          />
        </div>
      </div>
    </div>
  </section>
</template>
