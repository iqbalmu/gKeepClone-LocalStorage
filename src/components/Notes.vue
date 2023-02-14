<template>
    <div class="notes" @click="$emit('detail-note', note.id)">
      <a>
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 14.66V20a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h5.34"></path><polygon points="18 2 22 6 12 16 8 16 8 12 18 2"></polygon></svg>
      </a>
      <h3>{{ note.title }}</h3>
      <p>{{ note.text }}</p>
    </div>
</template>

<script>
export default{
  name: 'notes-comp',
  props: ['note']
}
</script>

<style scoped>
.notes{
  background: white;
  padding: 30px;
  margin-bottom: 35px;
  box-sizing: border-box;
  width: 350px;  
  line-break: auto;
  height: fit-content;
  max-height: 300px;
  overflow-y: scroll;
  border-radius: 10px;
  border: .1px solid rgba(128, 128, 128, 0.291);  
  cursor: pointer;
  position: relative;
  overflow-wrap: break-word;
}
.notes:hover{
  box-shadow: 1px 1px 5px 2px rgba(46, 46, 46, 0.115);  
  border: none;
}
.notes:hover a{
  display: block;
}
h3{
  margin-bottom: 15px;
}
a{
  display: none;
  position: absolute;  
  top: 15px;
  right: 15px;
}
</style>
