<template>
<div id="app">
<layout>
	<template #header="h" >

<div id="app">
  <v-app id="inspire">
    <div>
      <v-toolbar>
        <v-toolbar-title>SHIP</v-toolbar-title>
        <v-icon>mdi-anchor</v-icon>
  
        <v-spacer></v-spacer>
  
        <v-toolbar-items>
          <v-btn text>JOIN</v-btn>
          <v-btn text>LOGIN</v-btn>
          <v-btn text>MY PAGE</v-btn>
        </v-toolbar-items>
  
        <template v-if="$vuetify.breakpoint.smAndUp">
          <v-btn icon>
            <v-icon>mdi-export-variant</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-delete-circle</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-plus-circle</v-icon>
          </v-btn>
        </template>
      </v-toolbar>
    </div>
  </v-app>
</div>
    
	</template>

	<template #sidebar="sidebar">
      <!-- <div v-switch="sidebarCheck">
        <h4 v-case="'presidebar'">
          <component :is="'pre-sidebar'"></component></h4>
        <h4 v-case="'adminsidebar'">
          <component :is="'admin-sidebar'"></component> </h4>
        <h4 v-case="'studentsidebar'">
          <component :is="'student-sidebar'"></component> </h4>
      </div> -->
      <!-- <component :is="sidebarCheck"></component> -->
      <ul class="menu" >
				<li v-for="sidebar of sidebarCheck" :key="sidebar.menu">
					<router-link :to='sidebar.link'>{{sidebar.menu}}</router-link>
				</li>
			</ul>	
  </template>

	<template #content ="c" class="c">
     <router-view></router-view>
	</template>

	<template #footer ="f">
	<h3>footer</h3>
  </template>

</layout>
</div>
</template>

<script>
import Layout from '@/components/cmm/Layout.vue'
export default {
  components:{
    Layout
  },
  data(){
    return{
		}
  },
  methods:{
    logout(){
      this.$store.state.admin={}
      this.$store.state.admin.isAuth=''
      this.$router.push({path : '/'})
    }
  },
  computed:{
    loginCheck() {
      if(this.$store.state.admin.isAuth==''){
        return false
      }else{
        return true
        }
      },
		sidebarCheck(){
      if(this.$store.state.admin.isAuth==''){
        return this.$store.state.common.sidebars
      }else{
        return this.$store.state.admin.sidebars
      }
    },
  }
}
</script>
<style scoped>
v-toolbar{
  background-color:black;
}
li {
   position:relative;
    padding: 5px 5px 5px 5px;
    list-style: none;
}
header {
}

</style>