<template>
  <div>
    <h1 class="text-subtitle-1 font-weight-bold grey--text mx-4 mb-5">
      {{ $t('title.index') }}
    </h1>

    <v-container>
      <template v-for="project of projects">
        <v-card :key="`${project.title}-card`" flat class="pa-3">
          <v-row no-gutters>
            <v-col cols="12" md="6" class="px-3">
              <div class="text-caption grey--text mb-2">
                タイトル
              </div>
              <div class="text-body1 font-weight-bold">
                {{ project.title }}
              </div>
            </v-col>
            <v-col cols="4" md="2" class="px-3">
              <div class="text-caption grey--text mb-2">
                アカウント名
              </div>
              <div class="text-body1 font-weight-bold text-truncate">
                {{ project.person }}
              </div>
            </v-col>
            <v-col cols="4" md="2" class="px-3">
              <div class="text-caption grey--text mb-2">
                締切日
              </div>
              <div class="text-body1 font-weight-bold">
                {{ project.due }}
              </div>
            </v-col>
            <v-col cols="4" md="2" class="px-3">
              <div class="text-caption grey--text mb-2">
                状態
              </div>
              <div class="text-body1 font-weight-bold">
                <v-chip small text-color="white" :class="statusColor(project.status)">
                  {{ project.status }}
                </v-chip>
              </div>
            </v-col>
          </v-row>
        </v-card>
        <v-divider :key="`${project.title}-divider`" />
      </template>
    </v-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      projects: [
        { title: 'Design a new website', person: 'The Net Ninjaaaaaaaaa', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' }
      ]
    }
  },
  head () {
    return {
      title: this.$t('title.index')
    }
  },
  computed: {
    statusColor () {
      return (status) => {
        switch (status) {
          case 'complete':
            return 'light-blue accent-2'
          case 'ongoing':
            return 'light-green accent-2'
          case 'overdue':
            return 'pink accent-2'
        }
      }
    }
  }
}
</script>
