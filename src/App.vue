<template>
  <div class="w3-container">
    <header class="w3-teal w3-center">
      <h1>Vuejs Form App</h1>
      <p class="w3-text-small">(validate, submit and reset)</p>
    </header>

      <form class="w3-container w3-text-teal w3-card-4" style="padding: 10px;" v-if="!submitted" >

        <label>First Name</label>
        <input class="w3-input" type="text" v-model="firstName" required />

        <label>Last Name</label>
        <input class="w3-input" type="text" v-model="lastName" required />

        <label>Email</label>
        <input class="w3-input" type="email" v-model="email" />

        <label>Password</label>
        <input class="w3-input" type="password" v-model="password" required />



        <div class="w3-container w3-light-grey w3-padding">
        <label>Store Data?</label>
        <br />
        <input class="w3-radio" type="radio" value="Yes" v-model="storeData" /> Yes

        <input class="w3-radio" type="radio" value="No" v-model="storeData" /> No

        <button @click="submit" type="submit" class="submit">Submit</button>
        </div>
      </form>

    <div class="w3-container w3-padding w3-border w3-card-4 w3-pale-green" style="margin-top: 50px;" v-else>
      <h3>Your Data:</h3>
      <p><b>Full Name: </b>{{firstName}} {{lastName}}</p>
      <p><b>Email: </b>{{email}}</p>
      <p><b>Password: </b>{{password}}</p>
      <p><b>Store in Database?: </b>{{storeData}}</p>
      <button class="w3-button w3-teal w3-right w3-round" @click="reset">Reset</button>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        firstName: '',
        lastName: '',
        email: '',
        password: '',
        storeData: 'Yes',
        submitted: false
      }
    },
    methods: {
      submit() {
        if (this.firstName && this.lastName && this.password !== '') {
          this.submitted = true;
        }
      },
      reset() {
        this.firstName = '';
        this.lastName = '';
        this.email = '';
        this.password = '';
        this.storeData = 'Yes';
        this.submitted = false;
      }
    }
  }
</script>

<style>
  /*Submit Button*/
  .submit {
    border: none;
    background-color: transparent;
    float: right;
    color: teal;
    padding: 5px;
  }
  .submit:hover {
    color: gray;
  }

  /*For Large Screens*/
  @media all and (min-width: 800px) {
    header, form {
      width: 75%;
      margin: auto;
    }
  }
</style>
