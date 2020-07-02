<template>
    <div>
        <SearchBar
            @changeQuery = 'changeQuery'
            v-bind:full = 'full'
            @setFullWidth = "setFullWidth"
            @setGridWidth = "setGridWidth"
         />
        <div class="notes_list">  
                <Note 
                    v-for="note in filtered"
                    v-bind:note = "note"
                    v-bind:key="note.id"
                    v-bind:full = 'full'
                    @removeNote = "$emit('removeNote', note.id)"
                />
        </div>
    </div>
   
</template>

<script>
import Note from '@/components/Note'
import SearchBar from '@/components/SearchBar'


export default {
    name: "NotesList",
    components: {
        Note,
        SearchBar
    },
    data: function(){
        return {
            full: false,
        }
    },
    methods: {
        changeQuery: function(query){
             this.$emit('changeQuery', query);
        },
        setFullWidth: function(){
            this.full = true;
        },
        setGridWidth: function(){
            this.full = false;
        }

    },
    props: ["notes", 'search'],
    computed: {
        filtered : function(){
           if(this.search != '')
                return this.notes.filter(item=>item.title.toLowerCase().includes(this.search.toLowerCase()));
           else
                return this.notes;
        }
    },

}
</script>


<style scoped>
    .notes_list {
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
        padding: 40px 0;
    }
</style>
