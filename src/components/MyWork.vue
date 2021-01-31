<template>
<div id="work">
  <p>
    <router-link to="/components/Projects">Mes Projets</router-link>
    <router-link to="/components/Gallery">Mes Photos</router-link>
   
  </p>
  <router-view></router-view>
</div>
</template>

<script>
import Vue from 'vue'
import VueRouter from 'vue-router'

export default {
  name: "work",
  
  components: {
      work
    
  }}

Vue.use(VueRouter)

const User = {
  template: `
    <div class="user">
      <h2>User {{ $route.params.id }}</h2>
      <router-view></router-view>
    </div>
  `
}

const Projects = { template: '<div>Projets</div>' }
const Gallery = { template: '<div>Mes Photos</div>' }



const router = new VueRouter({
  routes: [
    { path: '/component/Mywork', component: User,
      children: [
        // UserHome will be rendered inside User's <router-view>
        // when /user/:id is matched
        { path: 'Photos', component: Gallery },
				
        // UserProfile will be rendered inside User's <router-view>
        // when /user/:id/profile is matched
        { path: 'Projects', component: Projects },

       
      ]
    }
  ]
})

const work = new Vue({ router }).$mount('#work')
</script>