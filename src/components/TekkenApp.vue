<script>
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'
    
export default {
  name: 'TekkenApp',
  components: { Datepicker },
  props: {
    msg: String,
  },

  data() {
    return {
      inSignIn: false,
      inLogIn: false,

      logIn: false,

      cityId: 0,
      adresId:0,
      nickname: 'Enter nickname',
      password: 'Enter password',
      name: 'Enter name',
      surname: 'Enter surname',
      patronymic: 'Enter patronymic',
      birthDate: Date,
      eMail: 'Enter e-Mail',
      phoneNumber: '+7',

      locations: [
        { 
          city: 'г. Красноярск',
          adresses: ['ул. Качинская 66а', 'ул. Урванцева 21']
        },

        {
          city: 'г. Зеленогорск',
          adresses: ['ул. Калинина 25/3']
        },

        {
          city: 'г. Новосибирск',
          adresses: ['ул. Челюскинцев 50']
        },

        {
          city: 'г. Екатиринбург',
          adresses: ['ул. Добролюбова 16']
        },
          
        {
          city: 'г. Санкт-Петербург',
          adresses: ['ул. Типанова 21А']
        }
      ],

      database: {
        krs1: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],

        krs2: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],

        zgr: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],

        nsk: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],
          

        ekb: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],
          
        spb: [{
          nickname: String,
          password: String,
          name: String,
          surname: String,
          patronymic: String,
          birthDate: Date,
          eMail: String,
          phoneNumber: String,
          }],
          
      }
    }
  },

  methods: {
    showSingInMenu() {
      if(this.inSignIn == true) return;
      this.inSignIn = true; 
    },

    closeSingInMenu() {
      if (this.inSignIn == false) return;
      this.registration();
      this.inSignIn = false;
    },

    showLogInMeny() {
      if (this.inLogIn == true) return;
      this.inLogIn = true;
    },

    closeLogInMeny() {
      if (this.inLogIn == false) return;
      this.logIn = true;
      this.inLogIn = false;
    },

    registration() {
      
      // Push code must be here
      
      this.nickname = "Enter nickname";
      this.password = "Enter password";
      this.name = "Enter name";
      this.surname = "Enter surname";
      this.patronymic = "Enter patronymic";
      this.birthDate = Date;
      this.eMail = "Enter e-Mail";
      this.phoneNumber = "+7";
    }


  },
}

</script>

<template>
  <!--Bar-->
  <div class="navbar">
    <div class="left">
        <p class="roboto-font-navbar">Tekken Arena</p>
    </div>
    <div @click="showSingInMenu" class="right">
        <button class="btn roboto-btn">Sign In</button>
    </div>
    <div @click="showLogInMeny" class="right">
      <button class="btn roboto-btn">Log In</button>
    </div>
  </div>

  <!--Sign in-->
  <Transition name="modal">
    <div v-if="this.inSignIn" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container-sign-in">
          <div class="modal-header">
            <p name="header">
            
              <!--Chose location-->
              <div class="center">
                <div class="roboto-font-black">Fill in all fields</div>
                Pick location: <select v-model="cityId">
                  <option v-for="(location, index) in locations" :value="index" :key="index">
                    {{location.city}}
                  </option>
                </select>
                <select v-model="adresId">
                  <option v-for="(adres, index) in locations[cityId].adresses" :key="index">
                    {{adres}}
                  </option>
                </select>
              </div>
              
              <!--Other data-->
              <div class="left">
                Nickname: <input v-model="nickname" type="text" class="form-control">
                Password: <input v-model="password" type="text" class="form-control">
                Name: <input v-model="name" type="text" class="form-control">
                Surname: <input v-model="surname" type="text" class="form-control">
                Patronymic: <input v-model="patronymic" type="text" class="form-control">
              </div>

              <div class="right">
                e-Mail: <input v-model="eMail" type="text" class="form-control">
                Phone Number: <input v-model="phoneNumber" type="text" class="form-control">
                Birth Date :<Datepicker v-model="birthDate" class="birthDate"></Datepicker>

              </div>
            </p>
          </div>

          <div class="modal-body">
            <p name="body">
              <div class="d-flex">
                <button @click="(closeSingInMenu)" class="btn btn-primary right">
                  Register
                </button>
              </div>
            </p>
          </div>
        </div>
      </div>
    </div>
  </Transition>

  <!--Log in-->
  <Transition name="modal">
    <div v-if="this.inLogIn" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container-log-in">

          <div class="modal-body">

            <!--Chose location-->
            <div class="center">
              Pick location: 
              <select v-model="cityId">
                <option v-for="(location, index) in locations" :value="index" :key="index">
                  {{location.city}}
                </option>
              </select>
              <select v-model="adresId">
                <option v-for="(adres, index) in locations[cityId].adresses" :key="index">
                  {{adres}}
                </option>
              </select>
            </div>

            Nickname: <input v-model="this.nickname" type="text" class="form-control">
            Password: <input v-model="this.password" type="text" class="form-control">

            <div class="d-flex">
              <button @click="(closeLogInMeny)" class="btn btn-primary right margin-top">
                Log In
              </button>
            </div>

          </div>
        </div>
      </div>
    </div>
  </Transition>


</template>

<style scoped>

.center {
  margin: auto;
  text-align: left;
  padding-bottom: 20px;
}

.right {
  float: right!important;
}

.left {
  float: left!important;
}

.margin-top {
  margin-top: 20px;
}

.navbar {
  background:  #3428a0;
  padding: 10px;
  border-radius: 0;
}

.roboto-font-navbar {
  font-family: Roboto;
  font-size: 23px;
  color: white;
  margin: 4px;
}

.roboto-btn {
  font-family: Roboto;
  font-size: 16px;
  border: 1px black;
  background-color: white;
  color: black;
  margin: 5px;
}

.roboto-font-black {
  font-family: Roboto;
  font-size: 16px;
  color: black;
}


.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container-sign-in {
  width: 500px;
  height: 470px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-container-log-in {
  width: 500px;
  height: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header {
  border-top: 0 none;
  border-bottom: 0 none;
}

.modal-body {
  margin: 20px 0;
  border-bottom: 0 none;
}

.modal-footer {
    border-top: 0 none;
}

.birthDate {
  width: 200px;
}


</style>
