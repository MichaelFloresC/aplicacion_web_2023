<script setup>
import DefaultReviewCard from "@/examples/cards/reviewCards/DefaultReviewCard.vue";
</script>
<template>
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
      <div class="row mt-6">
        <DefaultReviewCard
          name="Nick Willever"
          date="Hace 1 día"
          review='Este es un producto excelente, tuve las mejores vacaciones'
          :rating="2.0"
        />
        <DefaultReviewCard
          name="Shailesh Kushwaha"
          date="Hace 1 semana"
          review='Encontré excelentes lugares dentro de Arequipa.
                  ¡Excelentes pasatiempos para divertirme! Y es
                  chicos realmente asequibles y muy humildes!!!'
          :rating="5.0"
        />

        <DefaultReviewCard
          name="Samuel Kamuli"
          date="Hace 1 mes"
          review='Buen producto. Me ayudó a planificar mis vacaciones.
                  ¡Fui de visita a muchos lugares de Arequipa... !'
          :rating="5.0"
        />
      </div>
      <hr class="horizontal dark my-5" />

    </div>
  </section>
</template>
