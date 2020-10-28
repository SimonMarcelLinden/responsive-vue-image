<template>
  <div class="responsive-vue-image">
    <picture>
      <source media="(max-width:768px)" :srcset="getImageMobile" />
      <source media="(max-width:992px)" :srcset="getImageTablet" />
      <img :src="image.image" :alt="image.alt" @error="imageLoadError" />
    </picture>
  </div>
</template>

<script>
export default {
  name: "ResponsiveVueImage",
  props: {
    fallbackImage: {
      default: 'https://via.placeholder.com/64',
      required: false
    },
    image: {
      type: Object,
      default: () => ({
        imageMobile: 'https://via.placeholder.com/128',
        imageTablet: 'https://via.placeholder.com/256',
        image: 'https://via.placeholder.com/512',
        alt: 'Default Image'
      }),
    },
  },
  computed: {
    getImageMobile() {
      return this.image.imageMobile
          ? this.image.imageMobile
          : this.image.imageTablet
              ? this.image.imageTablet
              : this.image.image;
    },
    getImageTablet() {
      return this.image.imageTablet
          ? this.image.imageTablet
          : this.image.image;
    },
  },
  methods: {
    imageLoadError ( $event ) {
      console.log( 'Image failed to load. Load fallback image: %s', this.fallbackImage);
      $event.onerror = null;
      $event.target.src  = ( this.fallbackImage ) ? this.fallbackImage : 'https://via.placeholder.com/150'
    }
  }
}
</script>

<style scoped>
.responsive-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.custom-size img {
  object-fit: scale-down;
}
</style>
