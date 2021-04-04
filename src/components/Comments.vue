<template>
    <div class="container">
                    <h1>Coméntarios</h1>
                    <hr>
            
                   <FormTodo v-on:add-todo="addComment"></FormTodo>
                    <hr>

                    <p v-if="comments.length <= 0">Sem coméntarios</p>
                    <!--listando os Comentarios -->
                    <div class="list-group">
                        <div class="list-group-item" v-for="(commenta, index) in allComments" :key="index">
                            <span class="comment-author">Author: 
                                <Strong>{{ commenta.name }}</Strong>
                            </span>
                            <p>{{ commenta.message }}</p>
                            <div>
                                <a href="#" v-on:click.prevent="removerComment(index)" >Excluir</a>
                            </div>
                        </div>
                    </div>
                    
                </div>
</template>

<script>
    import FormTodo from './FormTodo.vue';

  export default {
            components:{
                FormTodo
                       
            },
            data() {
                return {
                    comments: []
                    
                }
            },
            methods:{
                addComment(comment){
                    this.comments.push(comment);
                },
                removerComment(index){
                    this.comments.splice(index,1);
                }
            },
            computed: {
                allComments(){
                    return this.comments.map(commenta =>({
                        ...commenta,
                        name: commenta.name.trim() === '' ? 'Anônimo' : commenta.name
                    }))
                }
            },
            watch:{
                comments(val){
                    console.log('val',val)
                }
            }

        
    }
</script>