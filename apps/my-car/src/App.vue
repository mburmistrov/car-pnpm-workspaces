<template>
  <div id="app">
    <CarHeader app-name="My Car Dashboard">
      <template #nav>
        <CarButton @click="showMaintenance">Maintenance</CarButton>
        <CarButton variant="secondary" @click="showTrips">Trips</CarButton>
        <CarButton variant="danger" @click="emergencyContact">Emergency</CarButton>
      </template>
    </CarHeader>

    <main class="main-content">
      <h2>My Vehicle Info</h2>

      <CarCard title="Current Vehicle">
        <div class="vehicle-info">
          <p><strong>Make & Model:</strong> {{ mycar.make }} {{ mycar.model }}</p>
          <p><strong>Year:</strong> {{ mycar.year }}</p>
          <p><strong>VIN:</strong> {{ mycar.vin }}</p>
          <p><strong>Mileage:</strong> {{ mycar.mileage }}</p>
          <p><strong>Last Service:</strong> {{ mycar.lastService }}</p>
        </div>

        <template #footer>
          <CarButton @click="updateMileage">Update Mileage</CarButton>
          <CarButton variant="secondary" @click="scheduleService">Schedule Service</CarButton>
        </template>
      </CarCard>

      <div class="dashboard-grid">
        <CarCard title="Fuel Efficiency">
          <p>Average: {{ mycar.fuelEfficiency }} MPG</p>
          <p>Last Fill-up: {{ mycar.lastFillup }}</p>

          <template #footer>
            <CarButton @click="addFuelRecord">Add Fuel Record</CarButton>
          </template>
        </CarCard>

        <CarCard title="Maintenance Reminders">
          <ul class="reminder-list">
            <li v-for="reminder in maintenanceReminders" :key="reminder.id">
              {{ reminder.task }} - {{ reminder.dueDate }}
            </li>
          </ul>

          <template #footer>
            <CarButton @click="viewAllReminders">View All</CarButton>
          </template>
        </CarCard>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { CarHeader, CarCard, CarButton } from '@workspace/shared'

const mycar = ref({
  make: 'Honda',
  model: 'Accord',
  year: 2021,
  vin: '1HGCV1F30LA123456',
  mileage: '45,230 miles',
  lastService: 'March 15, 2024',
  fuelEfficiency: '32.5',
  lastFillup: 'April 2, 2024'
})

const maintenanceReminders = ref([
  { id: 1, task: 'Oil Change', dueDate: 'May 15, 2024' },
  { id: 2, task: 'Tire Rotation', dueDate: 'June 1, 2024' },
  { id: 3, task: 'Brake Inspection', dueDate: 'July 10, 2024' }
])

const showMaintenance = () => {
  console.log('Showing maintenance records')
}

const showTrips = () => {
  console.log('Showing trip history')
}

const emergencyContact = () => {
  console.log('Emergency contact activated')
}

const updateMileage = () => {
  console.log('Updating mileage')
}

const scheduleService = () => {
  console.log('Scheduling service appointment')
}

const addFuelRecord = () => {
  console.log('Adding fuel record')
}

const viewAllReminders = () => {
  console.log('Viewing all maintenance reminders')
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
}

.main-content {
  padding: 24px;
}

.vehicle-info {
  line-height: 1.6;
}

.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 16px;
  margin-top: 24px;
}

.reminder-list {
  margin: 0;
  padding-left: 20px;
}

.reminder-list li {
  margin-bottom: 8px;
}
</style>