<template>
  <div>
    <h1>SignUp</h1>
    <v-text-field label="아이디"   v-model="userId"   type="text"></v-text-field>
    <v-text-field label="비밀번호" v-model="password" type="password" ></v-text-field>
    <v-text-field label="이름"     v-model="name"></v-text-field>
    <v-text-field label="주소"     v-model="address"></v-text-field>
    <v-text-field label="이미지"   v-model="src"></v-text-field>

    <v-btn @click="signUp">회원가입</v-btn>
  </div>
</template>

<script>
import { EventBus } from '@/main.js'
import { mapMutations, mapActions } from 'vuex'

export default {
  data() {
    return {
      userId: null,
      password: null,
      name: null,
      address: null,
      src: null
    }
  },
  methods: {
    // ...mapMutations(['addUsers']),
    ...mapActions(['addUsers']),
    signUp() {
      let userObj = {
        userId: this.userId,
        password: this.password,
        name: this.name,
        address: this.address,
        src: this.src
      }
      // mutations - commit 불러오는 방법
      // this.$store.commit('addUsers', userObj)

      // mutations - ...mapMutations 불러오는 방법
      // this.addUsers(userObj)

      // EventBus 로 쓰는 방법
      // EventBus.$emit('signUp', userObj)

      // actions - dispatch 불러오는 방법
      // this.$store.dispatch('addUsers', userObj)

      // actions - ...mapActions 불러오는 방법
      this.addUsers(userObj)

      this.clearForm()
    },
    clearForm() {
      this.userId = null,
        this.password = null,
        this.name = null,
        this.address = null,
        this.src = null
    }

  }
}
</script>
