<template>
  <div class="main">
    <h1>ただのじゃんけん</h1>
    <button @click="userSelect">じゃんけんをする</button>
    <div class="player1">
      <input
      type="text"
      v-model="player1"
      placeholder="名前を入力してください">
      <p>{{player1}} :
        <span class="firstResult">{{ firstResult }}</span>
      </p>
    </div>
    <p class="vs">VS</p>
    <div class="pleyer2">
      <input
      type="text"
      v-model="player2"
      placeholder="名前を入力してください">
      <p>{{ player2 }} :
        <span class="secondResult">{{ secondResult }}</span>
      </p>
    </div>
    <div class="result">
      <p>
      結果 :
      <span>{{ result }}</span>
      </p>
      <button @click="reset">リセット</button>
    </div>

    <ul>
      <span>勝ち</span>
      <li v-for="turn in results" :key="turn">
        {{turn}}
      </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      player1: '',
      player2: '',
      result: '',
      results: [],
      firstResult: '',
      secondResult: '',
      list: ['グー', 'チョキ', 'パー'],
    }
  },
  methods: {
    userSelect() {
      this.firstResult = this.list[Math.floor(Math.random() * this.list.length)];
      this.secondResult = this.list[Math.floor(Math.random() * this.list.length)];

      switch (this.firstResult) {
        case 'グー':
          if(this.secondResult == 'チョキ') {
            this.result = `${this.player1}の勝ち`;
            this.results.push(this.player1);
          } else if(this.secondResult == 'グー') {
            this.result = 'アイコ';
          } else {
            this.result = `${this.player2}の勝ち`;
            this.results.push(this.player2);
          }
          break;

        case 'チョキ':
          if(this.secondResult == 'パー') {
            this.result = `${this.player1}の勝ち`;
            this.results.push(this.player1);
          } else if(this.secondResult == 'チョキ') {
            this.result = 'アイコ';
          } else {
            this.result = `${this.player2}の勝ち`;
            this.results.push(this.player2);
          }
          break;

        case 'パー':
          if(this.secondResult == 'グー') {
            this.result = `${this.player1}の勝ち`
            this.results.push(this.player1);
            console.log(this.player1);
          } else if(this.secondResult == 'パー') {
            this.result = 'アイコ'
          } else {
            this.result = `${this.player2}の勝ち`
            this.results.push(this.player2);
            console.log(this.player1);
          }
          break;
        default:
          break;
      }
    },
    reset() {
      this.firstResult = '';
      this.secondResult = '';
      this.result = '';
      this.results = [];
    }
  }
}
</script>

<style>
.main {
  margin: 0 auto;
  text-align: center;
  position: relative;
}
h1 {
  color: #f5df4b;
}
button {
  width: 150px;
  height: 50px;
  border: none;
  outline: none;
  transition: 0.3s;
  border-radius: 4px;
  margin-bottom: 20px;
  background-color: #f0eee9;
  box-shadow: 0 2px 4px rgba(0,0,0,0.3);
}
button:hover {
  cursor: pointer;
  background-color: #e9ebf0;
}
button:active {
  box-shadow: none;
  transform: translateY(2px);
}
span {
  font-size: 20px;
  font-weight: bold;
}
.firstResult {
  color: darkorange;
}
.secondResult {
  color: #0073ff;
}
.vs {
  font-size: 30px;
  color: #cf5c78;
  font-weight: bold;
}
ul {
  padding-left: 0;
  list-style: none;
  position: absolute;
  top: 0;
  left: 400px;
}
li {
  font-weight: 400;
}
</style>