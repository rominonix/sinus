<template>
<div class="my-account">
  <h2>Personal data</h2>
  <ul>
    <li>
     <p class="profile-info"><strong>Name</strong>: {{ user.name }} <br> </p> 
    <p class="profile-info"><strong>Address</strong>: {{ user.address.street }}, {{ user.address.zip }}, {{ user.address.city }}<br></p> 
       <p class="profile-info"><strong>Email</strong>: {{ user.email }} <br></p> 
       <p class="profile-info"><strong>Role</strong>: {{ user.role }}</p> 
       <p class="profile-info"><strong>Order history</strong>: {{ user.orderHistory }}</p>
    </li>
  </ul>
</div>
</template>

<script>

export default {
  name:'UserInfo',

  computed:{
    user(){
      return this.$store.state.userInfo.user
    }
  }
  
}

</script>

<style scoped>

.my-account{
  display: flex;
  flex-direction: column;
  min-width: 600px;
  padding: 0 3rem;
}

li {
  padding: 3%;
  font-size: 1.2rem;
}
.profile-info{
  padding: 4%;
}
</style>