<template>
  <ClientOnly>
    <hr />
    <div v-if="data">
      <p>Host Data:</p>
      {{ data }}
    </div>
    <hr />
    <div v-if="error">
      <p>Error:</p>
      {{ error }}
    </div>
    <hr />
    <div v-if="error">
      <p>Status :</p>
      <strong>
        {{ error?.statusCode }}
      </strong>
      <p>
        {{ error?.cause }}
      </p>
    </div>
    <hr />
  </ClientOnly>
</template>
<script setup>
const { data, error, status } = await useFetch(
  "https://craft.alike.host/items/languages/?fields=code&fields=name&fields=dir"
);

if (error?.value) {
  console.log("Error : ", error.value);
  console.log("Status Code : ", error.value?.statusCode);
}

if (data?.value) {
  console.log("Response : ", data.value);
}

if (status?.value) {
  console.log("status : ", status.value);
}

onMounted(async () => {
  console.log("data", data.value);
});
</script>
