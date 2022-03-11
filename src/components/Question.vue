<template>

<b-container id="container">
    <b-row>      
            {{current+1}}. {{question.content}} ({{question.point}}đ)
    </b-row>
    <b-row>
        <b-col cols="1"></b-col>
        <b-col cols="10">
                <b-row 
                class="answers"
                v-for="(answer,index) in question.answers"
                :key="index"
                @click="question.answer = index"
                :class="{selected: question.answer == index}"
                >
                {{answer}}
                </b-row>
        </b-col>
    </b-row>
   
</b-container>
</template>
<script>
export default {
    props:['question', 'current']
}
</script>
<style scoped>
.selected{
    font-weight: bold;
    font-size: 18px;
}
#container{
    width: 600px;
    margin-top: 20px;
}
.answers{
    padding-left: 8px;
    border: 1px solid black;
    border-radius: 5px;
    margin-top: 2px;
}
</style>>
