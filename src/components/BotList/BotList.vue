<template>
    <div>
       <div class='collection'>
           <div class='card'>
               <p>{{botObj.botName}}</p>
               <p>Attack: {{botObj.attack}}</p>
               <p>Health: {{botObj.health}}</p>
               <button @click='selectBot(botObj)'>SELECT</button>
               <button @click='deleteBot(index)'>RETIRE</button>
           </div>
       </div>
    </div>
</template>


<script>


export default {
    props: ['botObj', 'deleteBot', 'selectBot', 'index']
}
</script>


<style>

</style>
