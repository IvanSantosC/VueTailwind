<script setup lang="ts">
/**
 * Dashboard de Usuarios - Consumiendo API GoRest
 * Vue 3 + Composition API + Tailwind CSS
 */
import { ref, onMounted } from 'vue';
import axios from 'axios';
import UserCard from './components/UserCard.vue';

// Interface para tipado de usuario
interface User {
  id: number;
  name: string;
}

// Estado reactivo
const users = ref<User[]>([]);

/**
 * Obtiene usuarios desde la API GoRest
 * Usando async/await según las mejores prácticas
 */
const fetchUsers = async (): Promise<void> => {
  try {
    const response = await axios.get<User[]>(
      'https://gorest.co.in/public/v2/users'
    );
    users.value = response.data;

    if (users.value.length === 0) {
      users.value = [
        { id: 1, name: "Juan Pérez" },
        { id: 2, name: "María García" },
        { id: 3, name: "Carlos López" },
        { id: 4, name: "Ana Martín" }
      ];
    }
  } catch (err) {
    console.error('Error fetching users:', err);

    // Datos de respaldo en caso de error
    users.value = [
      { id: 1, name: "Usuario Demo" }
    ];
  }
};

// Cargar usuarios al montar el componente
onMounted(() => {
  fetchUsers();
});
</script>

<template>
  <div class="">
    <!-- Solo las UserCards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        <UserCard v-for="user in users" :key="user.id" :user="user" />
    </div>
  </div>
</template>
