<template>
  <div class="responsive-vue-image">
    <picture>
      <source media="(max-width:768px)"
              :srcset="getImageMobile + ' 768w'"  :data-fallback-src="fallbackImage"/>
      <source media="(max-width:992px)"
              :srcset="getImageTablet + ' 992w'"  :data-fallback-src="fallbackImage"/>
      <source :srcset="getImageDesktop"           :data-fallback-src="fallbackImage"/>
      <img :src="getImageDesktop" :alt="image.alt" ref="image" @error="imageLoadError" :data-fallback-src="fallbackImage"/>
    </picture>
  </div>
</template>

<script>
export default {
  name: "ResponsiveVueImage",
  props: {
    fallbackImage: {
      default: 'https://via.placeholder.com/768',
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
    getImageDesktop() {
      return this.image.image;
    },
  },
  methods: {
    imageLoadError( event ) {
      console.log( 'Image failed to load. Load fallback image: %s', this.fallbackImage);
      const imgTag      = this.$refs.image;
      const srcElement  = imgTag.closest('picture').querySelector( `[srcset~="${event.target.currentSrc}"]` );
      srcElement.srcset = srcElement.dataset.fallbackSrc;
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
