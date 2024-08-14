<template>
    <AuthenticatedLayout> Testing! {{ $page.props }} </AuthenticatedLayout>
</template>
<script setup lang="ts">
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
</script>
