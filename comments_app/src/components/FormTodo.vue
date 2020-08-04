<template>
  <form action>
    <div class="form-todo form-group">
      <p>
        <input type="email" class="form-control" name="name" placeholder="Nome" v-model="name" />
      </p>
      <p>
        <textarea
          class="form-control"
          name="message"
          rows="3"
          placeholder="Comentário"
          v-model="message"
        ></textarea>
      </p>
      <button v-on:click="addComment" type="button" class="btn btn-primary">Comentar</button>
    </div>
  </form>
</template>


<script>
export default {
    data(){
        return{
            name:'',
            message:''
        }
    },
    methods : {
        addComment() {
            if (this.message.trim() === "") {
                return;
            }

            this.$emit('add-todo',{
                name: this.name,
                message: this.message
            })

            this.name = "";
            this.message = "";
            }
    }
}
</script>