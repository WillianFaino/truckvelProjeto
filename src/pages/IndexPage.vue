<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
  </q-page>
</template>

<script setup>
  import { ref, onMounted } from 'vue';
  import { useQuasar } from 'quasar';
  import { api } from 'src/boot/axios';

  const $q = useQuasar();
  const users = ref([]);

  async function getUsers() {
    try {
      const response = await api.get('/users?page=1')
      users.value = response.data.data
      console.log(users.value)
    } catch (error) {
      $q.notify({
        color: 'negative',
        position: 'top',
        icon: 'report_problem',
        type: 'negative',
        message: 'Failed: ' + error.message
      });
    }
  }

async function registerUser() {
  try {
    const response = await api.post()
  } catch (error) {

  }
}

  onMounted(() => {
    getUsers();
  })

</script>
