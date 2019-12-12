<template>
    <section>
        <ul>
            <li v-for="(todoItem,index) in propsdata" class="shadow" :key="todoItem" aria-hidden="true">
                <i class="checkBtn fas fa-check"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>
<script>
export default {
    props:['propsdata'],
    methods:{
        removeTodo(todoItem, index){
            // console.log(todoItem, index);
            this.$emit('removeTodo', todoItem , index);
        }
    }
}
</script>
<style scoped>
    ul{
        list-style: none;
        padding-left: 0;
        margin-top: 0;
        text-align: left;
    }
    li{
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding:0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }
    .removeBtn{
        margin-left: auto;
        color:#de4343;
    }
</style>