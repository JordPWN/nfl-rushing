<template>
  <div class="home">
    <page-body>
      <sort-bar
        v-model="playerName"
        @updateSortBy="updateSortBy"
        @exportCSV="exportCSV"
        :reversed="reversed"
      />
      <div class="content-container">
        <rushing-table :players="sortedPlayers" :key="updated" :sortBy='sortBy' />
      </div>
    </page-body>
  </div>
</template>

<script>
import PageBody from "@/components/PageBody"
import RushingTable from "@/components/RushingTable"
import SortBar from "@/components/SortBar"

import rushing from "../../rushing.json"

export default {
  name: "home",
  components: {
    PageBody,
    RushingTable,
    SortBar
  },
  computed: {
    filteredPlayers() {
      return this.players.filter(player => {
        return player.Player.match(new RegExp(this.playerName, "i"))
      })
    },
    sortedPlayers() {
      // eslint-disable-next-line
      const sorted = this.filteredPlayers.sort((a, b) => {
        return (
          parseInt(b[this.sortBy].toString().replace(/[^\d.-]/g, "")) -
          parseInt(a[this.sortBy].toString().replace(/[^\d.-]/g, ""))
        )
      })
      return this.reversed ? sorted.reverse() : sorted
    }
  },
  data() {
    return {
      players: rushing,
      playerName: "",
      sortBy: "Player",
      updated: 0,
      reversed: false
    }
  },
  methods: {
    exportCSV() {
      const headers = [ "Player", "Team", "Pos", "Att", "Att/G", "Yds", "Avg",
      "Yds/G", "TD", "Lng", "1st", "1st%", "20+", "40+", "FUM" ]
      let players = this.sortedPlayers.map(
        player => {
          return Object.keys(player).map((stat, index) => {
            return player[stat]
          })
        }
      )
      players.unshift(headers)
      console.log("players: ", players)
      const csvFile = "data:text/csv;charset=utf-8," + players.map(e => e.join(",")).join("\n")
      const data = encodeURI(csvFile)
      const link = document.createElement("a")
      link.setAttribute("href", data)
      // Set CSV name here
      link.setAttribute("download", "export.csv")
      link.click()
    },
    reverseSort() {
      this.reversed = !this.reversed
    },
    updateSortBy(val) {
      this.updated++
      if (this.sortBy === val) {
        this.reverseSort()
      } else {
        this.reversed = false
        this.sortBy = val
      }
    }
  }
}
</script>

<style lang="scss">
// Media Queries
@media only screen and (orientation: portrait) {
  .home {
    .content-container {
      width: calc(100% - 2em);
      padding: 2.5em 1em;
    }
  }
}
// ---
.content-container {
  display: flex;
  flex-direction: column;
  min-height: calc(100% - 5em);
  width: calc(100% - 5em);
  padding: 2.5em;
  margin-top: 5em;
}
</style>