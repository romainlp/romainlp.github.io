<template>
  <div>
    <transition name="fade">
    <div class="credits" v-if="display">
      <h2>Credits</h2>
      <ul>
        <li><a href="https://vuejs.org/" target="_blank">Vue.js</a></li>
        <li><a href="https://unsplash.com/photos/4wzRuAb-KWs" target="_blank">Photo by Mohammad Alizade on Unsplash</a></li>
      </ul>
    </div>
  </transition>
  </div>
</template>

<script>
export default {
  name: 'Credits',
  data () {
    return {
      display: false
    }
  },
  methods: {
    show: function () {
      this.display = true
    },
    hide: function () {
      this.display = false
      this.$parent.$emit('close')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.fade-enter-active {
  transition: opacity .5s;
  transition-delay: .5s;
}
 .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0
}
.credits {
  position: absolute;
  bottom: 0;
  left: 0;
  width: calc(100vw - 80px);
  padding: 40px;
}
.close {
  position: absolute;
  text-decoration: none;
  top: 20px;
  right: 40px;
  font-size: 40px;
  color: #333;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
  a {
    display: inline-block;
    text-decoration: none;
    color: #15333b;
    position: relative;
    transition: all .3s ease-in-out;
    &:before {
      content: '';
      background-color: #15333b;
      position: absolute;
      height: 2px;
      width: 100%;
      transition: all .5s ease-in-out;
      z-index: -1;
      opacity: 0;
      bottom: -5px;
    }
    &:hover {
      &:before {
        opacity: 1;
        bottom: -3px;
      }
    }
  }
}
</style>
