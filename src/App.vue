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
    
    // Si no hay usuarios de la API, agregar datos de ejemplo
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
  <div class="dashboard-container">
    <!-- Solo las UserCards -->
    <div class="users-grid">
      <UserCard
        v-for="user in users"
        :key="user.id"
        :user="user"
      />
    </div>
  </div>
</template>

<style scoped>
.dashboard-container {
  min-height: 100vh;
  width: 100vw;
  background: #1C1F4A;
  padding: 40px 20px;
  margin: 0;
  box-sizing: border-box;
}

.users-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
  justify-items: center;
  max-width: 1400px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .dashboard-container {
    padding: 20px 16px;
  }
  
  .users-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
}
</style>
