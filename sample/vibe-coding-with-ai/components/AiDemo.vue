<template>
  <div class="ai-demo-container">
    <div class="chat-interface">
      <div class="message user-message">
        <div class="avatar">👤</div>
        <div class="content">{{ userMessage }}</div>
      </div>
      <div class="message ai-message" v-if="showAiResponse">
        <div class="avatar">🤖</div>
        <div class="content">{{ aiMessage }}</div>
      </div>
      <div class="code-output" v-if="showCode">
        <pre><code>{{ generatedCode }}</code></pre>
      </div>
    </div>
    <button @click="nextStep" class="demo-button" v-if="canProceed">
      {{ buttonText }}
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const props = defineProps<{
  userMessage: string
  aiMessage: string
  generatedCode: string
}>()

const step = ref(0)

const showAiResponse = computed(() => step.value >= 1)
const showCode = computed(() => step.value >= 2)
const canProceed = computed(() => step.value < 2)

const buttonText = computed(() => {
  switch (step.value) {
    case 0: return 'AI応答を表示'
    case 1: return 'コードを生成'
    default: return ''
  }
})

const nextStep = () => {
  if (step.value < 2) {
    step.value++
  }
}
</script>

<style scoped>
.ai-demo-container {
  background: #1a1a1a;
  border-radius: 8px;
  padding: 1rem;
  color: white;
  font-family: 'JetBrains Mono', monospace;
}

.chat-interface {
  margin-bottom: 1rem;
}

.message {
  display: flex;
  margin-bottom: 1rem;
  align-items: flex-start;
}

.avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: #333;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 0.5rem;
  font-size: 1rem;
}

.content {
  background: #2d2d2d;
  padding: 0.5rem 1rem;
  border-radius: 1rem;
  max-width: 80%;
}

.user-message .content {
  background: #0084ff;
}

.ai-message .content {
  background: #00d9ff;
  color: black;
}

.code-output {
  background: #0d1117;
  border: 1px solid #30363d;
  border-radius: 6px;
  padding: 1rem;
  margin-top: 1rem;
}

.code-output pre {
  margin: 0;
  color: #e6edf3;
}

.demo-button {
  background: #238636;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
}

.demo-button:hover {
  background: #2ea043;
}
</style>
