<template>
    <div class="task" ref="el">
        <div>{{ task.id }}</div>
        <div>
            <h1 class="task__title">{{ task.title }}</h1>
            <h2 class="task__status">В процессе</h2>
            <p class="task__time">{{ task.time }}</p>
        </div>
        <div>
            <a @click="removeCallback(task)">
                <i class="fa-solid fa-xmark"></i>
            </a>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
    name: "component.task",
    props: ['initData', 'removeCallback'],
    setup({ initData }) {
        const task = ref(initData);
        const el = ref(null);

        return { task, el };
    }
}
</script>

<style lang="scss" scoped>
.task {
    padding: 1.5rem 2rem;
    box-shadow: 2px 4px 7px 2px rgba(0, 0, 0, 0.1);
    border-radius: 1rem;
    margin-bottom: 1rem;
    display: grid;
    grid-template-columns: 1fr 5fr 1fr;
    gap: 5px;
    align-items: center;
    &__title {
        font-weight: 500;
        font-size: 1rem;
        margin-bottom: .125rem;
    }
    &__status {
        font-weight: 300;
        font-size: .875rem;
        margin-bottom: .2rem;
    }
    &__time {
        font-weight: 300;
        font-size: .75rem;
        opacity: .5;
    }
}
</style>