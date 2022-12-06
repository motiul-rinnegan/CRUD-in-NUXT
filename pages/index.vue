<template>
    <div>
      <button >Create</button>
    </div>

</template>

<script setup lang="ts">
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();
const email=ref('motiul@gmail.com');
const firstname=ref('Motiul');
async function main() {
  const user = await prisma.user.create({
    data: {
      
      email: email.value,
      firstname: firstname.value,
    },
  })
  console.log(user)
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