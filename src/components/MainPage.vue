<template>
  <div class="main">
    <form @submit.prevent="submitUser" class="form" action="">
      <h1 class="title">Личные данные</h1>
      <div class="form-table">
        <div class="form-section">
          <label for="" class="form-label">
            Фамилия
          </label>
          <input 
            type="text" 
            placeholder="Фамилия"
            v-model="user.lastName"
            :class="{ 'error-input': v$.user.lastName.$error }"
            class="form-input"
          />
          <div v-if="v$.user.lastName.$error" class="error-text">
            Введите вашу фамилию
          </div>
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Имя
          </label>
          <input 
            type="text" 
            placeholder="Имя"
            v-model="user.firstName"
            :class="{ 'error-input': v$.user.firstName.$error }"
            class="form-input"
          />
          <div v-if="v$.user.firstName.$error" class="error-text">
            Введите ваше имя
          </div>
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Отчество
          </label>
          <input 
            type="text" 
            placeholder="Отчество"
            v-model="user.patronymic"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Дата рождения
          </label>
          <input 
            type="date"
            placeholder="Отчество"
            v-model="user.birthDate"
            :class="{ 'error-input': v$.user.birthDate.$error}"
            class="form-input"
          />
          <div v-if="v$.user.birthDate.$error" class="error-text">
            Введите корректную дату
          </div>
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Номер телефона
          </label>
          <input 
            type="tel"
            placeholder="7(111)222-33-44"
            v-model="user.phone"
            :class="{ 'error-input': v$.user.phone.$error}"
            class="form-input"
          />
          <div v-if="v$.user.phone.$error" class="error-text">
            Введите телефон в формате 7(***)*** ** **
          </div>
        </div>

        <div class="form-section form-section-radiobuttons-wrap">
          <div class="form-section-radiobuttons"> 
            <h3 class="form-section-radiobuttons_title">Пол</h3>
            <div class="form-section-radiobutton">
              <input type="radio" id="huey" name="drone" value="huey" checked class="custom-checkbox"/>
              <label for="huey">М</label>
            </div>
            <div>
              <input type="radio" id="dewey" name="drone" value="dewey" class="custom-checkbox"/>
              <label for="dewey">Ж</label>
            </div>
          </div>
        </div>

        <div class="form-section">
          <label class="form-label" for="">Группа клиентов</label>
          <div class="form_label"  :class="{ 'error-input': v$.user.clients.$error}">
            <div class="multiselect_block">
            <label for="select-1" class="field_multiselect">Группа клиентов</label>
            <input id="checkbox-1" class="multiselect_checkbox" type="checkbox" >
            <label for="checkbox-1" class="multiselect_label"></label>
            <select id="select-1" v-model="user.clients" class="field_select"  name="technology" multiple style="@media (min-width: 768px) { height: calc(4 * 38px)}">
              <option value="HTML">VIP</option>
              <option value="CSS">Проблемные</option>
              <option value="JavaScript">ОМС</option>
            </select>
          </div>
          </div>
          <div class="error-text" v-if="v$.user.clients.$error">
            выберите как минимум бы 1 пункт
          </div>
        </div>

        <div class="form-section">
          <label for="" class="form-label">Лечащий врач</label>
          <select class="form-select ">
            <option value="value1">Иванов</option>
            <option value="value2">Захаров</option>
            <option value="value3">Чернышева</option>
          </select>
        </div>

        <div class="form-section ">
          <div class="form-checkbox">
            <input id="checkbox" type="checkbox" class="form-checkbox-input custom-checkbox">
            <label for="checkbox" class="form-label form-label-checkbox"> Не отправлять СМС</label>
          </div>
        </div>

        <div class="form-empty"></div>
        <h2 class="form-title">Адрес</h2>

        <div class="form-section">
          <label for="" class="form-label">
            Индекс
          </label>
          <input 
            type="text" 
            placeholder="индекс"
            v-model="user.index"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Страна
          </label>
          <input 
            type="text" 
            placeholder="страна"
            v-model="user.country"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Область
          </label>
          <input 
            type="text" 
            placeholder="область"
            v-model="user.region"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Город
          </label>
          <input 
            type="text" 
            placeholder="город"
            v-model="user.city"
            :class="{ 'error-input': v$.user.city.$error}"
            class="form-input"
          />
          <div v-if="v$.user.city.$error" class="error-text">
            Введите ваш город
          </div>
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Улица
          </label>
          <input 
            type="text" 
            placeholder="улица"
            v-model="user.street"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Дом
          </label>
          <input 
            type="text" 
            placeholder="дом"
            v-model="user.house"
            class="form-input"
          />
        </div>

        <h2 class="form-title">Паспорт</h2>

        <div class="form-section">
          <label for="" class="form-label">Документ</label>
          <select class="form-select">
            <option value="value1" selected>Паспорт</option>
            <option value="value2">Свидетельство о рождении</option>
            <option value="value3">Вод. удостоверение</option>
          </select>
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Серия
          </label>
          <input 
            type="text" 
            placeholder="серия"
            v-model="user.passportSeries"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Номер
          </label>
          <input 
            type="text" 
            placeholder="номер"
            v-model="user.passportId"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            Кем выдан
          </label>
          <input 
            type="text" 
            placeholder="кем выдан"
            v-model="user.passportIssued"
            class="form-input"
          />
        </div>

        <div class="form-section">
          <label for="" class="form-label">
            дата выдачи
          </label>
          <input 
            type="date" 
            placeholder="дом"
            v-model="user.passportDate"
            :class="{ 'error-input': v$.user.passportDate.$error}"
            class="form-input"
          />
          <div v-if="v$.user.passportDate.$error" class="error-text">
            Введите дату выдачи
          </div>
        </div>

        <div class="form-empty"></div>

        <div class="form-section-btn">
          <button 
            type="submit"
            class="form-btn"
          >
            Отправить
          </button>
        </div>
        <div v-if="showSuccess" class="form-success">
          Новый клиент создан
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { useVuelidate } from '@vuelidate/core'
import { minLength, maxLength, required, numeric } from '@vuelidate/validators'

const validatePhone = (value) => {
  return value[0] == '7'
}

export default {
  name: 'MainPage',
  setup() {
    return{
      v$: useVuelidate(),
    }
  },
  data() {
    return {
      user: {
        name:'',
        lastName:'',
        patronymic:'',
        birthDate:'',
        phone:'',
        clients:'',
        gender:'',

        index:'',
        country:'',
        region:'',
        city:'',
        street:'',
        house:'',

        passportSeries:'',
        passportId:'',
        passportIssued:'',
        passportDate:''
      },
      showSuccess: false
    }
  },

  methods: {
    submitUser() {
      this.v$.user.$touch();
      if(this.v$.user.$error) {
        this.showSuccess = false
        return
      }
      this.showSuccess = true
    }
  },
  validations() {
    return {
      user:{
        lastName: { 
          required,
          $autoDirty: true
        },
        firstName: {
          required,
          $autoDirty: true
        },
        birthDate: {
          required,
          $autoDirty: true
        },
        phone: {
          validatePhone,
          required,
          minLength: minLength(11),
          maxLength: maxLength(11),
          $autoDirty: true,
          numeric
        },
        clients: {
          required,
          $autoDirty: true,
        },
        city: {
          required,
          $autoDirty: true,
        },
        passportDate: {
          required,
          $autoDirty: true,
        }
      }
    }
  }
}
</script>

<style scoped lang="sass">
.main
  display: flex
  justify-content: center
.title 
  width: 100%
  color: #fff
  margin-top: 48px
  text-align: center
.form
  max-width: 1024px
  width: 100%
  display: flex
  flex-direction: column
  background: #323745
  &-table 
    width: 100%px
    display: flex
    flex-direction: row
    justify-content: space-around
    flex-wrap: wrap
    padding: 4px
    margin-top: 32px
    margin-bottom: 64px
  &-section
    display: flex
    align-items: flex-start
    flex-direction: column
    margin-top: 8px
    margin-bottom: 8px
    color: #E0E4E7
    &-radiobuttons
      display: flex
      flex-direction: row
      align-items: center
      &_title 
        margin-right: 16px
      &-wrap 
        width: 380px
        display: flex
        flex-direction: row
        align-items: center
        margin-left: 12px
    &-radiobutton
      margin-right: 12px
    &-btn 
      width: 100%
      display: flex
      justify-content: center
      margin-top: 32px
  &-label
    font-size: 20px
    margin-bottom: 4px
    margin-left: 8px
  &-input
    min-width: 380px
    height: 40px
    font-size: 18px
    background: #242731
    color: #fff
    border: 1px solid #323745
    border-radius: 8px
    outline: none
    padding: 4px
    padding-left: 8px
  &-input::-webkit-input-placeholder 
    color: #7C7C8D
  &-input::-moz-placeholder
    color: #7C7C8D
  &-select 
    width: 380px
    height: 36px
    font-size: 18px
    background: #242731
    color: #E0E4E7
    outline: none
    padding: 4px
    border: none
    border-radius: 8px
    overflow: hidden
  &-checkbox 
    width: 380px
    position: relative
    display: flex
    flex-direction: row
    margin-left: 10px
  &-title
    color: #fff
    margin-left: 64px
    margin-top: 24px
    width: 100%
    height: 56px
  &-btn 
    width: 320px
    font-size: 20px
    background: #FF7518
    color: #E0E4E7
    border: none 
    border-radius: 16px
    padding-top: 16px
    padding-bottom: 16px
    margin: 16px 
    cursor: pointer
    align-self: center
  &-empty
    width: 380px
  &-success 
    color: #fff 
    font-size: 18px  
.custom-checkbox
  position: absolute
  z-index: -1
  opacity: 0
.custom-checkbox+label 
  display: inline-flex
  align-items: center
  user-select: none
.custom-checkbox+label::before 
  content: ''
  display: inline-block
  width: 1em
  height: 1em
  flex-shrink: 0
  flex-grow: 0
  border-radius: 0.25em
  margin-right: 0.5em
  background-color: #1F2128
  background-repeat: no-repeat
  background-position: center center
  background-size: 50% 50%
.custom-checkbox:checked+label::before 
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 8 8'%3e%3cpath fill='%23fff' d='M6.564.75l-3.59 3.612-1.538-1.55L0 4.26 2.974 7.25 8 2.193z'/%3e%3c/svg%3e")
.error-input
  border: 1px solid red
  border-radius: 8px
.error-text
  color: red
  margin-top: 4px
  margin-left: 8px

// 
.form_label 
  width: 380px
  // height: 40px
  position: relative
.form_label input,
.field_multiselect 
  position: relative
  width: 100%
  display: block
  border: 1px solid #cdd6f3
  box-sizing: border-box
  border-radius: 8px
  padding: 12px 40px 10px 16px
  font-size: 14px
  color: #a8acc9
  outline-color: #cdd6f3
.form_label input::placeholder,
.field_multiselect::placeholder 
  color: #a8acc9
.field_multiselect 
  width: 380px
  background: #242731
  color: #7C7C8D
  border: none
  border-radius: 8px
  ////тута
.field_multiselect:after 
  content: ""
  position: absolute
  right: 14px 
  top: 12px
  width: 6px
  height: 16px
  background: url("data:image/svg+xml,%3Csvg width='6' height='16' viewBox='0 0 6 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M3 0L6 5H0L3 0Z' fill='%23A8ACC9'/%3E%3Cpath d='M3 16L6 11H0L3 16Z' fill='%23A8ACC9'/%3E%3C/svg%3E") 50% 50% no-repeat
.multiselect_block 
  position: relative
  width: 100%
.field_select 
  position: absolute
  top: calc(100% - 2px)
  left: 0
  width: 100%
  height: 97px
  border: 2px solid #cdd6f3
  border-bottom-right-radius: 2px
  border-bottom-left-radius: 2px
  box-sizing: border-box
  outline-color: #cdd6f3
  z-index: 6
.field_select[multiple] 
  overflow-y: auto
.field_select option 
  display: block
  padding: 8px 16px
  width: 100%
  cursor: pointer
.field_select option:hover 
  background-color: lightgray
.multiselect_label 
  position: absolute
  top: 1px
  left: 2px
  width: 100%
  height: 40px
  cursor: pointer
  z-index: 3
.field_select 
  display: none
input.multiselect_checkbox 
  position: absolute
  right: 0px
  top: 0
  width: 40px
  height: 40px
  border: none
  opacity: 0
.multiselect_checkbox:checked ~ .field_select 
  display: block
.multiselect_checkbox:checked ~ .multiselect_label 
  width: 40px
  height: 40px
  left: initial
  right: 0px  
  top: 0px
  border-radius: 8px
  background: #242731 url("data:image/svg+xml,%3Csvg width='24' height='24' viewBox='0 0 24 24' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M19.4958 6.49499C19.7691 6.22162 19.7691 5.7784 19.4958 5.50504C19.2224 5.23167 18.7792 5.23167 18.5058 5.50504L12.5008 11.5101L6.49576 5.50504C6.22239 5.23167 5.77917 5.23167 5.50581 5.50504C5.23244 5.7784 5.23244 6.22162 5.50581 6.49499L11.5108 12.5L5.50581 18.505C5.23244 18.7784 5.23244 19.2216 5.50581 19.495C5.77917 19.7684 6.22239 19.7684 6.49576 19.495L12.5008 13.49L18.5058 19.495C18.7792 19.7684 19.2224 19.7684 19.4958 19.495C19.7691 19.2216 19.7691 18.7784 19.4958 18.505L13.4907 12.5L19.4958 6.49499Z' fill='%234F5588'/%3E%3C/svg%3E") 50% 50% no-repeat

@media (max-width: 856px) 
  .form
    overflow: hidden
    &-table 
      display: flex
      flex-direction: column
      justify-content: center
      width: 100%
      padding: 0
      
    &-input
      min-width: 0px
      max-width: 380px
      width: 80%
    &-select   
      min-width: 0px
      max-width: 380px
      width: 80%
    &-section
      display: flex
      align-items: center
      width: 100vw
      &-radiobuttons 
        max-width: 380px
        width: 80%
        &-wrap 
          width: 100%
          display: flex
          justify-content: center
          align-items: center
    &-checkbox 
      max-width: 380px
      width: 80%
    &-empty
      width: 100vw
    &-title 
      margin-left: 0
      text-align: center
    &_label 
      width: 80%
      max-width: 380px   
  .field_multiselect    
    width: 100%
    max-width: 380px    
</style>