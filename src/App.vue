<template>
  <!-- Aufgabe 1 -->
  <!-- <div style="display:flex">
    <Sheet bg-color="#3498db" color="white" width="250" height="300">
      <h3>Memo to myself</h3>
      <p>Always prepare for PLFs in time!</p>
      <img src="info.svg" width="80px" />
    </Sheet>
    <Sheet bg-color="#8e44ad" color="yellow" width="400" height="300">
      <p>INSY, SEW and Webtechnologies are our favorite subjects!</p>
      <span style="font-style: italic">Starkschwitz Fiedler, Jan Schreck</span>
      <p>Wish is was there!</p>
      <span style="font-style: italic">E. Wahn</span>
    </Sheet>
  </div> -->

  <!-- Aufgabe 2 -->
  <!-- <div id="app">
    <AppLayout>
      <template v-slot:footer>
        By Robert Baumgartner
      </template>
      <template v-slot:header>
        I was made with Vue slots!
      </template>
      <template v-slot:default>
        <AppButton><img src="home.svg" /> Home</AppButton>
      </template>
    </AppLayout>
  </div> -->

  <!-- Aufgabe 2: Nein die Reihenfolge spielt keine Rolle da v-slot angibt wo der slot stehen soll
    z.b: Footer kann auch an erster Stelle stehen und trotzdem ist der Content ganz unten.
   -->

<!-- Aufgabe 3: -->
  <div id="app">
    <DataTable :items="desserts" :headers="headers">
      <template v-slot:header>
        <h2>Watch What You Eat!</h2>
      </template>
      <template v-slot:footer> Created 2021 by Robert Baumgartner </template>
      <template v-slot:bodyInhalt>
        <tr class="last-row">
          <td>Total</td>
          <td>{{ totalCalories }}</td>
          <td>{{ totalFat }}</td>
          <td>{{ totalCarbs }}</td>
          <td>{{ totalProtein }}</td>
          <td></td>
        </tr>
      </template>
    </DataTable>
  </div>
</template>

<script>
// import Sheet from './components/Sheet.vue';
// import AppLayout from '@/components/AppLayout.vue';
// import AppButton from '@/components/AppButton.vue';
import DataTable from '@/components/DataTable.vue';

export default {
  name: 'App',

  components: {
    // Sheet,
    // AppLayout,
    // AppButton,
    DataTable,
  },

  data() {
    return {
      headers: [
        {
          text: 'Dessert (100g serving)',
          value: 'name',
        },
        { text: 'Calories', value: 'calories' },
        { text: 'Fat (g)', value: 'fat' },
        { text: 'Carbs (g)', value: 'carbs' },
        { text: 'Protein (g)', value: 'protein' },
        { text: 'Iron (%)', value: 'iron' },
      ],
      desserts: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%',
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%',
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%',
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%',
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%',
        },
        {
          name: 'Döner',
          calories: 184,
          fat: 4.0,
          carbs: 25,
          protein: 12,
          iron: '1%',
        },
      ],
    };
  },
  computed: {
    totalCalories() {
      return this.desserts.map((el) => el.calories).reduce((previous, current) => previous + current);
    },
    totalFat() {
      return this.desserts.map((el) => el.fat).reduce((previous, current) => previous + current);
    },
    totalCarbs() {
      return this.desserts.map((el) => el.carbs).reduce((previous, current) => previous + current);
    },
    totalProtein() {
      return this.desserts.map((el) => el.protein).reduce((previous, current) => previous + current);
    },
  },
};
</script>
<style scoped>
#app {
  text-align: center;
}
.last-row {
  font-weight: bold;
}
</style>
