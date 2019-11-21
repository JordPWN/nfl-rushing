<template>
  <table id="players">
    <tr>
      <th id="rushing-player" title="Player">Player</th>
    </tr>
    <tr v-for="player in players" :key="player.player">
      <td class="player-name">{{ player.Player }}</td>
    </tr>
  </table>
</template>
<script>
export default {
    name: "PlayerTable",
    props: ["players"]
}
</script>