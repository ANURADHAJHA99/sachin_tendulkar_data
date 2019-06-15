<template>
    <div class="inference-container">
        <h2>Inference from Chart</h2>
        <span v-if="inference" class="inference">{{inference}}</span>
        <span v-if="winner" class="winner">Winner for {{titleText}} is {{winner}}</span>
    </div>
</template>

<script>
export default {
  name: 'Inference',
  props: ['inference', 'winner', 'titleText'],
};
</script>

<style scoped>
.inference-container {
    width: 25%;
    display: block;
    float: right;
    padding: 12px;
    margin-top: 150px;
    border-left: 2px solid rgb(112, 112, 112);
    border-right: 2px solid rgb(112, 112, 112);
     border-top: 2px solid rgb(112, 112, 112);
     border-bottom : 2px solid rgb(112, 112, 112);
     background-color: rgb(254, 246, 255);

    height: 220px;
}

.inference {
    color: rgb(4, 2, 7);
    font-size: 15px;
    font-weight: normal;
    display: block;
    margin-block-start: 0.42em;
    margin-block-end: 0.42em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
}

.winner {
    color: rgb(58,55,52);
    font-size: 15px;
    font-weight: bold;
    display: block;
    margin-top: 10px;
    margin-block-start: 0.42em;
    margin-block-end: 0.42em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
}

</style>
