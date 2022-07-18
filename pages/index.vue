<template>
  <mp-flex height="100vh" align-items="center" justify-content="center">
    <mp-box text-align="center" max-width="sm">
      <mp-icon name="mekari-brand" size="xl" margin-bottom="5" />
      <mp-heading>Hello Pixel 2 - Templates</mp-heading>
      <mp-text font-size="lg" margin-y="5">
        <strong>SSR</strong> : {{ ssr.body }}
      </mp-text>
      <mp-text font-size="lg" margin-y="5">
        <strong>CSR</strong> : {{ csr.body }}
      </mp-text>
      <mp-flex direction="column" gap="2">
        <mp-input v-model="name" placeholder="Input your name" />
        <mp-button as="a" :href="`/hello/${name}`" :is-disabled="!name">
          Go
        </mp-button>
      </mp-flex>
      <mp-text margin-top="2" color="gray.600"> [Default Layout] </mp-text>
    </mp-box>
  </mp-flex>
</template>

<script>
export default {
  name: 'Home',
  async asyncData({ $http }) {
    const data = await $http.$get(
      'https://jsonplaceholder.typicode.com/posts/1'
    )
    return { ssr: data }
  },
  data() {
    return {
      name: '',
      csr: '',
    }
  },
  mounted() {
    this.fetchPost()
  },
  methods: {
    async fetchPost() {
      const data = await this.$http.$get(
        'https://jsonplaceholder.typicode.com/posts/2'
      )

      setTimeout(() => {
        this.csr = data
      }, 2000)
    },
  },
}
</script>
