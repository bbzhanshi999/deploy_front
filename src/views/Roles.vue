<template>
  <div class="roles">
    <h1>角色列表</h1>
    <ul>
      <li v-for="(role, index) in roles" v-bind:key="role">{{ index }} - {{ role }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "roles",
  data () {
    return {
        roles:[]
    }
  },
  created(){
    this.fetchData()
  },
  methods:{
    fetchData(){
      axios.post("/api/roles",{username:this.$route.params.username}).then(function(res){
        for (var i=0;i<res.data.length;i++){
          this.roles.push(res.data[i])
        }
      })

    }
  }
};
</script>

