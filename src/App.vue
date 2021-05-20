<template>
  <v-app>
    <v-main>
      <v-row justify="space-around">
        <v-date-picker
          v-model="picker"
          :year-format="yearFormat"
          :header-date-format="headerDateFormat"
          color="green lighten-1" />
        <v-date-picker
          v-model="picker"
          color="green lighten-1"
          header-color="primary" />
      </v-row>
      <v-row justify="center">
        {{ picker }}
      </v-row>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      picker: null
    }
  },
  methods: {
    yearFormat (val) {
      const year = parseInt(val) + 543
      return year
    },
    headerDateFormat (val) {
      const dateArr = val.split('-')
      const titleDateFormat = []
      if (dateArr[1]) {
        titleDateFormat.push(this.$dayjs(dateArr[1]).format('MMM'))
      }
      if (dateArr[0]) {
        titleDateFormat.push(this.yearFormat(this.$dayjs(dateArr[0]).format('YYYY')))
      }
      return titleDateFormat.join(' ')
    }
  }
}
</script>
