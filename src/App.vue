<script>
import UserInput from "./components/UserInput.vue"
import LCDNumber from "./components/LCDNumber.vue"
export default{
  components:{
    UserInput,
    LCDNumber
  }
}
</script>

<template>
  <UserInput />
  <!-- <LCDNumber :horizantls="[1,0,1]" :verticals="[1,0,1,1]"/> -->
</template>

<style>

</style>
