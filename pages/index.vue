<template>
  <div class="space-y-10">

    <!-- Title -->
    <section class='text-center'>
      <h1 class="font-bold text-2xl">Email Signature Generator</h1>
    </section>

    <!-- Signature Preview -->
    <section class='flex justify-center'>
      <div class='flex flex-col text-left'>
        <!-- Image -->
        <NuxtImg :src=signature.img width="100px" />
        <!-- Name -->
        <p>{{ signature.name }}</p>
        <!-- Title -->
        <p>{{ signature.title }}</p>
        <!-- Company -->
        <p>{{ signature.company }}</p>
        <!-- Website -->
        <a :href="`https://${signature.website.src}`" class="link link-primary">{{ signature.website.name }}</a>
        <!-- Email -->
        <a :href="`mailto:${signature.email.src}`" class="link link-primary">{{ signature.email.name }}</a>
        <!-- Phone -->
        <a :href="`tel:+${signature.phone.src}`" class="link link-neutral">{{ signature.phone.name }}</a>
      </div>
    </section>

    <!-- Signature Edit -->
    <section class="space-y-8">
      <h2 class="font-bold text-xl">Change Signature Information</h2>

      <div class="grid grid-cols-3 gap-8">
        
        <signature-input id="signature_img_src" title="Image source" type="text" v-model="signature.img"></signature-input>

        <signature-input id="signature_name" title="Name" type="text" v-model="signature.name"></signature-input>

        <signature-input id="signature_title" title="Title" type="text" v-model="signature.title"></signature-input>

        <signature-input id="signature_company" title="Company" type="text" v-model="signature.company"></signature-input>

        <signature-input id="signature_website_src" title="Website source" type="text" v-model="signature.website.src"></signature-input>

        <signature-input id="signature_website_name" title="Website Name" type="text" v-model="signature.website.name"></signature-input>

        <signature-input id="signature_email_src" title="Email source" type="text" v-model="signature.email.src"></signature-input>

        <signature-input id="signature_website_name" title="Email Name" type="text" v-model="signature.email.name"></signature-input>

        <signature-input id="signature_phone_src" title="Phone source" type="text" v-model="signature.phone.src"></signature-input>

        <signature-input id="signature_phone_name" title="Phone Name" type="text" v-model="signature.phone.name"></signature-input>
        
      </div>
    </section>

  </div>
</template>

<script>
import SignatureInput from '~/components/SignatureInput.vue';

export default {
  components: {
    SignatureInput
  },

  data() {
    return {
      signature: {
        img: '/signature.png',
        name: 'John Doe',
        title: 'Accountant',
        company: 'Avocado Company',
        website: {
          src: 'www.avocado-my-company.com',
          name: 'www.avocado-my-company.com'
        },
        email: {
          src: 'john@avocado-company.com',
          name: 'john@avocado-company.com'
        },
        phone: {
          src: '999999999999',
          name: '999-99999-9999'
        }
      }
    }
  },

  watch: {},

  computed: {},

  mounted() { },

  methods: {
    submitForm() {

    }
  },
}
</script>