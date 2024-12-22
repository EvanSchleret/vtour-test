<script lang="ts" setup>
import type { TourStep } from "#nuxt-tour/props"
import type {VTour} from "#components"

const tour = ref<InstanceType<typeof VTour> | null>(null)

const steps: TourStep[] = [
    {
        target: "body",
        body: "This is the first step",
    },
    {
        target: "#welcome",
        body: "This is the second step, placed on the bottom of the target",
        popperConfig: {
            placement: "bottom",
        },
    },
    {
        target: '.step3',
        body: "This is the third step",
    },
]

const rerunTour = () => {
    tour.value?.resetTour()
}

onMounted(() => {
    tour.value?.startTour()
})
</script>

<template>
    <div>
        <NuxtRouteAnnouncer/>

        <h1 id="welcome">Welcome</h1>
        <p class="step3">
            We are delighted to see you again. Log in to your manager to manage your communities.
        </p>

        <button @click="rerunTour">Start the tour</button>

        <VTour ref="tour" :steps="steps" autoStart />
    </div>
</template>
