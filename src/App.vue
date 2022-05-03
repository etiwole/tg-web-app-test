<template>
    <main :class="colorSchema">
        <task v-for="task in tasks" :key="task.id" :init-data="task" :remove-callback="removeTask"/>

        <c-button :callback="newTask">Новая задача</c-button>
    </main>
<!--    <router-link to="/">Home</router-link> |-->
<!--    <router-link to="/about">About</router-link>-->
<!--  <router-view/>-->
</template>

<script>
import { ref, reactive } from 'vue';
import Task from '@/components/component.task';
import CButton from '@/components/component.button';

export default {
    components: {
        Task,
        CButton,
    },
    setup() {
        // #222122

        const tasks = reactive([
            {
                id: 1,
                title: 'Поиск',
                time: '11:10'
            },
            {
                id: 2,
                title: 'МО доработки',
                time: '12:10'
            }
        ]);

        const newTask = () => {
            const last = tasks[tasks.length - 1];

            tasks.push({
                id: last.id + 1,
                title: 'new task',
                time: '14:00',
            })
        };

        const removeTask = (task) => {
            tasks.splice(tasks.indexOf(task), 1)
        }

        const tgApi = window.Telegram.WebApp;
        const colorSchema = ref(tgApi.colorScheme);

        return { colorSchema, tasks, newTask, removeTask }
    }
}
</script>

<style lang="scss">

</style>
