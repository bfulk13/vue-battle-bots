<template>
    <div id="app">
        <div class="nav">
            <button @click='switchView(true)'>CREATE</button>
            <h1>BATTLE BOTS</h1>
            <button @click='switchView(false)'>COLLECTION</button>
        </div>

        <section v-if='showForm'>
            <Create :createBot='createBot' />
        </section>

    <section v-else>
        <div>
            <h4 v-if='selectedBots[0]'>Bot #1: {{selectedBots[0].botName}}</h4>
            <h4 v-if='selectedBots[1]'>Bot #2: {{selectedBots[1].botName}}</h4>
            <button @click='battle'>BATTLE</button>
            <button @click='clearSelected'>CLEAR</button><hr>
        </div>
        <bot-list v-for='(bot, i) in botCollection'
            :key='i'
            :index='i'
            :botObj='bot'
            :deleteBot='deleteBot'
            :selectBot='selectBot'
        />
    </section>
  </div>
</template>


<script>
import BotList from './components/BotList/BotList';
import Create from './components/Create/Create';

export default {
  name: 'app',
  data: function(){
    return{
        botName: '',
        attack: '',
        health: '',
        showForm: true,
        botCollection: [],
        selectedBots: []
    }
  },
  methods: {
      switchView(val) {
          this.showForm = val;
      },
      deleteBot(i){
          this.botCollection.splice(i,1);
      },
      createBot(botName, attack, health){
        //   console.log('hit');
          this.botCollection.push({ botName, attack, health });
         console.log(this.botCollection)
          this.botName = '';
          this.attack = '';
          this.health = '';
          this.switchView(false);
      },
      selectBot(bot){
          if(this.selectedBots.length < 2){
              this.selectedBots.push(bot);
          } else {
              alert('Only 2 bots may battle at once');
          }
      },
      clearSelected(){
          this.selectedBots = [];
      },
      battle(){
          if(this.selectedBots[0].attack > this.selectedBots[1].attack){
              alert(`${this.selectedBots[0].botName} wins!`)
          } else {
              alert(`${this.selectedBots[1].botName} wins!`)
          }
      }
  },
  components: { Create, BotList },
}
</script>


<style>
/* html{
    box-shadow: border-box;
    margin: 0;
    padding: 0;
} */
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #FDA665;
  margin: 0;
}
button{
  color: #222;
}

.nav{
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    background: #05386B;
    color: #fff;
}
</style>
