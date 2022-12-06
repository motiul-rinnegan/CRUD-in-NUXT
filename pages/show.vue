<template>
    <div v-for="item in users" v-bind:key="item">
        <p>Result: {{item.email}}</p>
    </div>
</template>

<script setup lang="ts">
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();
const users=ref();
async function main() {
   
  const users = await prisma.user.findMany()
  console.log(users)
}

main()
  .then(async () => {
    await prisma.$disconnect()
  })
  .catch(async (e) => {
    console.error(e)
    await prisma.$disconnect()
    process.exit(1)
  })
</script>

<style scoped>

</style>