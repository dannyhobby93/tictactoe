<template>
    <AuthenticatedLayout>
        <menu class="grid grid-cols-3 gap-1.5 w-0 min-w-fit mx-auto mt-12">
            <li
                v-for="(square, index) in boardState"
                class="size-32 grid place-items-center bg-gray-300 text-4xl font-bold"
            >
                <button
                    @click="fillSquare(index)"
                    v-if="square === 0"
                    class="place-self-stretch bg-gray-200 hover:bg-gray-300 transition-colors"
                ></button>
                <span v-else v-text="square === -1 ? 'X' : 'O'"></span>
            </li>
        </menu>
    </AuthenticatedLayout>
</template>
<script setup lang="ts">
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { computed, ref } from "vue";

const boardState = ref([0, 0, 0, 0, 0, 0, 0, 0, 0]);

const xTurn = computed(
    () => boardState.value.reduce((carry, value) => carry + value, 0) === 0
);

const fillSquare = (index) => {
    boardState.value[index] = xTurn.value ? -1 : 1;
};
</script>
