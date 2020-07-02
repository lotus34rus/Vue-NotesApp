<template>
    <div v-bind:class ="{note, full: full }">
      <div class="note-header">
          <p>{{note.title}}</p>
          <p style="cursor: pointer;" @click="$emit('removeNote', note.id)">x</p>
      </div>

      <div class="note-body">
          <p>{{note.desc}}</p>
          <span>{{note.date}}</span>
     </div>

    </div>
</template>

<script>

export default {
    name: "Note",
    props: ["note", 'full']
}

</script>


<style scoped>
    .note{
        width: 48%;
        padding: 18px 20px;
        margin-bottom: 20px;
        background-color: #fff;
        transition: all .25s cubic-bezier(.02,.01,.47,1);
        box-shadow: 0 30px 30px rgba(0,0,0,.02);
        border:1px solid lightgray;
    }

    .note:hover{
        box-shadow: 0 30px 30px rgba(0,0,0,.04);
        transform: translateY(-6px);
        transition-delay: 0s!important;
    }
    .note.full {
        width: 100%;
        text-align: center;
    }
    .note.full .note-header{
        justify-content: center;
    }
    .note.full .note-header p{
        margin-right: 20px;
    }
    .note-header {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .note-header p {
        font-size: 22px;
        color: #402caf;
    }

    .note-body p {
        margin: 20px 0;
    }
    .note-body span {
        font-size: 14px;
        color: #999;
    }
</style>
