<template>
  <div class="container h-100">
    <div class="row h-100">
      <div class="col-12 mx-auto">
        <div class="jumbotron text-center mt-5">
       <a href="https://www.xhostcom.com" target="_blank" title="Fish">
                                        <img src="@/assets/img/logo_small.png" alt="Fish">
   </a>
   <p class="lead">Yip, its an app to add and manipulate actual fish and their food!</p>
   <h3>
   Input Fish Species, and give it name.
   </h3>
   </div>
   <div class="mb-5">
  <form>
   <div class="form-group">
   <select v-model="selectedFish" class="form-control">
    <option disabled value="">Please select fish</option>
    <option v-for="fish in fishes" :key="fish.name" :value="fish">{{fish.fishType}}</option>
    </select>
   </div>
     <div class="form-group">
  <label for="name">Name Of Fish</label>
    <input id="name" type="text" class="form-control" v-model="fishName">
     </div>
    <input id="nr" type="hidden" class="form-control" v-model="fishNr">
    <button class="btn btn-success mb-3" @click.prevent="getFormValues()">
    Save
  </button>
   <button class="btn btn-secondary mb-3" @click.prevent="pushApi()">
    Send To Api
  </button>
  </form>
   <h4>Type: {{ selectedFish.fishType }}</h4>
   <h4>Name: {{ fish }}</h4>
   <h4>Feed Weight: {{ selectedFish.feedMass }}</h4>
   <h4 v-if ="selectedFish.feedMass">
   Total: {{ selectedFish.feedMass * fishNr }}
   </h4>
   <h3>{{ tank }}</h3>
   </div>
  </div>  
  </div>
  </div>
  
</template>

<script>
import axios from 'axios';
export default {
   data() {
     return {
   fishes: [
      {
        fishType: "Gold Fish",
        feedMass: 0.1
      }, 
      {
        fishType: "Angel Fish",
        feedMass: 0.2
      }, 
      {
        fishType: "Babel Fish",
        feedMass: 0.3
      }
    ],
    selectedFish: '',
    fishName: '',
    fishNr: 1,
    tank: []
     }
  },
  computed: {
    fish: function () {
      return this.fishName
    }
  },
  methods: {
    getFormValues () {
      this.selectedFish.fishName = this.fishName
      this.selectedFish.fishNr = this.fishNr
      this.tank.push(this.selectedFish)
      this.selectedFish = ''
      this.fishName = ''
      this.fishNr = 1
      console.log(this.tank)
     
  },
  //example Mocklab api to post tank data to, just returns back the JSON that was sent and 200 code, can be viewed in the console.
  pushApi() {
    const postTank = this.tank;
      axios
  .post('http://1eyr9.mocklab.io/tank', postTank)
  .then(function (response) {
    console.log(response);
  })
}
}
}

</script>
<style>
#__layout {
  height: 100vh;
}
.jumbotron {
  background-color: rgb(238, 228, 228);
}

</style>

