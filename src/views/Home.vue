<template>
  <default-dashboard />
</template>

<script>
import DefaultDashboard from "@/views/dashboards/Default.vue";

export default {
  name: "Home",
  components: {
    DefaultDashboard,
  },
  mounted(){
    let user = localStorage.getItem('user-info');
    if(!user){
      this.$router.push('/sign-in')
    }
  }
};
</script>
