<script setup lang="ts">
type Geo = {
  lat: string;
  lng: string;
}

type Address = {
  street: string;
  suite: string;
  city: string;
  zipcode: string;
  geo: Geo;
}

type Company = {
  name: string;
  catchPhrase: string;
  bs: string;
}

type User = {
  id: number | null;
  name: string;
  username: string;
  email: string;
  address: Address;
  phone: string;
  website: string;
  company: Company;
}

const user: Ref<User> = ref({
  id: null,
  name: '',
  username: '',
  email: '',
  address: {
    street: '',
    suite: '',
    city: '',
    zipcode: '',
    geo: {
      lat: '',
      lng: '',
    }
  },
  phone: '',
  website: '',
  company:{
    name: '',
    catchPhrase: '',
    bs: '',
  }
})

const route = useRoute()

onMounted(async () => {
  const route = useRoute()
  try {
    const data: User = await $fetch(`https://jsonplaceholder.typicode.com/users/${route.params.id}`)
    user.value = data
  } catch (err) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Page Not Found',
      fatal: true
    })
  }
})
</script>

<template>
  <p>hello {{ user.name }}</p>
</template>