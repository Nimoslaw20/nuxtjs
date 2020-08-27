<template>
  <v-layout>
    <v-flex class="text-center">
      <v-row>
        <v-col order="last">
          <v-card class="pa-2" height="200" outlined tile>
            First, but last
          </v-card>
        </v-col>
        <v-col>
          <v-card class="pa-2" height="200" outlined tile>
            Second, but unordered
          </v-card>
        </v-col>
        <v-col order="first">
          <v-card class="pa-2" height="200" outlined tile>
            Third, but first
          </v-card>
        </v-col>
      </v-row>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: 'Base'
}
</script>

<style scoped></style>
