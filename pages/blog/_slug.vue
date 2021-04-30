<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img class="card__image" :src="require(`~/assets/images/${article.img}`)" :alt="article.alt" />
    <p>Последнее обновление: {{ formatDate(article.updatedAt, 'ru') }}</p>
    <p>Article last updated: {{ formatDate(article.updatedAt, 'en') }}</p>
    <p>最後の更新: {{ formatDate(article.updatedAt, 'ja-jp') }}</p>

    <nuxt-content :document="article" />
  </article>
</template>

<script>
  export default {
    methods: {
        formatDate(date, lang) {
          const options = {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
            hour: 'numeric',
            minute: 'numeric'
          }
          return new Date(date).toLocaleDateString(lang, options)
        }
    },

    async asyncData({ $content, params }) {
      const article = await $content('articles', params.slug).fetch()

      return { article }
    }
  }
</script>
<style lang="scss" scoped>
  .nuxt-content h1 {
    font-weight: bold;
    font-size: 28px;
  }
  .nuxt-content h3 {
    font-weight: bold;
    font-size: 22px;
  }
  .nuxt-content p {
    margin-bottom: 20px;
  }
  .card {
    &__image {
      width: 100%;
      max-width: 100vw;
      height: auto;
      box-sizing: border-box;
    }
  }
</style>
