<template lang="html">
  <div>
    <table>
      <thead>
        <th>WebSite</th>
        <th>Avatar</th>
        <th>Acceptability</th>
      </thead>
      <tr>
        <td>{{github.url}}</td>
        <td><img :src="github.avatar" alt=""></td>
        <td>{{github.state}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ['github']
}
</script>

<style lang="css">
table tr td {
		width: 300px;
		border: 1px solid #ccc;
}

table {
		padding-top: 2%;
		margin: 0 auto;
}
</style>
