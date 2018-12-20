<template>
  <div class="card__container">
    <ImageModule />
  </div>
</template>

<script>
import ImageModule from '@/modules/ImageModule.vue';

export default {
  name: 'Card',
  components: {
    ImageModule,
  }
};
</script>
