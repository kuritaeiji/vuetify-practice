<template>
  <div>
    <h1 class="grey--text text-subtitle-1 font-weight-bold mx-4">
      {{ title }}
    </h1>

    <v-container>
      <v-row>
        <v-col
          v-for="team of teams"
          :key="team.name"
          cols="12"
          sm="6"
          md="4"
        >
          <v-card flat class="pa-4 text-center">
            <v-avatar size="100" color="grey">
              <v-img :src="team.avatar" />
            </v-avatar>

            <v-card-text class="grey--text">
              <div class="text-h6 font-weight-bold">
                {{ team.name }}
              </div>
              <div>
                {{ team.role }}
              </div>
            </v-card-text>

            <v-card-actions class="d-flex justify-center">
              <v-btn text color="grey">
                <v-icon left>
                  mdi-message
                </v-icon>
                MESSAGE
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import avatar1 from '@/assets/avatar-1.png'
import avatar2 from '@/assets/avatar-2.png'
import avatar3 from '@/assets/avatar-3.png'
import avatar4 from '@/assets/avatar-4.png'
import avatar5 from '@/assets/avatar-5.png'

export default {
  data () {
    return {
      title: 'チーム',
      teams: [
        { name: 'The Net Ninja', role: 'Web developer', avatar: avatar1 },
        { name: 'Ryu', role: 'Graphic designer', avatar: avatar2 },
        { name: 'Chun Li', role: 'Web developer', avatar: avatar3 },
        { name: 'Gouken', role: 'Social media maverick', avatar: avatar4 },
        { name: 'Yoshi', role: 'Sales guru', avatar: avatar5 }
      ]
    }
  },
  head () {
    return {
      title: this.title
    }
  }
}
</script>
