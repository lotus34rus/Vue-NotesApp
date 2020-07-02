<template>
    <div class="add-note">
        <form @submit.prevent = 'addnote'>
                <div class="input-field">
                    <label> Title</label>
                    <input type="text" v-model="title">
                </div>

                <div class="input-field">
                    <label> Description </label>
                    <textarea v-model="text"></textarea>
                </div>
                <button type="submit">NEW NOTE</button>
        </form>
    </div>
</template>


<script>
export default {
    name: "AddNote",
    data: function(){
        return {
            title: '',
            text: ''
        }
    },
    methods: {
        addnote() {
            let date = new Date;
            let newNote = {
                id: Date.now(),
                title: this.title,
                desc: this.text,
                date: date.toLocaleString(),
                show: true
            }
            this.$emit('addNote', newNote);
            this.title = '';
            this.text = '';
        }
    },
}
</script>


<style scoped>

    .add-note{
        padding-top: 50px;
    }


    input {
        padding: 16px 26px;
        margin-bottom: 30px;
        border-radius: 20px;
    }

    input, textarea {
        width: 100%;
    }

    label {
        display: block;
        font-size: 24px;
        margin-bottom: 10px;
        text-align: center;
    }
    textarea {
        padding: 30px 27px;
        border-radius: 14px;
        resize: none;
        overflow: auto;
        vertical-align: top;
        box-shadow: none;
        -webkit-box-shadow: none
    }

    button{
        display: flex;
        padding: .8em 2.6em;
        margin: 20px 0;
        line-height: 1;
        text-transform: uppercase;
        cursor: pointer;
        border-radius: 30px;
        color: #fff;
        border: 1px solid #494ce8;
        background-color: #494ce8;
        font-size: 24px;
        margin: 0 auto;
        margin-top: 40px;        
    }
</style>