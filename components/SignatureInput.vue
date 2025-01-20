<template>
  <div>

    <div class="col-span-1 flex flex-col gap-2">
      <label :for="id" class="font-semibold">{{ title }}</label>
      <input :id="id" :type="type" :placeholder="title" class="input input-bordered w-full max-w-xs"
        :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
    </div>

  </div>
</template>

<script>
export default {
  components: {},

  props: {
    id: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    modelValue: {
      type: String,
      required: true
    },
  },

  emits: ['update:modelValue'],

  data() {
    return {}
  },

  watch: {},

  computed: {},

  mounted() { },

  methods: {},
}
</script>