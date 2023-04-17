<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
const valid = ref(false)
const first_name = ref('')
const last_name = ref('')
const email = ref('')

const nameRules = ref([
  (value) => {
    if (value) return true

    return 'Name is required.'
  },
  (value) => {
    if (value?.length <= 10) return true

    return 'Name must be less than 10 characters.'
  },
])

const emailRules = ref([
  (value) => {
    if (value) return true

    return 'E-mail is requred.'
  },
  (value) => {
    if (/.+@.+\..+/.test(value)) return true

    return 'E-mail must be valid.'
  },
])
</script>

<template>
  <div class="d-flex align-center flex-column">
    <div class="text-subtitle-2">Andya With props: {{ msg }}</div>

    <v-card
      width="400"
      title="This is a title"
      subtitle="This is a subtitle"
      text="This is content"
    ></v-card>

    <div class="mt-4 text-subtitle-2">With slots</div>

    <v-card width="400">
      <template v-slot:title> This is a title </template>

      <template v-slot:subtitle> This is a subtitle </template>

      <template v-slot:text> This is content </template>
    </v-card>

    <div class="mt-4 text-subtitle-2">With markup</div>

    <v-card width="400">
      <v-card-item>
        <v-card-title>This is a title</v-card-title>

        <v-card-subtitle>This is a subtitle</v-card-subtitle>
      </v-card-item>

      <v-card-text> This is content </v-card-text>
    </v-card>
  </div>

  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="first_name"
            :rules="nameRules"
            :counter="10"
            label="First name"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="last_name"
            :rules="nameRules"
            :counter="10"
            label="Last name"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>
    <v-btn
      type="submit"
      block
      class="mt-2"
      >Submit</v-btn
    >
  </v-form>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
