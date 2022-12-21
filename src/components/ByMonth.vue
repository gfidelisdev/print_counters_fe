<template>
  <v-container fluid>
    <v-row>
      <v-col>
        <!-- Selectors for month and year, and a submit button -->
        <v-select :items="months" v-model="month" label="Mês"></v-select>

      </v-col>
      <v-col>
        <v-select :items="years" v-model="year" label="Ano"></v-select>
      </v-col>
      <v-col>
        <v-btn @click="generateReport()" icon color="success">
          <v-icon color="white">mdi-check</v-icon>
        </v-btn>

      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      month: 'Janeiro',
      months: [
        'Janeiro',
        'Fevereiro',
        'Março',
        'Abril',
        'Maio',
        'Junho',
        'Julho',
        'Agosto',
        'Setembro',
        'Outubro',
        'Novembro',
        'Dezembro'
      ],
      year: new Date().getFullYear(),
      years: Array(28).fill(0).map((e, i) => i + 2022)
    }
  },
  methods: {
    generateReport() {
      console.log(this.month)
      console.log(this.year)
      this.$axios.post('/bymonth', {
        month:this.month,
        year: this.year
      })
        .then(data => {
          console.log(data)
        })

    }
  },
}
</script>

<style>

</style>
