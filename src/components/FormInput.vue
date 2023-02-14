<template>
  <div class="form-input">
    <form @submit.prevent="$emit('add-note', $event)">
      <div class="form-group">
        <input name="title" type="text" placeholder="Title" @focusin="showTitle = true" v-show="showTitle" >
        <textarea name="text" placeholder="Take a note" @input="autoGrow" @focusin="showTitle = true"></textarea>
      </div>
      <button type="submit">+</button>
    </form>
  </div>
</template>

<script>
export default{
  data(){
    return{
      showTitle: false,      
    }
  },
  methods: {
    autoGrow(event){
      const el = event.target
      el.style.height = '3px'
      el.style.height = (el.scrollHeight)+'px'
    },
  }
}
</script>

<style scoped>
.form-input form{
  display: flex;  
  width: 550px;height: auto;
  margin: 30px auto;
  flex-direction: column;
  align-items: center;
  position: relative;
}
.form-group{
  width: 100%;
  height: auto;
  background-color: white;
  border-radius: 10px;
  padding: 15px 0 30px;
  box-shadow: 1px 1px 5px 2px rgba(46, 46, 46, 0.115);  
}
input,textarea{
  width: 500px;
  height: auto;
  border: none;
  padding: 10px 0px 0;
}
::placeholder{
  font-weight: 600;
  color: rgba(119, 119, 119, 0.911);
}
input:focus, textarea:focus{
  outline: none;
}
input{
  font-weight: bold;
  font-size: 18px;
}
textarea{
  resize: none;
  min-height: 50px;
  max-height: 50vh;
  font-size: 14px;
}
button{
  width: 40px;
  height: 40px;
  line-height: 0;
  border-radius: 50%;
  border: none;
  position: absolute;
  bottom: -20px;
  right: 20px;
  background: rgb(33, 115, 159);
  color: white;
  font-size: 25px;
  font-weight: 600;
  cursor: pointer;
}
</style>