<template>
  <h1>Добавить запись</h1>
  <div class="createMain">
    <form class="form" @submit.prevent="">
      <div class="form_inputs">
        <input type="text" placeholder="Name" v-model="newForm.name">
        <input type="text" placeholder="Email" v-model="newForm.email">
      </div>
      <div class="form_radio">
        <p>Пол</p>
        <input type="radio" value="male" v-model="newForm.gender" id="male">
        <label for="male">Мужской</label>
        <input type="radio" value="female" v-model="newForm.gender" id="female">
        <label for="female">Женский</label>
      </div>
      <div class="form_textarea">
        <p align="right">Символов: {{wordCounter}} </p>
        <textarea rows="10" v-model="newForm.message" @change="sumText"></textarea>
      </div>
      <div class="form_checkbox">
        <input type="checkbox" id="scales" v-model="newForm.agree">
        <label for="scales">Согласен на обработку персональных данных</label>
      </div>
      <div class="form_button">
        <button @click="createForm" :disabled="!isSuccess">Отправить</button>
      </div>
    </form>

    <section v-if="isSent">
      <div class="info_user">
        <div class="info_user__title">
          name
        </div>
        <div class="info_user__value">
          <p>{{successForm.name}}</p>
        </div>
      </div>
      <div class="info_user">
        <div class="info_user__title">
          email
        </div>
        <div class="info_user__value">
          <p>{{successForm.email}}</p>
        </div>
      </div>
      <div class="info_user">
        <div class="info_user__title">
          gender
        </div>
        <div class="info_user__value">
          <p>{{successForm.gender}}</p>
        </div>
      </div>
      <div class="info_user">
        <div class="info_user__title">
          message
        </div>
        <div class="info_user__value">
          <p>{{successForm.message}}</p>
        </div>
      </div>
      <div class="info_user">
        <div class="info_user__title">
          agree
        </div>
        <div class="info_user__value">
          <p>{{successForm.agree}}</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
// import InputForm from '@/components/InputForm.vue'
// import TextAreaForm from '@/components/TextAreaForm.vue'
// import RadioForm from '@/components/RadioForm.vue'
// import CheckBoxForm from '@/components/CheckBoxForm.vue'
// import ButtonForm from '@/components/ButtonForm.vue'
export default {
  name: 'Create',
  // components: {
  //   InputForm,
  //   TextAreaForm,
  //   RadioForm,
  //   CheckBoxForm,
  //   ButtonForm
  // }
  data() {
    return {
      newForm: {
        name: '',
        email: '',
        gender: 'male',
        message: '',
        agree: false
      },
      successForm: {},
      isSent: false
    }
  },
  methods: {
    createForm() {
      this.successForm = {
        ...this.newForm
      }
      this.newForm = {
        name: '',
        email: '',
        gender: 'male',
        message: '',
        agree: false
      }
      this.isSent = true
    }
  },
  computed: {
    wordCounter() {
      return this.newForm.message.length
    },
    isSuccess() {
      return this.newForm.name.length && this.newForm.email.length && this.newForm.message.length && this.newForm.agree
    }
  },
}
</script>

<style lang="less" scoped>
.createMain {
  display: flex;
  align-items: stretch;
}
.form {
  flex: 1;
  max-width: 50%;
  box-sizing: border-box;
  background: #fff;
  padding: 20px;
  input {
    box-sizing: border-box;
  }
  &_inputs {
    input {
      display: block;
      padding: 10px 5px;
      width: 100%;
      margin-bottom: 20px;
      border-radius: 5px;
      border: 1px solid rgb(238, 220, 220);
      outline: none;
      &:focus{
        border: 1px solid #3179e6;
      }
    }
  }
  &_radio {
    margin-bottom: 20px;
    p {
      margin: 0;
      font-weight: bold;
    }
    input[type='radio'] {
      box-sizing: border-box;
      appearance: none;
      background: white;
      outline: 1px solid #969ca5;
      border: 3px solid white;
      width: 12px;
      height: 12px;
      margin-right: 10px;
      &:checked {
        background: #3179e6;
        outline: 1px solid #3179e6;
      }
    }
    
    label {
      margin-right: 10px;
    }
  }
  &_textarea {

    textarea {
      padding: 10px 5px;
      width: 100%;
      margin-bottom: 20px;
      border-radius: 5px;
      border: 1px solid rgb(238, 220, 220);
      box-sizing: border-box;
      outline: none;
      &:focus{
        border: 1px solid #3179e6;
      }
    }
  }
  &_checkbox {
    display: flex;
    align-items: center;
    input[type='checkbox'] {
      box-sizing: border-box;
      appearance: none;
      background: white;
      outline: 1px solid #969ca5;
      border: 3px solid white;
      width: 12px;
      height: 12px;
      margin-right: 10px;
    }
    input[type='checkbox']:checked {
      background: #3179e6;
      outline: 1px solid #3179e6;
    }
  }
  &_button {
    display: flex;
    justify-content: flex-end;

    button {
      padding: 10px 25px;
      background: #fff;
      border: 1px solid #3179e6;
      border-radius: 3px;
      font-weight: bold;
      color: #3179e6;
      &:disabled {
        border: 1px solid #ccc;
        color: #ccc;
      }
    }
  }
}
section {
  flex: 1;
  max-width: 50%;
  box-sizing: border-box;
  margin-left: 30px;
}
.info_user {
  padding: 15px;
  display: flex;
  background: #fff;
  align-items: center;
  &__title {
    flex-basis: 100px;
    min-width: 100px;
    color: #ccc;
  }
  &__value {
    
    font-weight: bold;
    p {
      overflow-wrap: anywhere;
    }
  }
}
</style>
