<template>
  <Header></Header>
  <main>
    <form-input v-on:add-note="submit"></form-input>
    <div class="warp-notes">
      <modal-notes v-show="showModal" :selectNote="selectNote" v-on:done="doneNote" v-on:delete="deleteNote"></modal-notes>
      <Notes v-for="note in notes" :key="note.id" :note="note" v-on:detail-note="detail"></Notes>
    </div>
  </main>
  <footer></footer>
</template>

<script>

import Header from './components/Header.vue';
import FormInput from './components/FormInput.vue';
import Notes from './components/Notes.vue'
import ModalNotes from './components/ModalNotes.vue'
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {
    Header,
    'form-input': FormInput,
    Notes,
    'modal-notes': ModalNotes
  },
  created(){
    this.notes = JSON.parse(localStorage.getItem('notes')) || []
  },
  data() {
    return {
      notes: [],
      selectNote: {
        id : '', 
        title: '',
        text: ''
      },
      showModal: false
    }
  },
  methods: {
    submit(event) {
      const el = event.target.elements
      const title = el.title.value;
      const text = el.text.value;
      
      this.notes.unshift({ 
        id: uuidv4(),
        title,
        text 
      })

      this.setStorage(this.notes)

      el.text.style.height = '50px'
      el.title.value = ''
      el.text.value = ''      
    },
    detail(id){
      const note = this.notes.filter((note) => note.id === id)[0]     
      this.selectNote = {
        id: note.id,
        title: note.title,
        text: note.text
      }
      this.showModal = true
    },
    doneNote(event, id){
      const el = event.target.elements
      const title = el.title.value;
      const text = el.text.value;      
      const index = this.notes.findIndex( note => note.id == id)

      this.notes[index].title = title
      this.notes[index].text = text
            
      this.setStorage(this.notes)

      this.showModal = false
    },
    deleteNote(id){
      let notes = this.notes = this.notes.filter( (note) => note.id !== id )

      this.setStorage(notes)

      this.showModal = false
    },
    setStorage(data){
      localStorage.setItem('notes', JSON.stringify(data))
    }
  }
}
</script>

<style>
* {
  margin: 0;
}

body {
  background: rgb(245, 245, 245);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100vw;
  padding: 15px 7vw;
  box-sizing: border-box;
  height: auto;
}

.warp-notes {
  display: grid;
  grid-template-columns: auto auto auto;
  margin-top: 70px;
}
</style>
