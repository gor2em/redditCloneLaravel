<script setup>
import { Link } from "@inertiajs/inertia-vue3";

defineProps({
    communities: Object,
});
</script>

<template>
    <div class="w-full border bg-white p-4 rounded-lg">
        <h2 class="font-semibold text-lg p-1 bg-indigo-700 text-white">
            <slot name="title" />
        </h2>
        <ul role="list" class="divide-y divide-slate-300">
            <li
                class="py-3 sm:py-4"
                v-for="community in communities"
                :key="community.id"
            >
                <div class="flex items-center space-x-4">
                    <Link
                        :href="
                            route('frontend.communities.show', community.slug)
                        "
                        class="text-slate-800 font-semibold truncate text-sm"
                    >
                        {{ community.name }}
                    </Link>
                    <div>Posts ({{ community.posts_count }})</div>
                </div>
            </li>
        </ul>
    </div>
</template>
