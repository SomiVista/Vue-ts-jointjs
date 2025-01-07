<script setup lang="ts">
import { dia, shapes } from "@joint/core";
import { onMounted } from "vue";

function setupJointJs() {
  const namespace = shapes;

  const graph = new dia.Graph({}, { cellNamespace: namespace });
  const paperWidth = document.body.clientWidth;
  const paperHeight = document.body.clientHeight;

  const paper = new dia.Paper({
    el: document.getElementById("paper"),
    model: graph,
    width: paperWidth,
    height: paperHeight,
    background: { color: "#f5f5f5" },
    cellViewNamespace: namespace,
  });

  const rect1 = new shapes.standard.Rectangle();
  const rect1Width = 180;
  const rect1Height = 50;
  rect1.position(
    (paperWidth - rect1Width) / 2,
    (paperHeight - rect1Height) / 2
  );
  rect1.resize(rect1Width, rect1Height);
  rect1.addTo(graph);
}

onMounted(() => {
  setupJointJs();
});
</script>

<template>
  <div id="paper"></div>
</template>

<style scoped></style>
