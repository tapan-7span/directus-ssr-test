<template>Hello Wrold</template>
<script setup>
const { data, error } = await useFetch("https://craft.alike.io/items/faqs");

onMounted(async () => {
  if (error?.value) {
    console.log("Error : ", error.value);
    console.log("Status Code : ", error.value?.statusCode);
  }
  console.log("data", data.value);
});
</script>
