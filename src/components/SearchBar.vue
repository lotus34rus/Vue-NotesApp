<template>
    <div class="search-bar">
        <h1>Note App</h1>
        <input type="text" v-model="query" placeholder="Find your note">
        <div class="icons">
            <svg @click="$emit('setGridWidth')" v-bind:class="{active: !full}"  xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"  style="cursor: pointer;"><rect data-v-7c74c7b6="" x="3" y="3" width="7" height="7"></rect><rect data-v-7c74c7b6="" x="14" y="3" width="7" height="7"></rect><rect data-v-7c74c7b6="" x="14" y="14" width="7" height="7"></rect><rect data-v-7c74c7b6="" x="3" y="14" width="7" height="7"></rect></svg>
            <svg @click="$emit('setFullWidth')" v-bind:class="{active: full}" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"  style="cursor: pointer;"><line data-v-7c74c7b6="" x1="8" y1="6" x2="21" y2="6"></line><line data-v-7c74c7b6="" x1="8" y1="12" x2="21" y2="12"></line><line data-v-7c74c7b6="" x1="8" y1="18" x2="21" y2="18"></line><line data-v-7c74c7b6="" x1="3" y1="6" x2="3" y2="6"></line><line data-v-7c74c7b6="" x1="3" y1="12" x2="3" y2="12"></line><line data-v-7c74c7b6="" x1="3" y1="18" x2="3" y2="18"></line></svg>
        </div>
    </div>
</template>


<script>

export default {
    name: "SearchBar",
    data : function(){
        return {
            query: ''
        }
    },
    watch: {
        query: function(){
            this.$emit('changeQuery', this.query)
        }
    } ,
    props: ['full']  
}
</script>


<style scoped>
    .search-bar{
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 50px;
    }
    .search-bar input{
        padding: 16px 16px 16px 56px!important;
        margin-bottom: 0;
        border-radius: 30px;
        color: #909399;
        font-size: 16px;
        min-width: 400px;
        height: auto;
    }
    svg.active {
        color: #402caf;
    }
 
</style>