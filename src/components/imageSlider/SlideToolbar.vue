<template>
  <div class="slide-toolbar">
    <div class="slide-counter">
      <span>{{ currentIndex }} / {{ maxIndex }}</span>
    </div>
<!--    <div class="slide-btn-wrap">
      <button :class="{'is-disable': pinchZoomScale === 1}"
              @click="onClickZoomOutBtn('zoom-out')"
              class="slide-btn slide-zoom-btn slide-zoom-out-btn">
        ─
      </button>
    </div>-->
    <div :class="{'is-disable': pinchZoomScale === 1}" class="slide-btn-wrap">
      <SlideBtn @click="onClickZoomOutBtn"
                icon-type="zoomOutIcon"
                class="slide-zoom-btn slide-zoom-in-btn"/>
    </div>
    <!--    <div class="slide-btn-wrap">
          <button :class="{'is-disable': pinchZoomScale === 4}"
                  @click="onClickZoomInBtn('zoom-in')"
                  :style="{maskImage: 'url(' + svgIcon.get('zoomInIcon') + ')'}"
                  class="slide-btn slide-zoom-btn slide-zoom-in-btn"></button>
        </div>-->
    <div :class="{'is-disable': pinchZoomScale === 4}" class="slide-btn-wrap">
      <SlideBtn @click="onClickZoomInBtn"
                icon-type="zoomInIcon"
                class="slide-zoom-btn slide-zoom-in-btn"/>
    </div>
    <div class="slide-btn-wrap">
      <SlideBtn @click="onClickCloseBtn" icon-type="closeIcon" class="slide-close-btn"/>
    </div>
<!--    <button @click="onClickCloseBtn" class="slide-btn slide-close-btn">✕</button>-->
  </div>
</template>

<script>
import svgIcon from "../../../public/img/svgIcon";
import SlideBtn from "./SlideBtn.vue";

export default {
  name: "SlideToolbar",
  components: {SlideBtn},
  computed: {
    svgIcon() {
      return svgIcon
    }
  },
  props: {
    maxIndex: Number,
    currentIndex: Number,
    pinchZoom: Boolean,
    pinchZoomScale: Number
  },
  methods: {
    onClickZoomOutBtn() {
      if (this.pinchZoomScale > 1) {
        this.$emit('change:zoom', 'zoom-out')
      }
    },
    onClickZoomInBtn() {
      if (this.pinchZoomScale < 4) {
        this.$emit('change:zoom', 'zoom-in')
      }
    },
    onClickCloseBtn() {
      this.$emit('close:slider')
    }
  }
}
</script>

<style scoped>

</style>