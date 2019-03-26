<template>
    <div>
        <form action="">
            <input type="text" v-model='botName' placeholder='Bot Name'/><br>
            <input type="text" v-model='attack' placeholder='Attack Value' /><br>
            <input type="text" v-model='health' placeholder='Health Value' />
        </form>
        <button @click='createBot(botName, attack, health)'>SUBMIT</button>
        <button @click='clearForm'>CLEAR</button>
    </div>
</template>


<script>
export default {
    data: function(){
        return{
            botName: '',
            attack: '',
            health: ''
        }
    },
    methods: {
        clearForm(){
            this.botName = '';
            this.attack = '';
            this.health = '';
        }
    },
    props: ['createBot']

}
</script>


<style>

</style>

