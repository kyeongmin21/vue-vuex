<template>
  <div>
    <h1>All Users ({{ allUsersCount }})</h1>
    <h3>Seoul Users: {{ countOfSeoul }}</h3>
    <h3>Seoul Users Percent: {{ percentOfSeoul }}%</h3>
    <v-list two-line>
      <v-list-tile
        v-for="(user, index) in allUsers"
        :key="index"
        avatar
      >
        <v-list-tile-avatar color="grey lighten-3">
          <img :src="user.src">
        </v-list-tile-avatar>

        <v-list-tile-content>
          <v-list-tile-title v-html="user.name"></v-list-tile-title>
          <v-list-tile-sub-title>id:#{{ index }} / {{ user.address }} 거주</v-list-tile-sub-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>

  </div>
</template>

<script>
import {EventBus} from '../../main'
import {mapState, mapGetters} from 'vuex'

export default {
  data() {
    return {}
  },
  computed: {
  /*  객체로 쓰는 방법 (count, seouls, percent 로 바인딩 해줘야한다.)
      ...mapGetters({
      count: 'allUsersCount',
      seouls: 'countOfSeoul',
      percent: 'percentOfSeoul'
    })*/
    ...mapState(['allUsers']),
    ...mapGetters(['allUsersCount', 'countOfSeoul', 'percentOfSeoul'])
  },
  mounted() {
    EventBus.$on('signUp', users => {
      this.allUsers.push(users)
    })
  }
}
</script>
