<template>
  <component :is="$parent.ripple?'ripple':'div'" position="center" :class="classes" @click.native="handleClick">
    <slot></slot>
  </component>
</template>

<script>
import Ripple from '../ripple'
export default {
  componentName: 'TabbarItem',
  components: {
    Ripple
  },
  props: {
    name: {
      type: [Number, String, Object],
      required: true
    }
  },
  methods: {
    handleClick () {
      this.$emit('change', this.name)
    }
  },
  computed: {
    classes () {
      let array = ['vx-flexbox-item', 'vx-tabbar-item']
      if (this.$parent.active === this.name) {
        array.push('is-active')
        array.push(this.$parent.activeClass)
      }
      return array
    }
  }
}
</script>
