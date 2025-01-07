<script setup lang="ts">
import { dia, shapes } from "@joint/core";
import { onMounted } from "vue";

function setupJointJs() {
  const namespace = shapes;

  const graph = new dia.Graph({}, { cellNamespace: namespace });

  const paper = new dia.Paper({
    el: document.getElementById("paper"),
    model: graph,
    width: document.body.clientWidth,
    height: document.body.clientHeight,
    background: { color: "red" },
    cellViewNamespace: namespace,
  });
}

onMounted(() => {
  setupJointJs();
});
</script>

<template>
  <div id="paper"></div>
</template>

<style scoped></style>
