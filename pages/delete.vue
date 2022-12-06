<template>
    <div>
        <button>Delete</button>
    </div>
</template>

<script setup lang="ts">
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();

async function main() {
  try {

    const res = await prisma.user.delete({
      where: {
        id: 3,
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