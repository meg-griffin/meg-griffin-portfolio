<template>
  <div class="cards">
    <!-- card filters -->
    <div class="card-filters">
      <label class="sr-only">Filter:</label>
      <span class="filter" :class="{ active: currentFilter === 'All' }" @click="setFilter('All')">All</span>
      <span class="filter" :class="{ active: currentFilter === 'Education' }"
        @click="setFilter('Education')">Education</span>
      <span class="filter" :class="{ active: currentFilter === 'Corporate' }"
        @click="setFilter('Corporate')">Corporate</span>
      <span class="filter" :class="{ active: currentFilter === 'Lifestyle' }"
        @click="setFilter('Lifestyle')">Lifestyle</span>

      <span class="filter-dropdown">
        <label for="select" class="sr-only">Sort By:</label>
        <select name="sortBy" id="select" v-model="sortBy">
          <option value="mostRecent">Most Recent</option>
          <option value="alphabetical">Alphabetical</option>
        </select>
      </span>
    </div>

    <div class="cards-grid">
      <div :key="card.id" v-for="card in filteredCards" class="card-cat all" :class="card.filter.toLowerCase()">
        <!-- flip card component -->
        <FlipCard :fullOne="card.fullOne" :fullTwo="card.fullTwo" :fullThree="card.fullThree">
          <!-- flip card slot front -->
          <template v-slot:front="front">
            <!-- project images side -->
            <div class="project-category">
              {{ card.filter }}
            </div>
            <div class="project-images" @click="front.zoom">
              <div class="project-showcase">
                <img class="showcase-one" :src="card.thumbOne" :alt="card.clientName" />
                <img class="showcase-two" :src="card.thumbTwo" :alt="card.clientName" />
                <img class="showcase-three" :src="card.thumbThree" :alt="card.clientName" />
              </div>
              <img class="project-logo" :src="card.logo" :alt="card.clientName" />
              <div class="project-logo-gradient"></div>
            </div>
          </template>

          <!-- flip card slot back -->
          <template v-slot:back>
            <!-- project details side -->
            <div class="project-details">
              <img class="project-logo" :src="card.logo" :alt="card.clientName" />
              <div class="project-details-text">
                <div class="details-header">
                  <div class="project-avatar">
                    <img :src="card.logo" :alt="card.clientName" />
                  </div>

                  <span>
                    <div class="client-name">{{ card.clientName }}</div>

                    <div v-if="card.launched === true" class="project-year">
                      Launched: {{ card.year }}
                    </div>
                    <div v-else class="project-year">In Development</div>
                  </span>
                </div>

                <div class="project-name">{{ card.projectName }}</div>

                <div class="project-description">
                  <span class="highlight-text">{{ card.description }}</span>
                </div>

              </div>
            </div>
            <!-- <div class="project-logo-gradient"></div> -->
          </template>
        </FlipCard>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import FlipCard from "./FlipCard.vue";

export default {
  name: "Cards",
  components: {
    FlipCard,
  },

  data: function () {
    return {
      sortBy: "mostRecent",
      cards: [],
      currentFilter: "All",
    };
  },

  methods: {
    // set project card filter
    setFilter: function (filter) {
      this.currentFilter = filter;

      let cardCat = document.getElementsByClassName("card-cat");
      let filterClass = this.currentFilter.toLowerCase();

      for (var i = 0; i < cardCat.length; i++) {
        if (!cardCat[i].classList.contains(filterClass)) {
          cardCat[i].classList.add("filtered");
        } else {
          cardCat[i].classList.remove("filtered");
        }
      }
    },
  },
  computed: {
    filteredCards() {
      let sortCards = this.cards;

      // sort by alphabetical order
      sortCards = sortCards.sort((a, b) => {
        if (this.sortBy == "alphabetical") {
          let sort_a = a.clientName.toLowerCase(),
            sort_b = b.clientName.toLowerCase();

          if (sort_a < sort_b) {
            return -1;
          }
          if (sort_a > sort_b) {
            return 1;
          }
          return 0;

          // sort by most recent
        } else if (this.sortBy == "mostRecent") {
          return b.year - a.year;
        }
      });

      return sortCards;
    },
  },
  created() {
    axios
      .get("portfolio.json")
      .then((response) => {
        this.cards = response.data.portfolio;
      })
      .catch((error) => {
        this.errors.push(error);
      });
  },
};
</script>
