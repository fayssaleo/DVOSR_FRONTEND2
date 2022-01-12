<template>
  <v-app>
    <v-card>
      <v-tabs
        v-model="tab"
        background-color="#3949AB"
        centered
        dark
        icons-and-text
      >
        <v-switch
          v-model="showAfter"
          inset
          :label="showAfter ? 'AFTER' : 'BEFORE'"
          :class="showAfter ? 'afterButton' : 'beforeButton'"
          style="
            float: left;
            margin-left: 11px;
            margin-right: auto;
            min-width: 132px;
          "
        ></v-switch>
        <v-tabs-slider></v-tabs-slider>

        <v-tab href="#arrival">
          Arrival
          <v-icon>mdi-location-enter</v-icon>
        </v-tab>

        <v-tab href="#departure">
          Departure
          <v-icon>mdi-location-exit</v-icon>
        </v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item :key="'arrival'" :value="'arrival'">
          <v-card>
            <v-tabs
              v-model="tab2"
              background-color="#ECEFF1"
              centered
              dark
              icons-and-text
              class="arrivaleTabs"
            >
              <v-tabs-slider></v-tabs-slider>

              <v-tab href="#voyage" class="black--text">
                Voyage infos
                <v-icon color="black">mdi-ferry</v-icon>
              </v-tab>

              <v-tab href="#crane" class="black--text">
                Crane info
                <v-icon color="black">mdi-boom-gate-arrow-down-outline</v-icon>
              </v-tab>
              <v-tab href="#delays" class="black--text">
                Delays info
                <v-icon color="black">mdi-timetable</v-icon>
              </v-tab>
            </v-tabs>

            <v-tabs-items v-model="tab2">
              <v-tab-item :key="'voyage1'" :value="'voyage'">
                <v-card flat>
                  <ArrivalVoyageActions
                    :ShowNewVoyage="ShowNewVoyage"
                    :ShowOldVoyage="ShowOldVoyage"
                    :showAfter="showAfter"
                  />
                </v-card>
              </v-tab-item>
              <v-tab-item :key="'crane1'" :value="'crane'">
                <v-card flat>
                  <ArrivalCraneAction
                    :ShowNewVoyage="ShowNewVoyage"
                    :ShowOldVoyage="ShowOldVoyage"
                    :showAfter="showAfter"
                  />
                </v-card>
              </v-tab-item>
              <v-tab-item :key="'delays1'" :value="'delays'">
                <v-card flat>
                  <v-card-text>delays</v-card-text>
                </v-card>
              </v-tab-item>
            </v-tabs-items>
          </v-card>
        </v-tab-item>
        <v-tab-item :key="'departure'" :value="'departure'">
          <v-card>
            <v-tabs
              v-model="tab3"
              background-color="#546E7A"
              centered
              dark
              icons-and-text
              class="departureTabs"
            >
              <v-tabs-slider></v-tabs-slider>

              <v-tab href="#voyage">
                Voyage infos
                <v-icon>mdi-ferry</v-icon>
              </v-tab>

              <v-tab href="#crane">
                Crane info
                <v-icon>mdi-boom-gate-arrow-up-outline</v-icon>
              </v-tab>
              <v-tab href="#delays">
                Delays info
                <v-icon>mdi-timetable</v-icon>
              </v-tab>
            </v-tabs>

            <v-tabs-items v-model="tab3">
              <v-tab-item :key="'voyage2'" :value="'voyage'">
                <v-card flat>
                  <v-card-text>Voyage</v-card-text>
                </v-card>
              </v-tab-item>
              <v-tab-item :key="'crane2'" :value="'crane'">
                <v-card flat>
                  <v-card-text>crane</v-card-text>
                </v-card>
              </v-tab-item>
              <v-tab-item :key="'delays2'" :value="'delays'">
                <v-card flat>
                  <v-card-text>delays</v-card-text>
                </v-card>
              </v-tab-item>
            </v-tabs-items>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-card>
  </v-app>
</template>

<script>
import ArrivalVoyageActions from "./ArrivalVoyageActions";
import ArrivalCraneAction from "./ArrivalCraneAction";
export default {
  components: { ArrivalVoyageActions, ArrivalCraneAction },
  props: ["ShowNewVoyage", "ShowOldVoyage"],
  data() {
    return {
      tab: null,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      tab2: null,
      tab3: null,
      voyage: {},
      showAfter: true,
    };
  },
  methods: {},
  mounted() {},
};
</script>
