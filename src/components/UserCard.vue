<template>
  <div class="user-card">
    <!-- Sección superior -->
    <div class="card-header">
      <!-- Imagen de perfil circular -->
      <div class="profile-image">
        <img
          :src="getImageForUser(user.id)"
          :alt="`Imagen de ${user.name}`"
          @error="handleImageError"
        />
      </div>
      
      <!-- Información del usuario -->
      <div class="user-info">
        <p class="report-text">Report for</p>
        <h3 class="user-name">{{ user.name }}</h3>
      </div>
    </div>

    <!-- Sección inferior -->
    <div class="card-footer">
      <div class="option-item">Daily</div>
      <div class="option-item active">Weekly</div>
      <div class="option-item">Monthly</div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface User {
  id: number;
  name: string;
}

interface Props {
  user: User;
}

defineProps<Props>();

const getImageForUser = (id: number): string => {
  // Imágenes de paisajes originales del ejercicio
  const landscapeImages = [
    'https://mott.pe/noticias/wp-content/uploads/2016/07/Estas-fotograf%C3%ADas-capturaron-la-belleza-de-los-paisajes-de-Finlandia-e-Islandia-Mikko-Lagerstedt-1.1.jpg',
    'https://www.phototourbarcelona.com/wp-content/uploads/2020/05/3-1.jpg',
    'https://cdn-7.nikon-cdn.com/Images/Learn-Explore/Photography-Techniques/2016/Tony-Sweet-Landscapes/Media/Tony-Sweet-landscape-boat-01.jpg',
    'https://ecologiahoy.net/wp-content/uploads/2019/07/1-1-718x477.jpg',
    'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=400&h=250&fit=crop',
    'https://images.unsplash.com/photo-1518837695005-2083093ee35b?w=400&h=250&fit=crop'
  ];
  return landscapeImages[id % landscapeImages.length];
};

// Función para manejar errores de carga de imagen
const handleImageError = (event: unknown): void => {
  const img = (event as { target: { src: string } }).target;
  img.src = 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=400&h=250&fit=crop';
};
</script>

<style scoped>
.user-card {
  width: 280px;
  border-radius: 16px;
  overflow: hidden;
  background: white;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transition: all 0.3s ease;
}

.user-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.card-header {
  background: #5847EA;
  padding: 24px 20px;
  color: white;
  height: 280px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
}

.profile-image {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid white;
  margin: 0 0 24px 0;
  align-self: flex-start;
  transition: transform 0.3s ease;
}

.user-card:hover .profile-image {
  transform: scale(1.05);
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.user-info {
  text-align: left;
  width: 100%;
}

.report-text {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.7);
  margin: 0 0 8px 0;
  font-weight: 400;
}

.user-name {
  font-size: 32px;
  font-weight: 700;
  color: white;
  margin: 0;
  line-height: 1.1;
}

.card-footer {
  background: #1C1F4A;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.option-item {
  color: #94a3b8;
  font-size: 16px;
  font-weight: 500;
  padding: 8px 0;
  cursor: pointer;
  transition: color 0.2s ease;
  text-align: left;
}

.option-item:hover {
  color: #e2e8f0;
}

.option-item.active {
  color: #ffffff;
  font-weight: 600;
}
</style>
