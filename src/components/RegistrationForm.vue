<template>
  <div class="registration-form-wrapper">
    <form class="registration-form-block" @submit.prevent="someAction()" novalidate>
      <h3 class="registration-form-title">Регистрация</h3>
      <div class="account-owning-block">
        <span>Уже есть аккаунт? </span>
        <a class="sign-in" href="#">Войти</a>
      </div>
      <Input v-model="name" class="input-element" id="name" type="text" title="Имя" placeholder="Введите Ваше имя" :error="!isNameValid"/>
      <Input v-model="email" class="input-element" id="email" type="email" title="Еmail" placeholder="Введите ваш email" :error="!isEmailValid"/>
      <Input v-model="phone" class="input-element" id="phone" type="tel" title="Номер телефона" placeholder="Введите номер телефона" :error="!isPhoneValid"/>
      <Dropdown title="Язык" :items="items" v-model="lang" :error="this.lang === ''"/>
      <div class="checkbox-wrapper">
        <Checkbox v-model="isCheck"/>
        <span class="checkbox-text">Принимаю <a href="#">условия</a> использования</span>
      </div>
      <div class="btn-wrapper">
        <Button :isDisabled="isBtnDisabled" class="btn-element" text="Зарегистрироваться"/>
      </div>
    </form>
  </div>
</template>

<script>
import Button from './Button.vue'
import Input from './Input.vue'
import Dropdown from './Dropdown.vue'
import Checkbox from './Checkbox.vue'

export default {
  name: 'RegistrationForm',
  components: {
    Button, Input, Dropdown, Checkbox
  },
  data () {
    return {
      lang: '',
      type: 'text',
      isCheck: false,
      name: '',
      email: '',
      phone: '',
      items: [
        'Русский', 'Английский', 'Китайский', 'Испанский'
      ]
    }
  },
  computed: {
    isBtnDisabled () {
      return !this.isNameValid || !this.isEmailValid || !this.isPhoneValid || this.isCheck === false || this.lang === ''
    },
    isNameValid () {
      const re = /^[а-яА-ЯёЁ\-\s]+$/
      return re.test(this.name)
    },
    isEmailValid () {
      const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return re.test(this.email.toLowerCase())
    },
    isPhoneValid () {
      // eslint-disable-next-line
      var re = /^[+]*[(]{0,1}[0-9]{1,3}[)]{0,1}[-\s\.0-9]*$/g
      return re.test(this.phone) && this.phone.match(/\d/g).length === 11
    }
  },
  methods: {
    someAction() {
      if (this.isBtnDisabled) {
        return
      }
      alert("Форма отправлена")
    }
  }
}
</script>

<style scoped>
  .registration-form-wrapper {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  .registration-form-block {
    box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.02), 0px 32px 64px rgba(44, 39, 56, 0.04);
    border-radius: 24px;
    padding: 40px 30px;
    width: 32%;
  }
  .registration-form-title {
    font-weight: 700;
    font-size: 2.125rem;
    line-height: 44px;
    padding-bottom: 8px;
  }
  .account-owning-block {
    padding-bottom: 55px;
  }
  .sign-in {
    color: #0880AE;
  }
  .input-element {
    padding-bottom: 34px;
  }
  .checkbox-wrapper {
    display: flex;
    align-items: center;
    margin-top: 31px;
    margin-bottom: 38px;
  }
  .checkbox-text {
    padding-left: 8px;
    color: #756F86;
    font-weight: 500;
  }
  .checkbox-text a {
    color: #0880AE;
  }
  .btn-element {
    width: 100%;
  }
  @media (max-width: 1200px) {
    .registration-form-block {
    width: 40%;
    }
  }
  @media (max-width: 930px) {
    .registration-form-block {
    width: 50%;
    }
  }
  @media (max-width: 730px) {
    .registration-form-block {
    width: 60%;
    }
  }
  @media (max-width: 615px) {
    .registration-form-block {
    width: 70%;
    }
  }
  @media (max-width: 530px) {
    .registration-form-block {
    width: 80%;
    }
  }
  @media (max-width: 460px) {
    .registration-form-block {
    width: 100%;
    }
  }
</style>