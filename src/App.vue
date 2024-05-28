<script setup>
import Column from 'primevue/column';
import DataTable from 'primevue/datatable';
import { computed, ref } from 'vue';
import axios from 'axios';

console.log(axios.isCancel('something'));

const posts = ref()

function getPosts() {
  axios.get('https://jsonplaceholder.typicode.com/posts/')
    .then(function (response) {
      // handle success
      console.log(response.data);

      // Set posts variable
      posts.value = response.data
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .finally(function () {
      // always executed
    });
}

function clearPosts() {
  posts.value = undefined
}



const products = [
  {
    code: "1",
    name: "Apple AirPods Basic",
    preis: 249.00,
    quantity: "10,000"
  },
  {
    code: "2",
    name: "Instant Pot Duo 7-in-1",
    preis: 79.95,
    quantity: "15,000"
  },
  {
    code: "3",
    name: "Kindle Paperwhite",
    preis: 80.56,
    quantity: "7,000"
  },
  {
    code: "4",
    name: "Nintendo Switch",
    preis: 43.76,
    quantity: "5,000"
  },
  {
    code: "5",
    name: "Echo Dot (3rd Gen)",
    preis: 65.97,
    quantity: "2,000"
  },
  {
    code: "6",
    name: "Fire TV Stick 4K",
    preis: 99.99,
    quantity: "6,500"
  },
  {
    code: "7",
    name: "Fitbit Charge 4",
    preis: 23.87,
    quantity: "5,000"
  },
  {
    code: "8",
    name: "LEGO Star Wars Set",
    preis: 122.76,
    quantity: "3,000"
  },
  {
    code: "9",
    name: "Sony WH-1000XM4",
    preis: 976.55,
    quantity: "11,000"
  },
  {
    code: "10",
    name: "Instant Pot Ultra",
    preis: 76.88,
    quantity: "9,000"
  },
]

const selectedItem = ref()

function selectItem(event) {
  selectedItem.value = event.data
}

const isExpensive = computed(() => {

  if (selectedItem.value == null) {
    return 'Kein Produkt gewählt.'
  }

  if (selectedItem.value.preis >= 100) {
    return true;
  }

  return false;
})

// const selectedItem2 = ref()

// function selectItem2(event) {
//   selectedItem2.value = event.data
// }

const isAlot = computed(() => {

  if (selectedItem.value == null) {
    return 'Kein Produkt gewählt.'
  }

  if (selectedItem.value.quantity >= 5000) {
    return true;
  }

  return false;
})





</script>


<template>
  <div id="app">
    <h1>AMAZON</h1>

    {{ selectedItem }}<br>
    {{ isExpensive }}<br>

    <!-- {{ selectedItem2 }}<br> -->
    {{ isAlot }}<br>

    <button @click="getPosts()">Posts abrufen</button>

    <button @click="clearPosts()">Posts löschen</button>

    <!-- @TODO Replace div with DataTable -->
    <div v-for="post in posts" :key="post.id">
      <h1>{{ post.title }}</h1>
    </div>

    <div v-if="selectedItem">
      <span v-if="isExpensive" style="color: #f00;">Teuer! ({{ selectedItem?.preis }})</span>
      <span v-else style="color: #0f0;">Günstig! ({{ selectedItem?.preis }})</span>
    </div>

    <div v-if="selectedItem">
      <span v-if="isAlot" style="color: #f00;">Genug! ({{ selectedItem?.quantity }})</span>
      <span v-else style="color: #0f0;">Nicht Genug! ({{ selectedItem?.quantity }})</span>
    </div>





    <DataTable :value="products" tableStyle="min-width: 50rem" @rowDblclick="(event) => selectItem(event)">
      <Column field="code" header="Code"></Column>
      <Column field="name" header="Name"></Column>
      <Column field="preis" header="Preis">
        <template #body="{ data }">
          ${{ data.preis }}
        </template>
      </Column>
      <Column field="quantity" header="Quantity">
        <template #body="{ data }">
          {{ data.quantity }}
        </template>
      </Column>
    </DataTable>

    <!-- <table>
      <thead>
        <tr>
          <th>Produktname</th>
          <th>Preis</th>
          <th>Verkaufsmenge</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="highlight">Apple AirPods Basic</td>
          <td class="highlight">$249.00</td>
          <td class="highlight">10,000</td>
        </tr>
        <tr>
          <td class="highlight">Instant Pot Duo 7-in-1</td>
          <td class="highlight">$79.95</td>
          <td class="highlight">15,000</td>
        </tr>
        <tr>
          <td class="highlight">Kindle Paperwhite</td>
          <td class="highlight">$129.99</td>
          <td class="highlight">8,000</td>
        </tr>
        <tr>
          <td class="highlight">Nintendo Switch</td>
          <td class="highlight">$299.00</td>
          <td class="highlight">20,000</td>
        </tr>
        <tr>
          <td class="highlight">Echo Dot (3rd Gen)</td>
          <td class="highlight">$49.99</td>
          <td class="highlight">30,000</td>
        </tr>
        <tr>
          <td class="highlight">Fire TV Stick 4K</td>
          <td class="highlight">$49.99</td>
          <td class="highlight">25,000</td>
        </tr>
        <tr>
          <td class="highlight">Fitbit Charge 4</td>
          <td class="highlight">$129.95</td>
          <td class="highlight">12,000</td>
        </tr>
        <tr>
          <td class="highlight">LEGO Star Wars Set</td>
          <td class="highlight">$59.99</td>
          <td class="highlight">18,000</td>
        </tr>
        <tr>
          <td class="highlight">Sony WH-1000XM4</td>
          <td class="highlight">$348.00</td>
          <td class="highlight">7,000</td>
        </tr>
        <tr>
          <td class="highlight">Instant Pot Ultra</td>
          <td class="highlight">$149.95</td>
          <td class="highlight">10,000</td>
        </tr>
       
      </tbody>
    </table> -->

    <!-- Добавьте другие строки таблицы при необходимости -->
  </div>
</template>




<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #393E46;
  margin-top: 10px;
}

table {
  width: 100%;
  border-collapse: separate;

}

th,
td {
  border: 5px solid #00ADB5;
  text-align: left;
  padding: 8px;
}

th {
  background-color: #FB8500;
}

tr {
  background-color: #EEEEEE;
}

.highlight {
  color: #037490;
  /* Цвет текста для ячеек с классом "highlight" */
}
</style>
