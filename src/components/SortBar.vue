<template>
  <div class="sort-bar">
    <div class="sort-bar-container">
      <div class="sort-option">
        <input placeholder="Filter..." @input="updateName" ref="playerName" />
      </div>
      <div class="sort-option selectors">
        <div class="sort-by">Sort By:</div>
        <div
          @click="updateSortBy('Yds')"
          class="sort-selector yds"
          :class="{'selected': sortBy === 'Yds'}"
        >
          Total Rushing Yards
          <span class="sort-icon" :class="{'reverse': reversed}">▾</span>
        </div>
        <div
          @click="updateSortBy('Lng')"
          class="sort-selector lng"
          :class="{'selected': sortBy === 'Lng'}"
        >
          Longest Rush
          <span class="sort-icon" :class="{'reverse': reversed}">▾</span>
        </div>
        <div
          @click="updateSortBy('TD')"
          class="sort-selector td"
          :class="{'selected': sortBy === 'TD'}"
        >
          Total Rushing Touchdowns
          <span class="sort-icon" :class="{'reverse': reversed}">▾</span>
        </div>
      </div>
      <div class="sort-option">
        <s-button @click="exportCSV" class="download-button">Download</s-button>
      </div>
    </div>
  </div>
</template>

<script>
import SButton from "@/components/SButton"

export default {
  name: "sort-bar",
  components: {
    SButton
  },
  props: ["reversed"],
  data() {
    return {
      sortBy: "Player"
    }
  },
  methods: {
    exportCSV() {
      this.$emit("exportCSV")
    },
    updateName() {
      this.$emit("input", this.$refs.playerName.value)
    },
    updateSortBy(val) {
      this.sortBy = val
      this.$emit("updateSortBy", val)
    }
  }
}
</script>

<style lang="scss">
// Media Queries
@media only screen and (orientation: portrait) {
  .home {
    .sort-bar {
      height: 5em;
      width: 100vw;
      background-color: var(--nav-accent);
    }
    .sort-bar-container {
      width: calc(100% - 0.6em);
      margin: 0 0.3em;
      .sort-by {
        display: none;
        padding: 0;
      }
      .sort-option {
        flex-direction: column;
        max-width: (100vw / 3);
        width: auto;
        font-size: 0.8em;
        input {
          min-width: 7em;
        }
        .sort-selector {
          height: 1.5em;
          max-width: fit-content;
          white-space: nowrap;
        }
        .download-button {
          display: flex;
          justify-content: center;
          align-items: center;
          height: 4em;
        }
      }
    }
  }
}
// ---
.sort-option {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  font-weight: bold;
  .sort-by {
    padding-right: 1em;
  }
}
.sort-bar,
.sort-bar-container {
  position: fixed;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100vw;
  background-color: var(--nav-accent);
  height: 5em;
  z-index: 5;
}
.sort-bar-container {
  width: calc(100vw - 5em);
  margin: 0 2.5em;
}
.sort-selector {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 8em;
  height: 4em;
  padding: 0 1em;
  border-radius: 0.3em;
  cursor: pointer;
  .sort-icon {
    padding-left: 1em;
    color: var(--nav-accent);
    &.reverse {
      transform: rotate(180deg);
      padding-left: 0em;
      padding-right: 1em;
    }
  }
  &.selected {
    background-color: var(--black);
    .sort-icon {
      color: var(--white);
    }
  }
}
</style>