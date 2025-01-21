<template>
  <div class='space-y-4'>

    <!-- Title -->
    <section class='text-center'>
      <h1 class='font-bold text-2xl'>Email Signature Generator</h1>
    </section>

    <!-- Signature Preview -->
    <section class='grid grid-cols-3 gap-4'>
      <div class='col-span-1'>
        <div class='card bg-base-100 w-full shadow-xl h-80'>
          <div class='card-body'>
            <div class='flex flex-col text-left' ref='copyContent'>
              <!-- Image -->
              <img :src=signature.img alt="Signature image" width='100px'>
              <!-- Name -->
              <p>{{ signature.name }}</p>
              <!-- Title -->
              <p>{{ signature.title }}</p>
              <!-- Company -->
              <p>{{ signature.company }}</p>
              <!-- Website -->
              <a :href='`https://${signature.website.src}`' class='link link-primary'>{{ signature.website.name }}</a>
              <!-- Email -->
              <a :href='`mailto:${signature.email.src}`' class='link link-primary'>{{ signature.email.name }}</a>
              <!-- Phone -->
              <a :href='`tel:+${signature.phone.src}`' class='link link-neutral'>{{ signature.phone.name }}</a>
            </div>
          </div>
        </div>
      </div>

      <div class='col-span-2'>
        <div class='card bg-base-100 w-full shadow-xl p-5 space-y-4 h-80'>
          <div class='flex justify-between'>
            <div class='card-title'>HTML result</div>
            <button class='btn btn-primary' @click='copyClipboard'>Copy to clipboard</button>
          </div>
          <div class='p-4 bg-base-300 rounded-xl overflow-scroll'>
            <div class=" overflow-scroll">
              {{ copyData }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Signature Edit -->
    <section>
      <div class='card bg-base-100 w-full shadow-xl p-5'>
        <h2 class='card-title'>Change Signature Information</h2>
        <div class='card-body'>
          <div class='grid grid-cols-3 gap-8'>
            <signature-input id='signature_img_src' title='Image source' type='text'
              v-model='signature.img'></signature-input>

            <signature-input id='signature_name' title='Name' type='text' v-model='signature.name'></signature-input>

            <signature-input id='signature_title' title='Title' type='text' v-model='signature.title'></signature-input>

            <signature-input id='signature_company' title='Company' type='text'
              v-model='signature.company'></signature-input>

            <signature-input id='signature_website_src' title='Website source' type='text'
              v-model='signature.website.src'></signature-input>

            <signature-input id='signature_website_name' title='Website Name' type='text'
              v-model='signature.website.name'></signature-input>

            <signature-input id='signature_email_src' title='Email source' type='text'
              v-model='signature.email.src'></signature-input>

            <signature-input id='signature_website_name' title='Email Name' type='text'
              v-model='signature.email.name'></signature-input>

            <signature-input id='signature_phone_src' title='Phone source' type='text'
              v-model='signature.phone.src'></signature-input>

            <signature-input id='signature_phone_name' title='Phone Name' type='text'
              v-model='signature.phone.name'></signature-input>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script>
import { nextTick } from 'vue'
import SignatureInput from '~/components/SignatureInput.vue'

export default {
  components: {
    SignatureInput
  },

  data() {
    return {
      signature: {
        // img: '/signature.png',
        img: 'https://picsum.photos/id/237/400',
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
      },
      copyData: ''
    }
  },

  watch: {
    // TODO Watch copyData
    signature: {
      handler() {
        nextTick(() => {
          this.copyData = this.$refs.copyContent.outerHTML
        })
      },
      deep: true
    }
  },

  computed: {},

  mounted() {
    this.copyData = this.$refs.copyContent.outerHTML
  },

  methods: {
    /**
     * Copy Signature code into clipboard
     */
    async copyClipboard() {
      navigator.clipboard.writeText(this.$refs.copyContent.outerHTML)
    }
  },
}
</script>