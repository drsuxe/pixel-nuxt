<template>
  <mp-flex height="100vh" align-items="center" justify-content="center">
    <mp-box text-align="center" max-width="sm">
      <mp-avatar size="xl" :name="$route.params.name" margin-bottom="5" />
      <mp-text font-size="2xl" margin-bottom="5"
        >Hello {{ $route.params.name }} 👋
      </mp-text>

      <mp-box p="4" border="1px" rounded="md" my="4">
        <mp-text v-for="user in ssr" :key="user.id" text-align="left">
          - {{ user.name }}
        </mp-text>
      </mp-box>

      <mp-button as="a" href="/">Back</mp-button>
      <mp-text margin-top="2" color="gray.600"> [Hello Layout] </mp-text>
    </mp-box>
  </mp-flex>
</template>

<script>
export default {
  name: 'Welcome',
  layout: 'hello',
  async asyncData({ $http }) {
    const data = await $http.$get('https://jsonplaceholder.typicode.com/users')
    return { ssr: data }
  },
}
</script>
