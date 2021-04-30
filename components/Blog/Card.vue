<template>
  <li class="card">
    <img class="card__image" src="@/assets/images/first-blog-post.jpg" />
    <div class="card__frame">

    </div>
  </li>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
  .card {
    position: relative;
    display: flex;
    background-color: #000;
    height: 600px;
    transition: .5s;
    opacity: .8;
    &:hover {
      opacity: 1;
    }
    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(45deg, #0D488D, #B43540);
    }
    &::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(45deg, #0D488D, #B43540);
      filter: blur(25px);
    }
    &__image {
      position: absolute;
      top: 6px;
      left: 6px;
      right: 6px;
      bottom: 6px;
      width: calc(100% - 12px);
      height: 50%;
      object-fit: cover;
      box-sizing: border-box;
      z-index: 2;
      opacity: .9;
    }
    &__frame {
      position: absolute;
      top: 6px;
      left: 6px;
      right: 6px;
      bottom: 6px;
      background: rgba(0, 0, 0);
      opacity: .6;
      z-index: 1;
    &::after {
      position: absolute;
      content: '';
      bottom: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: rgba(0, 0, 0, 0.1);
      pointer-events: none;
      z-index: 2;
    }
  }
  }
</style>
