<template>
  <div id="app">
    <CarHeader app-name="Car Dealership">
      <template #nav>
        <CarButton @click="showInventory">Inventory</CarButton>
        <CarButton variant="secondary" @click="showServices">Services</CarButton>
      </template>
    </CarHeader>

    <main class="main-content">
      <h2>Available Cars</h2>
      <div class="car-grid">
        <CarCard
          v-for="car in cars"
          :key="car.id"
          :title="car.name"
        >
          <p><strong>Price:</strong> {{ car.price }}</p>
          <p><strong>Year:</strong> {{ car.year }}</p>
          <p><strong>Mileage:</strong> {{ car.mileage }}</p>

          <template #footer>
            <CarButton @click="viewDetails(car)">View Details</CarButton>
            <CarButton variant="secondary" @click="testDrive(car)">Testing Drive</CarButton>
          </template>
        </CarCard>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { CarHeader, CarCard, CarButton } from '@workspace/shared'

const cars = ref([
  {
    id: 1,
    name: 'Toyota Camry',
    price: '$25,000',
    year: 2023,
    mileage: '15,000 miles'
  },
  {
    id: 2,
    name: 'Honda Civic',
    price: '$22,000',
    year: 2022,
    mileage: '25,000 miles'
  },
  {
    id: 3,
    name: 'BMW X5',
    price: '$45,000',
    year: 2023,
    mileage: '8,000 miles'
  }
])

const showInventory = () => {
  console.log('Showing inventory')
}

const showServices = () => {
  console.log('Showing services')
}

const viewDetails = (car) => {
  console.log('Viewing details for:', car.name)
}

const testDrive = (car) => {
  console.log('Scheduling test drive for:', car.name)
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
}

.main-content {
  padding: 24px;
}

.car-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 16px;
  margin-top: 16px;
}
</style>