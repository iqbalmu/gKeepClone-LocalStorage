<template>
  <div class="modal">
    <div class="form-input">
      <form @submit.prevent="$emit('done', $event, selectNote.id)">
        <div class="form-group">
          <input name="title" type="text" placeholder="Title" :value="selectNote.title">
          <textarea name="text" placeholder="Take a note" @input="autoGrow" :value="selectNote.text"></textarea>
        </div>
        <a class="btn-delete" @click="$emit('delete', selectNote.id)">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
        </a>
        <button class="btn-done" type="submit">
          save
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ['selectNote'],
}
</script>

<style scoped>
.modal {
  /* display: none; */
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(231, 231, 231, 0.797);
}

.form-input form {
  width: 650px;
  height: auto;
  margin: 10% auto;
  flex-direction: column;
  align-items: center;
  position: relative;
}

.form-group {
  width: 100%;
  height: auto;
  background-color: white;
  border-radius: 10px;
  padding: 15px 0 60px;
  box-shadow: 1px 1px 5px 2px rgba(46, 46, 46, 0.115);
}

input,
textarea {
  width: 600px;
  height: auto;
  border: none;
  padding: 10px 0px;
}

::placeholder {
  font-weight: 600;
}

input:focus,
textarea:focus {
  outline: none;
}

input {
  font-weight: bold;
  font-size: 18px;
}

textarea {
  resize: none;
  min-height: 250px;
  max-height: 50vh;
  font-size: 14px;
}

button, a{  
  display: block;
  border-radius: 5px;
  border: none;
  position: absolute;  
  color: white;
  cursor: pointer;
}

.btn-delete {
  bottom: 20px;
  left: 30px;
  background: rgb(193, 72, 59);
  padding: 7px 8px 3px;
}

.btn-done {
  bottom: 20px;
  padding: 7px 10px;
  font-size: 12px;
  font-weight: 600;
  right: 30px;
  background: rgb(40, 185, 67);
}
</style>