<template>
<b-container id="container">
    <b-row>
        Total Point: {{ questions.reduce( (total,question)=>{
            if( question.answer == question.correctAnswer ){
                total += question.point;               
            }
            return total;
        }, 0) }}
    </b-row>
    <b-row 
    id="question"
    v-for="(question, questionIndex) in questions" 
    :key="questionIndex">
         {{questionIndex+1}}. {{question.content}} ({{question.point}}đ)
        <b-row>
            <b-col cols="10" v-for="(answer,index) in question.answers"
            :key="index"
            class="answers"
            :class="{
                    wrong: question.answer == index && question.answer != question.correctAnswer, 
                    correctBut: question.answer == null && question.correctAnswer == index, 
                    correct: question.correctAnswer == index
                    }">
                    {{  answer}}            
            </b-col>
        </b-row>    
    </b-row>    
</b-container>
</template>

<script>
export default {
    props:['questions', 'current']
}
</script>

<style scoped>
.wrong{
    font-weight: bold;
    font-size: 18px;
}
.correct{
    font-weight: bold;
    font-size: 18px;
    background-color: #186F7B;

}
.correctBut{
    font-weight: bold;
    font-size: 18px;
    background-color: #A4A4AA;

}
#container{
    width: 600px;
    margin-top: 20px;
    margin-bottom: 30px;
}
.answers{
    padding-left: 8px;
    border: 1px solid black;
    border-radius: 5px;
    margin-top: 2px;
    margin-left: 30px;
}
#question{
    margin-top: 8px;
}
</style>>
