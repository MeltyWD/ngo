<template>
  <nav class="navigation">
    <nuxt-link to="/">
      <Logo :title="logoText" />
    </nuxt-link>
    <nuxt-link v-for="elem in routes" class="link" :to="elem.path" :key="elem.name">
      {{ elem.name }}
    </nuxt-link>
    <button class="button" @click="toggleModal">{{ text }}</button>
    <Modal v-show="showModal" @modalClose="toggleModal" />
  </nav>
</template>

<script>
  import Logo from './navigation/nav__logo';
  const DYNAMIC_ROUTE_MARKER = ':';

  export default {
    components: {
      Logo
    },
    data() {
      return {
        text: 'Enter',
        logoText: 'НКО-проект',
        linksArray: [
          { to: '/', title: 'Main' },
          { to: '/about', title: 'About page' },
        ],
        showModal: false,
      }
    },
    methods: {
      toggleModal() {
        this.showModal = !this.showModal;
      }
    },
    computed: {
      routes() {
        return this.$router.options.routes.filter((elem) => !elem.path.includes(DYNAMIC_ROUTE_MARKER))
      }
    }
  }
</script>

<style scoped>
.navigation {
  width: 100%;
  height: 80px;
  padding: 20px;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: rgba(255,255,255,0.2);
}

.button {
  width: 100px;
  padding: 10px 15px;
  background: white;
  color: black;
  border: 1px solid black;
  border-radius: 30px;
  cursor: pointer;
  transition: .3s;
}
.button:hover {
  background: black;
  color: white;
  transition: .3s;
}

.link {
  color: black;
}
</style>
