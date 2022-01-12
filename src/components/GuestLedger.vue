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
    <div id="guest" v-for="(guest,index) in guests" v-show="guests.length>0" :key="index">
      <div>Email: {{guest.mail}}</div>
      <div>Message: {{guest.message}}</div>
    </div>
  </div>

</template>

<script>
import axios from 'axios'
export default {
  name:"GuestLedger",
  data() {
    return {
      guests:[],
      mail:'',
      message:'',
    }
  },
  methods:{
    submitGuest(){
      axios.post('http://localhost:5000/guests',{
        "mail":this.mail,
        "message":this.message
      }).then(res => {
        console.log(res)
        this.getAllGuests()
      })
      this.mail= ''
      this.message= ''
      console.log(this.guests)
    },
    getAllGuests() {
      axios.get('http://localhost:5000/guests')
          .then(res => {
            this.guests=res.data
          })
    }
  },
  mounted() {
    axios.get('http://localhost:5000/guests')
        .then(res => {
          this.guests=res.data
        })
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
#guest {
  margin-top: 15px;
}
</style>
