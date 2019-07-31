<template>
  <div id="HeadLine">
    <div>
      <p>Jobs Available</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeadLines"
};
</script>

<style>
#HeadLine {
  display: flex;
  background: #74b9ff;
  padding: 0.5em 0.4em;
}
#HeadLine > div {
  display: flex;
  background: #0984e3;
  padding: 0.2em 0.8em;
}
#HeadLine p {
  color: whitesmoke;
  font-weight: 600;
}
</style>
