<script setup lang="ts">

const dependencies = [
  {
    name: 'Lynis',
    installable: false,
    removable: false,
    description: 'Used for auditing you machine and checking for security vulnerabilities.',
    id: 'lynis'
  },
  {
    name: 'Uncomplicated Firewall',
    installable: true,
    removable: true,
    command: '...',
    description: 'Used for managing your firewall settings.',
    id: 'ufw'
  }
]
</script>

<template>
<div class="home">
  <h1 class="dependencies-title text-2xl font-bold">Dependencies</h1>
  <ol class="w-5/6">
    <li v-for="({ name, description, installable, id, removable }, index) in dependencies" :key="index" class="flex w-full justify-between items-center my-4 ">
      <div class="dependency-content">
        <h3 class="text-xl"> {{ index + 1 }}. {{ name }}</h3>  
        <p>{{ description }}</p>
      </div>
      <Suspense class="dependency-install">
        <Dependency :installable="installable" :removable="removable" :id="id" />
        <template #fallback>
          <p class="text-[#ccc] italic">Checking...</p>
        </template>
      </Suspense>
    </li>
  </ol>
</div>
</template>

<style lang="stylus">

</style>