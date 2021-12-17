<template>
  <v-dialog v-model="dialog" width="600">
    <template #activator="{ on, attrs }">
      <v-btn depressed color="blue accent-1" v-bind="attrs" v-on="on">
        プロジェクトを追加
      </v-btn>
    </template>
    <v-card class="pa-5 text-center">
      <v-form ref="form" v-model="valid">
        <v-text-field v-model="project.title" autofocus :label="labeles.title" :rules="rules.title" />
        <v-textarea v-model="project.info" :label="labeles.info" :rules="rules.info" />

        <v-menu offset-y max-width="290">
          <template #activator="{ on, attrs }">
            <v-text-field v-model="project.due" :label="labeles.due" :rules="rules.due" v-bind="attrs" v-on="on" />
          </template>

          <v-date-picker v-model="project.due" :locale="datePicker.locale" :first-day-of-week="datePicker.firstDayOfWeek" :day-format="datePicker.dayFormat" />
        </v-menu>

        <v-btn depressed dark color="blue darken-2" :loading="loading" @click="addProject">
          プロジェクト追加
        </v-btn>
      </v-form>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data () {
    return {
      dialog: false,
      valid: false,
      loading: false,
      project: {
        title: '',
        info: '',
        due: null
      },
      labeles: {
        title: 'プロジェクト名',
        info: '内容',
        due: '期限'
      },
      rules: {
        title: [
          v => !!v || 'プロジェクト名を入力して下さい',
          v => v.length <= 15 || '15文字以内'
        ],
        info: [
          v => !!v || '内容を入力して下さい',
          v => v.length <= 30 || '30文字以内'
        ],
        due: [
          v => !!v || '期限を入力して下さい',
          v => /\d{4}-\d{2}-\d{2}/.test(v) || '正しいフォーマットで入力して下さい'
        ]
      },
      datePicker: {
        locale: 'ja-jp',
        firstDayOfWeek: 1,
        dayFormat (d) {
          return new Date(d).getDate()
        }
      }
    }
  },
  methods: {
    addProject () {
      const form = this.$refs.form
      if (form.validate()) {
        this.loading = true
        setTimeout(() => {
          console.dir(this.project)
          form.reset()
          this.loading = false
        }, 1000)
      }
    }
  }
}
</script>
