<template>
  <div class="profile">
    <h1>Hej {{ this.$store.state.userInfo.user.name}} </h1>
    <div class="user-icon">
    <img src="@/assets/big-heart.svg" alt="">
    </div>
    <div class="info-user">
      <UserInfo/>
      <!-- <OrderHistoric/> -->
    </div>
  </div>
</template>

<script>
// import OrderHistoric from '@/components/OrderHistoric'
import UserInfo from '@/components/UserInfo'

export default {
  name: 'Profile',
  
  components: { UserInfo },
}

</script>

<style>

.profile{
  display:flex;
  justify-content: center;
  align-items: center;
  justify-items: center;
  background-color:#FFEBD3;
  flex-direction: column;
  padding: 3% 5%;
  background-image: url("../assets/background-profile.svg");
  background-repeat: no-repeat;
  background-position: center;
}

.user-icon{
  padding: 1% 0 3%;
}
.info-user{
  /* display: grid;
  grid-template-columns: 1fr 1fr; */
}

</style>