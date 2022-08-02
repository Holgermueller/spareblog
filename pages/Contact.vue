<template>
  <div id="contact">
    <Socials />

    <ContactForm />
  </div>
</template>

<script>
import Socials from '../components/Socials.vue'
import ContactForm from '../components/ContactForm.vue'

export default {
  name: 'Contact',

  head() {
    return {
      title: 'Contact',
    }
  },

  components: {
    ContactForm,
    Socials,
  },
}
</script>

<style scoped></style>
