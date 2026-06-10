<script setup lang="ts">
import { computed, onMounted, onUnmounted, ref } from 'vue'

const props = withDefaults(
  defineProps<{
    /** Initial countdown duration, in minutes. */
    minutes?: number
    /** If true (default), the timer starts automatically when the slide opens. */
    autoStart?: boolean
    /** If true, shows pause/reset controls. */
    controls?: boolean
  }>(),
  {
    minutes: 18,
    autoStart: true,
    controls: true,
  },
)

const totalSeconds = computed(() => Math.max(1, Math.floor(props.minutes * 60)))
const remaining = ref(totalSeconds.value)
const status = ref<'stopped' | 'running' | 'paused'>('stopped')
const overtime = ref(false)
let intervalId: ReturnType<typeof setInterval> | null = null

const mmss = computed(() => {
  const sign = overtime.value ? '-' : ''
  const abs = Math.abs(remaining.value)
  const m = Math.floor(abs / 60).toString().padStart(2, '0')
  const s = Math.floor(abs % 60).toString().padStart(2, '0')
  return { sign, m, s }
})

const percentage = computed(() => {
  // 0% at start, 100% at the end, can exceed 100% in overtime
  return ((totalSeconds.value - remaining.value) / totalSeconds.value) * 100
})

const colorClass = computed(() => {
  if (status.value !== 'running' && !overtime.value) return 'text-blue-500 dark:text-blue-300'
  if (overtime.value || percentage.value >= 100) return 'text-red-500 dark:text-red-300'
  if (percentage.value >= 80) return 'text-yellow-500 dark:text-yellow-300'
  return 'text-green-500 dark:text-green-300'
})

const barColor = computed(() => {
  if (overtime.value || percentage.value >= 100) return 'bg-red-500'
  if (percentage.value >= 80) return 'bg-yellow-500'
  return 'bg-green-500'
})

function tick() {
  if (status.value !== 'running') return
  remaining.value -= 1
  if (remaining.value <= -totalSeconds.value) {
    // Safety: auto-stop at -totalSeconds to avoid runaway in overtime
    pause()
    return
  }
  if (remaining.value < 0 && !overtime.value) {
    overtime.value = true
    // Subtle notification: flash the title once
  }
}

function start() {
  if (status.value === 'running') return
  status.value = 'running'
  if (intervalId) clearInterval(intervalId)
  intervalId = setInterval(tick, 1000)
}

function pause() {
  if (status.value !== 'running') return
  status.value = 'paused'
  if (intervalId) {
    clearInterval(intervalId)
    intervalId = null
  }
}

function reset() {
  if (intervalId) {
    clearInterval(intervalId)
    intervalId = null
  }
  status.value = 'stopped'
  remaining.value = totalSeconds.value
  overtime.value = false
}

function toggle() {
  if (status.value === 'running') pause()
  else start()
}

function addMinute() {
  // Useful for "give them 5 more minutes"
  remaining.value += 60
  totalSeconds.value !== totalSeconds.value // no-op for reactivity
  overtime.value = false
  if (status.value === 'stopped') start()
}

defineExpose({ start, pause, reset, addMinute })

onMounted(() => {
  if (props.autoStart) start()
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})
</script>

<template>
  <div class="planning-timer flex flex-col items-center gap-6 select-none">
    <!-- Time display -->
    <div
      class="font-mono font-bold tabular-nums leading-none tracking-tight"
      :class="[colorClass, 'text-[10rem]']"
    >
      <span class="opacity-50">{{ mmss.sign }}</span><span>{{ mmss.m }}</span><span class="opacity-50">:</span><span>{{ mmss.s }}</span>
    </div>

    <!-- Progress bar -->
    <div class="w-[28rem] max-w-full h-2 bg-gray-200/60 dark:bg-gray-700/40 rounded-full overflow-hidden">
      <div
        class="h-full transition-all duration-1000 ease-linear"
        :class="barColor"
        :style="{ width: `${Math.min(Math.max(percentage, 0), 100)}%` }"
      />
    </div>

    <!-- Status text -->
    <div class="text-sm opacity-60">
      <span v-if="status === 'stopped'">Ready · {{ minutes }} min</span>
      <span v-else-if="status === 'paused'">Paused</span>
      <span v-else-if="overtime">⏰ Time's up — wrap up your plan</span>
      <span v-else>Running</span>
    </div>

    <!-- Controls (optional) -->
    <div v-if="controls" class="flex items-center gap-2 text-sm">
      <button
        type="button"
        class="px-4 py-2 rounded-lg border border-gray-300/60 dark:border-gray-600/60 hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors"
        @click="toggle"
      >
        <span v-if="status === 'running'">⏸ Pause</span>
        <span v-else>▶ {{ status === 'paused' ? 'Resume' : 'Start' }}</span>
      </button>
      <button
        type="button"
        class="px-3 py-2 rounded-lg border border-gray-300/60 dark:border-gray-600/60 hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors"
        @click="reset"
      >
        ↻ Reset
      </button>
      <button
        type="button"
        class="px-3 py-2 rounded-lg border border-gray-300/60 dark:border-gray-600/60 hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors"
        @click="addMinute"
        title="Add 1 minute"
      >
        +1 min
      </button>
    </div>
  </div>
</template>

<style scoped>
.planning-timer button {
  cursor: pointer;
}
</style>
