<template>
  <ThemeProvider>
    <MpReset />
    <client-only>
      <!-- this component will only be rendered on client-side -->
      <slot />

      <!-- loading indicator, rendered on server-side -->
      <template #placeholder> </template>
    </client-only>
  </ThemeProvider>
</template>
