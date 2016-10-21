<template>
    <div id="app">
        <hello></hello>
        <div id="example">
            <p v-if="seen">Original message: "{{ message }}"</p>
            <p>Computed reversed message: "{{ reversedMessage }}"</p>
            <p>{{ now }}</p>
        </div>
        <div>{{ fullName }}</div>
        <div class="static" :class="classObject">
        </div>
        <div :style="[baseStyles, overridingStyles]">
            我是很粗的红字
        </div>
        <test></test>
    </div>
</template>
<script>
import Hello from './components/Hello'
import Test from './components/Test'
export default{
    components: {
        Hello,
        Test

    },
    data(){
        return {
        message:"hello baby！",
        seen: 1,
        firstName: 'Foo',
        lastName: 'Bar',
        classObject:{
            isActive: 1,
            "str": 1,
        },
        baseStyles:{
             color: 'red',
            fontSize: '13px'
            },
         overridingStyles:{
            fontWeight:"bold"
         }
        }
    },
     computed: {
        reversedMessage: function () {
          // `this` points to the vm instance
          return this.message.split('').reverse().join('')
            },
        now: function () {
            return Date.now()
            },
        fullName:{
          // getter
            get: function () {
                return this.firstName + ' ' + this.lastName
            },
        // setter
            set: function (newValue) {
                var names = newValue.split(' ')
                this.firstName = names[0]
                this.lastName = names[names.length - 1]
            }
        }
    },
    methods:{

    },
    watch:{

    }
}

</script>

<style scoped lang="stylus">


</style>
