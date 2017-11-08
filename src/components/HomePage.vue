<template>
  <div class="hello">

    <div class="main" v-bind:class="classMain" v-on:click.prevent.self="back">
      <h1 v-if='current == "main"' >{{ title }}</h1>
      <h2 v-if='current == "main"' >{{ subtitle }}</h2>
      <a href="" 
        class="credits-link"
        v-if='current == "main"' 
        v-on:click.prevent="show('credits')">
        <icon name="info" label="View credits"></icon>
      </a>
      <a href="" 
        class="github-link"
        v-if='current == "main"' 
        v-on:click.prevent="show('github')">
        <icon name="github" label="View Github"></icon>
      </a>
    </div>
    
    <credits ref="credits"/>
    <github ref="github"/>

  </div>
</template>

<script>
import Credits from '@/components/Credits'
import Github from '@/components/Github'

export default {
  name: 'HomePage',
  components: {
    'credits': Credits,
    'github': Github
  },
  data () {
    return {
      title: 'Romain Le Polh',
      subtitle: 'Web Developer @Captovate',
      current: 'main'
    }
  },
  mounted () {
    var vm = this
    this.$on('close', function () {
      vm.current = 'main'
    })
  },
  computed: {
    classMain: function () {
      return {
        'show-credits': (this.current === 'credits'),
        'show-main': (this.current === 'main'),
        'show-github': (this.current === 'github')
      }
    }
  },
  methods: {
    show: function (section) {
      this.current = section
      this.$refs[this.current].show()
    },
    back: function () {
      if (this.current !== 'main') {
        this.$refs[this.current].hide()
        this.current = 'main'
      }
    }
  }
}
</script>

<style scoped lang="scss">
$top: 0px;
$left: 0px;
h1, h2 {
  font-weight: normal;
  margin: 0;
}

ul { 
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #15333b;
}

h1 {
  position: absolute;
  top: 20px;
  left: 20px;
  color: #f2f2f2;
  font-size: 16px;
}
h2 {
  position: absolute;
  top: 20px;
  right: 20px;
  color: #f2f2f2;
  font-size: 16px;
}
.main {
  position: absolute;
  width: calc(100vw);
  height: calc(100vh);
  top: $top;
  left: $left;
  background: transparent url(../assets/bg1.jpg) no-repeat center center;
  background-size: cover;
  transition: all .5s ease-in-out;
  -webkit-box-shadow: 0px 0px 7px -1px rgba(0,0,0,0.90);
  -moz-box-shadow: 0px 0px 7px -1px rgba(0,0,0,0.90);
  box-shadow: 0px 0px 7px -1px rgba(0,0,0,0.90);
  &:hover {
    cursor: pointer;
  }
  &.show-github,
  &.show-credits {
    transition: all .5s ease-in-out;
    transform: scale(0.8) translateY(-110px);

  }
}
.credits-link {
  position: absolute;
  bottom: 20px;
  right: 20px;
  color: #fff;
  font-weight: 300;
  font-size: 16px;
  svg {
    width: 32px;
    height: 32px;
  }
}
.github-link {
  position: absolute;
  bottom: 20px;
  left: 20px;
  color: #fff;
  font-weight: 300;
  font-size: 32px;
  svg {
    width: 32px;
    height: 32px;
  }
}
</style>
