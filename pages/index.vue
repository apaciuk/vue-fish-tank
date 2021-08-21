<template>
  <div class="container h-100">
    <div class="row align-items-center h-100">
      <div class="col-12 mx-auto">
        <div class="jumbotron text-center">
            <a href="https://www.xhostcom.com" target="_blank" title="Fish">
                                        <img src="@/assets/img/logo_small.png" alt="Fish">
         </a>
          <p class="lead">Yip, its an app to add and manipulate actual fish.</p>
           <div>
          </div>
          <form>
           <div class="form-group mt-5">
          <input v-model="selected" class="form-control mb-4" placeholder="Type new fish species and add to tank" />
            <span>Fish Species {{ selected }}</span>
          </div>
          <div id="v-model-fish" class="form-group mt-5 mb-4">
          <select class="form-control" v-model="selected">
           <option disabled value="">Please select fish</option>
          <option value="Gold Fish">Gold Fish</option>
          <option value="Babel Fish">Babel Fish</option>
          <option value="Angel Fish">Angel Fish</option>
         </select>
         </div>
         <button class="btn btn-success bt-sm">Add Fish</button>
       

     </form>
  </div>
      
</div>
        </div>
      </div>
  
</template>

<script>

export default {
   data() {
    return {
      selected: 'Gold Fish'
    }
  }
}

</script>
<style>
#__layout {
  height: 100vh;
}
.jumbotron {
  background-color: #fff;
}

</style>

