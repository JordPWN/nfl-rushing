<template>
    <div class="table-container">
      <table id="rushing">
        <tr class="table-headers">
          <th id="rushing-player" title="Player" class="hidden">Player</th>
          <th id="rushing-team" :title="generateTooltip('Team')">Team</th>
          <th id="rushing-pos" :title="generateTooltip('Pos')">Pos</th>
          <th id="rushing-att" :title="generateTooltip('Att')">Att</th>
          <th id="rushing-att-g" :title="generateTooltip('Att/G')">Att/G</th>
          <th id="rushing-yards" :title="generateTooltip('Yds')" :class="{ 'selected': sortBy === 'Yds'}">Yards</th>
          <th id="rushing-avg" :title="generateTooltip('Avg')">Avg</th>
          <th id="rushing-yds-g" :title="generateTooltip('Yds/G')">Yds/G</th>
          <th id="rushing-td" :title="generateTooltip('TD')" :class="{ 'selected': sortBy === 'TD'}">TD</th>
          <th id="rushing-lng" :title="generateTooltip('Lng')" :class="{ 'selected': sortBy === 'Lng'}">Lng</th>
          <th id="rushing-1st" :title="generateTooltip('1st')">1st</th>
          <th id="rushing-1-p" :title="generateTooltip('1st%')">1st%</th>
          <th id="rushing-20" :title="generateTooltip('20+')">20+</th>
          <th id="rushing-40" :title="generateTooltip('40+')">40+</th>
          <th id="rushing-Fumbles" :title="generateTooltip('FUM')">FUM</th>
        </tr>
        <tr v-for="player in players" :key="player.player">
          <td
            v-for="(stat, index) in player"
            :key="index"
            :class="{'hidden': index === 'Player' }"
            :title="generateTooltip(index)"
          >{{ stat }}</td>
        </tr>
      </table>
    </div>
</template>
<script>
export default {
    name: "StatTable",
    props: ["players", "sortBy"],
    methods: {
    generateTooltip(stat) {
      switch (stat) {
        case "Player":
          return "Player"
          break
        case "Team":
          return "Team"
          break
        case "Pos":
          return "Position"
          break
        case "Att":
          return "Rushing Attempts per Game Average"
          break
        case "Att/G":
          return "Rushing Attempts"
          break
        case "Yds":
          return "Total Rushing Yards"
          break
        case "Avg":
          return "Rushing Average Yards Per Attempt"
          break
        case "Yds/G":
          return "Rushing Yards Per Game"
          break
        case "TD":
          return "Total Rushing Touchdowns"
          break
        case "Lng":
          return "Longest Rush"
          break
        case "1st%":
          "Rushing First Down Percentage"
          break
        case "1st":
          return "Rushing First Downs"
          break
        case "20+":
          return "Rushing 20+ Yards Each"
          break
        case "40+":
          return "Rushing 40+ Yards Each"
          break
        case "FUM":
          return "Rushing Fumbles"
          break
      }
    }
  }
}
</script>