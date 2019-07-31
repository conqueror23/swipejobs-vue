<template>
  <div id="HeadLine">
    <div>
      <h4>Jobs Available</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeadLines",
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
  margin-left: 10%;
}
#HeadLine h4 {
  color: whitesmoke;
  font-weight: 600;
}
</style>
