<template>
<b-container>
  <b-row v-show="screen == 'test'">
    <b-row>
      <question :question="questions[current]" :current="current"/>
    </b-row>
    <b-row id="nextAnhPrev">
      <b-col id="prev">
        <button 
            class="btn" 
            @click="current--" 
            v-show="current > 0">
            &#8592;
          </button>
           <!-- <button 
           id="doNotClick"
            class="btn" 
            v-show="current = 0">
            &#8592;
          </button> -->
      </b-col>
      <b-col>
        <button 
            class="btn" 
            @click="current++" 
            v-show="current < questions.length-1">
            &#8594;
          </button>
      </b-col>
    </b-row>
    <b-row id="number">
      Question {{(current+1)}}/{{questions.length}}
    </b-row>
    <b-row>
      <b-col  id="nopBai">
        <button 
              class="btn" 
              @click="screen = 'result'" 
              v-show="current == questions.length-1">
              Nộp bài
        </button>
      </b-col>
    </b-row>
  </b-row>
  <b-row v-show="screen == 'result'">
    <result :questions="questions" :current="current"/>
  </b-row>
</b-container>


</template>

<script>
import Question from './components/Question.vue'
import Result from './components/Result.vue'
export default {
  components:{
    Question, Result
  },
  data(){
    return{
      screen: 'test',
      current: 0,
      questions:[
        {
          content:'Sự kiện nào xảy ra khi người dùng kích vào một phần tử HTML trên trang?',
          answers:[
            'onclick', 
            'onmouseclick', 
            'onmouseover', 
            'onchange'
          ],
          correctAnswer: 0,
          point: 0.5,
          answer: null

        },
        {
          content:'Câu lệnh break kết hợp với vòng lặp để làm gì?',
          answers:[
            'Ngưng vòng lặp nếu gặp lệnh này', 
            'Không có ý nghĩa gì trong vòng lặp', 
            'Nhảy đến một tập lệnh khác', 
            'Không thể kết hợp được'
          ],
          correctAnswer: 0,
          point: 0.5,
          answer: null

        },
        {
          content:'Làm thế nào để bo tròn góc cạnh các phần tử?',
          answers:[
            'border[round]: 30px;', 
            'corner-effect: round;', 
            'border-radius: 30px;', 
            'alpha-effect: round-corner;'
          ],
          correctAnswer: 2,
          point: 1,
          answer: null

        },
        {
          content:'Làm thế nào để thêm bóng (shadow) cho các phần tử trong CSS3?',
          answers:[
            'box-shadow: 10px 10px 5px grey;', 
            'shadow-right: 10px shadow-bottom: 10px;', 
            'shadow-color: grey;', 
            'alpha-effect[shadow]: 10px 10px 5px grey;'
          ],
          correctAnswer: 0,
          point: 1,
          answer: null

        },
        {
          content:'Đâu không phải là phép toán được dùng so sánh trong PHP?',
          answers:[
            '===', 
            '>=', 
            '!=', 
            '<=>'
          ],
          correctAnswer: 3,
          point: 1,
          answer: null

        },
        {
          content:'Đoạn mã nào sau đây được sử dụng để chú thích PHP?',
          answers:[
            '/* commented code here */', 
            '// you are handsome', 
            '# you are gay', 
            'Tất cả các ý trên'
          ],
          correctAnswer: 0,
          point: 1,
          answer: null

        },
        {
          content:'SQL là từ viết tắt của?',
          answers:[
            'Strong Question Language', 
            'Structured Question Language', 
            'Structured Query Language'
          ],
          correctAnswer: 2,
          point: 1,
          answer: null

        },
        {
          content:'Câu lệnh SQL nào được dùng để trích xuất dữ liệu từ database?',
          answers:[
            'Get', 
            'Open', 
            'Extract', 
            'Select'
          ],
          correctAnswer: 3,
          point: 1,
          answer: null

        },
        {
          content:'Trong SQL làm thế nào để chọn tất cả các bản ghi từ bảng Persons với giá trị trong cột FirstName là Peter?',
          answers:[
            'Select [all] FROM Persons WHERE FirstName=’Peter’', 
            'Select * FROM Persons WHERE FirstName LIKE’Peter’', 
            'Select [all] FROM Persons WHERE FirstName LIKE’Peter’', 
            'Select * FROM Persons WHERE FirstName=’Peter’'
          ],
          correctAnswer: 3,
          point: 1.5,
          answer: null

        },
        {
          content:'Từ khóa SQL nào được sử dụng để sắp xếp danh sách kết quả?',
          answers:[
            'SORT BY', 
            'ORDER', 
            'ORDER BY', 
            'SORT'
          ],
          correctAnswer: 2,
          point: 1.5,
          answer: null

        },
      ]
    }
  } 
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
body {
  background-image: url('./assets/bgr.png');
  background-repeat: no-repeat;
    background-attachment: fixed;
  background-size: cover;
}
#prev{
  display: flex;
  justify-content: right;
}
#nextAnhPrev{
  margin-top: 2px;
}
.btn{
  background-color: #1E807F;
  border: 1px solid #1C5476;
}
#number{
  display: flex;
  justify-content: center;
}
#doNotClick{
  background-color: black;
}
#nopBai{
  display: flex;
  justify-content: center;
}
</style>
