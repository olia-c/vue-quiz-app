<template>
    <div class="result">
        <div class="title">{{ result.title }}</div>
        <div class="desc">
            {{ result.description }}
        </div>
    </div>
</template>


<script>
export default {
    props: ['result']
}
</script>