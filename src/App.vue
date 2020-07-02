<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Notes App</h1>

    <AddNote 
      @addNote = "addNote"
    />
    
    <NotesList  v-bind:notes = 'notes'
                v-bind:search = 'query'
                @removeNote = 'removeNote'
                @changeQuery = 'changeQuery'
     />
  </div>
</template>

<script>

import AddNote from '@/components/AddNote'
import NotesList from '@/components/NotesList'

export default {
  name: 'App',
  components: {
    AddNote,
    NotesList
  },
  data: function(){
    return {
        notes: [
          {id: 1, title: "First note", 'desc': "this is first note", date: "02.07.2020, 10:34:42", show: true},
          {id: 2, title: "Second note", 'desc': "this is Second note", date: "02.07.2020, 10:34:42", show: true},
          {id: 3, title: "Third note", 'desc': "this is Third note", date: "02.07.2020, 10:34:42", show: true}
        ],
        query: ""
    }
  },
  watch: {
    query : function(){
      console.log(this.query);
    }
  },
  methods: {
    addNote(item){
      this.notes.push(item)
    },
    removeNote(item){      
      this.notes = this.notes.filter(t => t.id != item);
    },
    changeQuery(query){
      this.query = query;
    }
  },
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap');
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
    outline: none;
}
body{
  background-color: #f7f7f7;
}
#app {
  color: #2c3e50;
  max-width: 800px;
  margin: 0 auto;
  font-size: 16px;
  margin-top: 60px;
}
h1{
  text-align: center;
}
img{
  margin:  0 auto;
  display: flex;
}
button, input, select, textarea {
    border: 1px solid #dcdfe6;
}
    
</style>
