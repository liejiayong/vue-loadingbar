<template>
  <transition name="fade">
    <div :class="classes" :style="outerStyles" v-show="show">
      <div :class="innerClasses" :style="styles"></div>
    </div>
  </transition>
</template>
<script>
const prefixCls = 'jloading-bar';

export default {
  name: 'JLoadingBar',
  props: {
    color: {
      type: String,
      default: 'primary',
    },
    failedColor: {
      type: String,
      default: 'error',
    },
    height: {
      type: Number,
      default: 2,
    },
  },
  data() {
    return {
      percent: 0,
      status: 'success',
      show: false,
    };
  },
  computed: {
    classes() {
      return `${prefixCls}`;
    },
    innerClasses() {
      return [
        `${prefixCls}-inner`,
        {
          [`${prefixCls}-inner-color-primary`]: this.color === 'primary' && this.status === 'success',
          [`${prefixCls}-inner-failed-color-error`]: this.failedColor === 'error' && this.status === 'error',
        },
      ];
    },
    outerStyles() {
      return {
        height: `${this.height}px`,
      };
    },
    styles() {
      let style = {
        width: `${this.percent}%`,
        height: `${this.height}px`,
      };

      if (this.color !== 'primary' && this.status === 'success') {
        style.backgroundColor = this.color;
      }

      if (this.failedColor !== 'error' && this.status === 'error') {
        style.backgroundColor = this.failedColor;
      }

      return style;
    },
  },
};
</script>

<style>
.jloading-bar {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1111;
  background-color: #e5e5e5;
}
.jloading-bar-inner {
  transition: width 1s linear;
}
.jloading-bar-inner-color-primary {
  background-color: #ffc600;
}
.jloading-bar-inner-failed-color-error {
  background-color: #ff5a00;
}
</style>
