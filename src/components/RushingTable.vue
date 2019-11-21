<template>
  <div class="rushing-table">
    <player-table :players="players" />
    <stat-table :players="players" :sortBy="sortBy" />
  </div>
</template>

<script>
import PlayerTable from "@/components/RushingTable/PlayerTable"
import StatTable from "@/components/RushingTable/StatTable"

export default {
  name: "rushing-table",
  props: ["players", "sortBy"],
  components: {
    PlayerTable,
    StatTable
  }
}
</script>

<style lang="scss">
.rushing-table {
  display: flex;
  flex-flow: row;
  width: 100%;
  height: 100%;
  overflow-x: scroll;
  table {
    border-collapse: separate;
    border-spacing: 0;
  }

  td,
  th {
    margin: 0;
    white-space: nowrap;
    border-top-width: 0px;
  }
  td {
    min-width: 5em;
    padding: 0.25em;
  }
  th {
    transform: rotate(-60deg);
    font-weight: bold;
    text-transform: uppercase;
    height: 5em;
    font-size: 1.4em;
    margin: 0;
    padding: 0;
    margin-bottom: -2em;
  }
  table#players {
    width: 10em;
    border-right: 2px solid var(--white);
    th {
      padding-bottom: 1rem;
    }
    td {
      font-weight: bold;
      text-align: left;
    }
  }
  table#rushing {
    .table-headers {
      box-shadow: 0 -2px 0 0 var(--white) inset;
      padding-bottom: 0.25em;
      z-index: 2;
      &:hover {
        background-color: var(--black);
      }
      th.selected {
        color: var(--brand-accent);
      }
      & + tr {
        td {
          padding-top: 1em;
        }
      }
    }
    tr:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }
    td {
      border-right: 2px solid var(--white);
      cursor: default;
      &:hover {
        background-color: rgba(255, 255, 255, 0.25);
      }
    }
  }
  .hidden {
    display: none;
  }
  .table-container {
    width: calc(100% - 10em);
    overflow-x: scroll;
    overflow-y: visible;
    padding: 0;
  }

  .player-column {
    width: 10em;
  }
}
</style>