<template>
  <div>
    <div>
      E-mail
    </div>
    <input type="text" id="email" v-model="mail">
    <div>
      Message
    </div>
    <textarea id="message" rows="10" v-model="message"></textarea>
    <div>
      <button id="button" @click="submitGuest">SAVE</button>
    </div>
  </div>

</template>

<script>
export default {
  name:"GuestLedger",
  data() {
    return {
      guests:[],
      mail:'',
      message:''
    }
  },
  methods:{
    submitGuest(){
      this.guests.push({
        mail:this.mail,
        message:this.message
      })
      this.mail= ''
      this.message= ''
      console.log(this.guests)
    }
  }
}
</script>


<style scoped>
input[type=text] {
  width: 70%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
button {
  padding: 5px;
}
textarea {
  width: 70%;
}
</style>
