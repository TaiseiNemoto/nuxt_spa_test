<script lang="ts" setup>
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
  id: number;
  name: string;
  username: string;
  email: string;
  address: Address;
  phone: string;
  website: string;
  company: Company;
}

const data: User[] = await $fetch('https://jsonplaceholder.typicode.com/users')
</script>

<template>
  <ul>
    <li v-for="user in data">
      <NuxtLink :to="`/user/${user.id}`">{{ user.name }}</NuxtLink>
    </li>
  </ul>
</template>