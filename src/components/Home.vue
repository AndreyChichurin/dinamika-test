<template>
  <v-container>
    <v-card class="overflow-hidden" color="white" width="1000" align="center">
      <v-card-text>
        <v-autocomplete
          :items="states"
          item-text="city"
          label="Select city"
          @change="choose"
        ></v-autocomplete>
      </v-card-text>
      <v-data-table 
        v-if="model" 
        :headers="headers" 
        :items="model.airports" 
        :items-per-page="5" 
        class="elevation-1"
      ></v-data-table>
    </v-card>
  </v-container>
</template>


<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "Airport name",
          align: "start",
          
          value: "name"
        },
        { text: "IATA", value: "iata" },
        { text: "Passengers", value: "passengers" }
      ],
      model: null,
      states: [
        {
          city: "London",
          airports: [
            {
              name: "London Heathrow Airport",
              iata: "LHR",
              passengers: 80844310
            },
            {
              name: "Gatwick Airport",
              iata: "LGW",
              passengers: 46574786
            },
            {
              name: "London City Airport",
              iata: "LCY",
              passengers: 5100025
            },
            {
              name: "Luton Airport",
              iata: "LTN",
              passengers: '-'
            },
            {
              name: "London Stansted Airport",
              iata: "STN",
              passengers: '-'
            },
            {
              name: "London Southend Airport",
              iata: "SEN",
              passengers: '-'
            }
          ]
        },
        {
          city: "Moscow",
          airports: [
            {
              name: "Moscow Domodedovo Airport",
              iata: "DME",
              passengers: 30700000
            },
            {
              name: "Sheremetyevo International Airport",
              iata: "SVO",
              passengers: 40000000
            },
            {
              name: "Vnukovo International Airport",
              iata: "VKO",
              passengers: 24000100
            },
            {
              name: "Zhukovsky International Airport",
              iata: "ZIA",
              passengers: 1161633
            }
          ]
        }
      ]
    };
  },

  methods: {
    choose(item) {
      this.states.map(elem => (elem.city == item ? (this.model = elem) : elem));
    }
  }
};
</script>
