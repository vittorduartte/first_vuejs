<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    
    <FormTodo v-on:add-todo="addComment"/>
    <p v-if="comments.length <= 0"><small>Não temos comentários para listar.</small></p>
    <div class="list-group">
      <div
        class="list-group-item list-group-item-action flex-column align-items-start"
        v-for="(comment, index) in allComments" v-bind:key="index"
      >
        <div class="d-flex w-100 justify-content-between">
          <p class="mb-1">
            Autor:
            <strong>{{ comment.name }}</strong>
          </p>
        </div>
        <p class="mb-1">{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FormTodo from './FormTodo' 

export default {
  components:{
      FormTodo
  },
  data() {
    return {
      comments: [],
      name: "",
      message: "",
    };
  },
  methods: {
    removeComment(index) {
      this.comments.splice(index, 1);
    },
    addComment(comment){
        this.comments.push(comment)
    }
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name,
      }));
    },
  },
};
</script>
            