<template>
  <section class="blog">
    <div class="blog__intro">
      <img class="blog__image" src="../../assets/images/first-blog-post.jpg" alt="изображение"
      v-rellax="{
        speed: -4,
      }"
      />
      <div class="blog__overlay"></div>
      <h1 class="blog__title" v-rellax="{
      speed: -3,
    }">BLOG</h1>
    </div>
    <ul class="blog__grid">
      <Card v-for="guest in $store.state.guests" :guest="guest" :key="guest.slug" />
    </ul>
  </section>
</template>

<script>
import axios from '@/plugins/axios';
  export default {
    created() {
      axios.get('/signup').then((res) => {
        console.log('here res', json(res));
      }).catch((err) => console.log(err))
    }
  }
</script>

<style lang="scss" scoped>
  .blog {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    padding: 84px 0 56px;
    &__intro {
      position: relative;
      display: flex;
      flex-direction: column;
      width: 100%;
      min-height: 372px;
      height: min-content;
      background-color: #000;
      background-size: cover;
      background-repeat: no-repeat;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      z-index: -1;
      &::after {
        position: absolute;
        content: '';
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        box-shadow: inset 0px 0px 10px 20px rgba(0,0,0,1);
      }
    }
    &__image {
      position: absolute;
      display: block;
      width: 100%;
      height: auto;
      top: -50px;
    }
    &__overlay {
        position: absolute;
        content: '';
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, .65);
        z-index: 1;
    }
    &__title {
      font-size: 60px;
      color: #fff;
      line-height: 1.2;
      z-index: 1;
      margin: 0;
      text-shadow: 0px 0px 3px rgba(255, 255, 255, 0.8);
    }
    &__grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      padding: 40px 40px 800px;
    }
  }
</style>
