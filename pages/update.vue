<template>
    <div>

    </div>
</template>

<script setup lang="ts">
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();

async function main() {
  try {
    
    const res = await prisma.user.update({
      where: {
        id: 7
      },
      data: {
        email: 'uniform@gmail.com',
        firstname: 'Uniform'
      },
    });

    console.log(res);
  } catch (err) {
    console.log(err);
  } finally {
    async () => {
      await prisma.$disconnect();
    };
  }
}

main();
</script>

<style scoped>

</style>