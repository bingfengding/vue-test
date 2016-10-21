
<template>
    <div id="Test">
        <p>{{ msg }}</p>
        <template v-if="ok">
            <h1>Title</h1>
            <p>Paragraph 1</p>
            <p>Paragraph 2</p>
        </template>
        <template v-else>
            <h1>Title</h1>
            <p>Paragraph 3</p>
            <p>Paragraph 4</p>
        </template>
        <p v-show="condition">我是真的组件</p>
        <p v-show="!condition">这可能也是一个组件</p>
        <ul>
            <template v-for="(item, index) of items">
            <li >
                {{ parentMessage }} - {{ index }} - {{ item.message }}
            </li>
            <li class="divider">我是特殊的</li>
            </template>
        </ul>
        <ul>
            <li v-for="(valueOne,keyOne,indexOne) in object">
                {{ indexOne + 2 }}.{{ keyOne }} : {{ valueOne }}
            </li>
        </ul>
        <div>
            <span v-for="n in 10">{{ n }}</span>
        </div>

        <p v-for="(valueOne,keyOne,indexOne) in object">
            {{ indexOne + 2 }}.{{ keyOne }} : {{ valueOne }}
        </p>
        <hr/>
        <input
            v-model="newTodoText"
           @keyup.enter="addNewTodo"
            placeholder="Add a todo"
        >
        <ul>
            <template  v-for="(todo, index) in todos" @remove="todos.splice(index, 1)">
                <li>{{index}}{{ todo }}</li>
                <button @click="remove">X</button>
            </template>

        </ul>
    </div>
</template>
<script>
    export default{
        components: {
            // <my-component> 将只在父模板可用
            'my-component': Child
            }
        data(){
            return{
                msg:'hello vue',
                ok:0,
                condition:1,
                parentMessage:"我是第几个",
                items:[
                    {message: '人类' },
			        {message: '神' }
                ],
                object: {
                    FirstName: 'John',
                    LastName: 'Doe',
                    Age: 30
                 },
                newTodoText: '',
                todos: [
                    'Do the dishes',
                    'Take out the trash',
                    'Mow the lawn'
                    ]
            }
        },
        methods: {
            addNewTodo: function () {
                this.todos.push(this.newTodoText)
                this.newTodoText = ''
            },

            remove:function(){
               $emit:"remove"
            }

        }

    }
</script>
<style lang="stylus" scoped rel="stylesheet/stylus">
    *
        margin 0
        padding 0
        line-height 1
        font-family Microsoft Yahei
        color rgb(51, 51, 51)
    a
        text-decoration none
        color inherit
    ul
    ol
        list-style none
    em
    i
        font-style normal
</style>
