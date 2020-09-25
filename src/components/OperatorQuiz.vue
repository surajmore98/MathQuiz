<template>
    <div>
        <div v-if="isQuizStart">
            <h2>Question is :</h2>
            <h3>{{ operandleft }} {{ operator }} {{ operandRight }}</h3>

            <h2>Answers are:</h2>
            <button @click="selectAnswers(answer)" v-for="(answer, index) of answers" :key="index"> {{answer}} </button>
        </div>
        <div v-else>
            <button @click="onStart"> Start </button>
        </div>
    <div>
        <h3 v-show="validAnswer === true" style="color:green"> Answer is correct</h3> 
        <h3 v-show="validAnswer === false" style="color:red">Answer is wrong</h3>
         <br/>
        <button @click="$emit('on-back')"> Back </button>
        <button v-if="isQuizStart" @click="onStart"> Next </button>
    </div>
        
    </div>    
</template>

<script>
export default {
    props: ['operator'],
    data() {
        return {
            operandleft: null,
            operandRight: null,
            isQuizStart: false,
            answers: [],
            expectedAns: null,
            validAnswer: null
        } 
    },

    methods: {
        selectAnswers(answer){
            console.log("this.expectedAns is"+ this.expectedAns);
            if(this.expectedAns === answer){
                this.validAnswer = true;
            } else {
                this.validAnswer = false;                
            }
        },
        
        onStart(){
            this.validAnswer = null;
            this.operandleft = parseInt(Math.random() * 13);
            this.operandRight = parseInt(Math.random() * 13);
            this.isQuizStart = true;
            this.answers =[];
            const mets={
                '+': (a,b) => a+b,
                '-': (a,b) => a-b,
                '/': (a,b) => a/b,
                '*': (a,b) => a*b
            }
             for(let i =0; i<5; i++){
                let answer = mets[this.operator](this.operandleft + parseInt(Math.random()*6), this.operandRight + parseInt(Math.random()*6));                
                this.answers.push(answer);
            }
            
            this.expectedAns = mets[this.operator](this.operandleft, this.operandRight);
            const index = parseInt(Math.random() * this.answers.length);
            console.log("index is"+ index);
            this.answers[index] = this.expectedAns;
        }
    }
}
</script>
