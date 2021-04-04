<template >
  <div class="form-todo form-group">
    <p>
      <span style="color: #ff0000">*</span>
      <span>Seu nome</span>
      <input
        type="text"
        placeholder="nome"
        name="author"
        class="form-control"
        v-model="name"
      />
    </p>
    <p>
      <span style="color: #ff0000">*</span>
      <span>Seu Coméntario</span>
      <textarea
        name="message"
        placeholder="Comentário"
        class="form-control"
        v-model="message"
      ></textarea>
    </p>
    <button
      v-on:click="addComment"
      class="btn btn-outline-primary"
      type="submit"
    >
      Comentar
    </button>
  </div>
</template>
<script>
export default {
    data(){
        return {
            name: '',
            message: ''
        }
    },
    methods:{
        addComment(){
                  if( this.message.trim() === ''){
                      alert("Preencha os campos obrigatórios.");
                      return false;
                  }  

                  this.$emit('add-todo',{
                      name: this.name,
                      message: this.message,
                  });

                  this.name = '';
                  this.message = '';

                },
    }
};
</script>