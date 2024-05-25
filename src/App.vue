<template>
  <div id="app">
    <h1>AMAZON</h1>

    <table>
      <thead>
        <tr>
          <th>Produktname</th>
          <th>Preis</th>
          <th>Verkaufsmenge</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="highlight">Apple AirPods Pro</td>
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
        <!-- Добавьте другие строки таблицы при необходимости -->
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>


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

th, td {
  border: 5px solid #00ADB5;
  text-align: left;
  padding: 8px;
}

th {
  background-color: #FB8500;
}

tr {
  background-color: #EEEEEE ;
}

.highlight {
  color: #037490; /* Цвет текста для ячеек с классом "highlight" */
}


</style>


