<template>
  <div class="slidev-layout section">
    <div class="section__inner">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.section {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  text-align: center;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
}

.section__inner {
  width: min(900px, 100%);
}

.section__inner :deep(h1) {
  font-size: 3em;
  font-weight: 700;
  margin-bottom: 0.5em;
  background: linear-gradient(90deg, #4fc3f7, #81c784);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.section__inner :deep(p) {
  color: #9ca3af;
  font-size: 1.3em;
}
</style>
