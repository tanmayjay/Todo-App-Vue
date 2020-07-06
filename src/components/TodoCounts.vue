<template>
  <div class="count-box">
    |<p id="count-type">Incomplete: <span id="counts">{{ counts.incomplete }}</span></p>|
    <p id="count-type">Total: <span id="counts">{{ counts.total }}</span></p>|
    <p id="count-type">Complete: <span id="counts">{{ counts.complete }}</span></p>|
  </div>
</template>

<script>
export default {
  name: "TodoCounts",
  props: ["counts"],
}
</script>

<style>
  .count-box {
    background: lightgreen;
    color: #333;
    text-align: center;
    padding: 2px;
    display: flex;
    justify-content: space-between;
  }

  #counts {
    color: black;
    font-weight: bold;
  }

  #count-type {
    color: grey;
    margin: 0 10px 0 10px;
  }
</style>