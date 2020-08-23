<template>
  <div class="drawer">
    <div
      class="drawer__overlay"
      @click="toggle()"
      :style="overlayStyle"
      v-if="overlay"
    ></div>
    <div class="drawer__content" :style="style">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    width: { type: [String, Number], default: 300 },
    opacity: { type: Number, default: 0.3 },
    overlay: { type: Boolean, default: true }
  },
  computed: {
    style() {
      return {
        width: this._width
      }
    },
    overlayStyle() {
      return {
        background: `rgba(0, 0, 0, ${this.opacity})`
      }
    },
    _width() {
      return /^\d+$/.test(this.width) ? this.width + 'px' : this.width
    }
  },
  methods: {
    toggle() {
      const drawer = document.querySelector('.drawer')
      drawer.classList.toggle('show')
    }
  }
}
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.drawer {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  visibility: hidden;
  opacity: 0;
  transition: all 0.3s ease-in-out;
}
.drawer.show {
  visibility: visible;
  opacity: 1;
}
.drawer.show .drawer__content {
  transform: translateX(0px);
}
.drawer.show .drawer__overlay {
  width: 100%;
}
.drawer__overlay {
  position: absolute;
  width: 25%;
  height: 100%;
  transition: all 0.5s cubic-bezier(0.19, 1, 0.22, 1);
}
.drawer__content {
  position: relative;
  height: 100%;
  background: #fff;
  transform: translateX(-100px);
  transition: all 0.8s cubic-bezier(0.19, 1, 0.22, 1);
  box-shadow: 5px 0 5px -5px #ccc;
  border-right: 1px solid #ccc;
}
</style>
