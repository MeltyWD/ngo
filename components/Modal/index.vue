<template>
  <article class="modal-wrap">
    <span class="modal-wrap__overlay" @click="$emit('modalClose')" />
    <div class="container">
      <span class="icon-close" @click="$emit('modalClose')" />
      <h1 class="container__title">Вход</h1>
      <form>
        <label class="label">
          Email
          <input class="input" type="email" v-model="email" @keyup.enter="handleKeyPress">
        </label>
        <label class="label">
          Пароль
          <input class="input" type="password" v-model="password" @keyup.enter="handleKeyPress">
        </label>
        <label class="label">
          Имя
          <input class="input" type="text" v-model="name" @keyup.enter="handleKeyPress">
        </label>
        <button type="submit" class="button" @click.prevent="handleSubmit">Войти</button>
      </form>
    </div>
  </article>
</template>

<script>
import axios from '@/plugins/axios';
  export default {
    data() {
      return {
        email: '',
        password: '',
        name: '',
      }
    },

    methods: {
      handleButtonClick(event) {
        console.log('clicked')
      },
      handleKeyPress(event) {
        console.log(event, 'key pressed!')
      },
      handleSubmit(event) {
        const body = {
          email : this.email,
          password : this.password,
          name : this.name
        }
        console.log(JSON.stringify(body))
        axios.post('/signup', {
          email : this.email,
          password : this.password,
          name : this.name
        },
        ).then(res => {
          console.log(res)
        }).catch((err) => console.log(err.response.data.message))
          // commit('SET_GUESTS', res.data);
          // $router.push('/blog')
        }
    }
  }
</script>

<style scoped lang="scss">
  .modal-wrap {
    width: 100%;
    height: 100vh;
    position: absolute;
    left:0;
    top: 0;

    &__overlay {
      position: absolute;
      left:0;
      top: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
    }
  }

  .container {
    width: 400px;
    padding: 30px;
    margin: 0 auto;
    position: relative;
    top: 50%;
    transform: translateY(-50%);
    background: white;
    border-radius: 14px;
    &__title {
      margin: 0
    }
  }
  .icon-close {
    width: 20px;
    height: 20px;
    position: absolute;
    right: -25px;
    top: -25px;
  }
  .icon-close::after {
    width: 100%;
    display: inline-block;
    content: '';
    border: 1px solid white;
    transform: rotate(45deg);
    position: absolute;
    top: 50%;
    left: 0;
  }
  .icon-close::before {
    width: 100%;
    display: inline-block;
    content: '';
    border: 1px solid white;
    transform: rotate(-45deg);
    position: absolute;
    top: 50%;
    left: 0;
  }

  .label {
    display: flex;
    flex-direction: column;
    margin: 15px 0;
  }

  .input {
    padding: 7px 15px;
  }

  .button {
    width: 100%;
    margin-top: 35px;
    padding: 10px 20px;
    border-radius: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid black;
    background: white;
    color: black;
    transition: .3s;
    cursor: pointer;
  }
  .button:hover {
    color: white;
    background: black;
    transition: .3s;
  }
</style>
