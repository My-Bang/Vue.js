<script>
export default {
  data() {
    return {
      
      operator: null,
      prev: null,
      cur: null, 
      output: null,    
      darkMode: false,    // 현재 모드를 구분하기 위하여 다크모드 추가

      operatorActions: {
        '+': (a, b) => a + b,
        '-': (a, b) => a - b,
        '*': (a, b) => a * b,
        '/': (a, b) => a / b,
      },
    };
  },

  mounted() {
    // 컴포넌트가 마운트되면 키보드 입력 리스너 추가
    window.addEventListener("keydown", this.handleKeyDown);
  },

  beforeUnmount() {
    // 컴포넌트가 파괴되기 전에 키보드 리스너 제거
    window.removeEventListener("keydown", this.handleKeyDown);
  },

  methods: {
    // 계산기 초기화
    clear() {
      this.output = null;
      this.prev = null;
      this.cur = null;
      this.operator = null;
    },

    // 연산 실행 또는 연산자 처리
    calculate(n) {
      // 현재 값이 없으면 계산하지 않음 (= 입력 전 cur 없을 경우 방지)
      if (this.cur === null || this.cur === "") return;

      // cur을 숫자로 변환
      this.cur = Number(this.cur);

      // 기존 연산자와 이전 숫자가 있는 경우 → 계산 실행
      if (this.operator != null && this.prev != null) {
        this.prev = this.operatorActions[this.operator](this.prev, this.cur);

        // =이면 결과 출력, 아니면 연산자 갱신
        if (n === '=') {
          this.output = this.prev;
          this.operator = null;
          this.cur = null;
        } else {
          this.operator = n;
          this.cur = null;
          this.output = null;
        }

      } else {
        // 숫자 없이 연산자만 입력한 경우 무시
        if (n === '=' || this.cur === null) return;

        // 첫 입력 연산자 처리
        this.operator = n;
        this.prev = this.cur;
        this.cur = null;
        this.output = null;
      }
    },

    // 숫자 또는 소수점 입력 처리
    userInput(n) {
      // 소수점 중복 입력 방지
      if (n === '.') {
        if (this.cur && this.cur.includes('.')) return; // 이미 소수점이 있으면 무시
        if (this.cur === null) {
          this.cur = '0.'; // 시작할 때 . 입력하면 0. 으로 처리
          this.output = this.cur;
          return;
        }
      }

      // 숫자 입력 처리 (null이면 새로 시작, 아니면 이어붙이기)
      this.cur = this.cur === null ? n : (this.cur += n);
      this.output = this.cur;
    },

    // 버튼 또는 키보드 입력 처리
    operation(e) {
      const n = typeof e === "string" ? e : e.currentTarget.value;

      if (n === 'C') {
        // 초기화 메서드 호출
        this.clear();

      } else if (['+', '-', '*', '/', '='].includes(n)) {
        // 연산자 중복 입력 방지 (cur 없이 연산자 반복 입력 시 교체만 허용)
        if (this.cur === null && this.operator !== null && n !== '=') {
          this.operator = n;
          return;
        }

        // 연산 처리
        this.calculate(n);

      } else {
        // 숫자 및 소수점 입력 처리
        this.userInput(n);
      }
    },

    // 다크 모드 토글
    dark() {
      this.darkMode = !this.darkMode; // 상태 반전
      document.body.classList.toggle("dark-mode", this.darkMode); // body에 클래스 추가/제거
    },

    // 키보드 입력 처리
    handleKeyDown(e) {
      const key = e.key;

      if (!isNaN(key)) {
        // 숫자 키 입력
        this.operation(key);
      } else if (["+", "-", "*", "/"].includes(key)) {
        // 연산자 키 입력
        this.operation(key);
      } else if (key === "Enter" || key === "=") {
        // 엔터 또는 = 입력 시 계산
        e.preventDefault(); // form 제출 방지
        this.operation("=");
      } else if (key === "c" || key === "C") {
        // 초기화
        this.operation("C");
      } else if (key === ".") {
        // 소수점 입력
        this.operation(".");
      }
    }
  },
};
</script>

<template>
   <div class="calculator">
             <button @click="dark">다크모드</button>   <!-- 다크 모드 버튼 추가 -->
      <form name="forms">
        <input v-model="output" type="text" name="output" readonly /> 
        <input type="button" class="clear" value="C" @click="operation"/>
        <input type="button" class="operator" value="/" @click="operation"/>
        <input type="button" value="1" @click="operation"/>
        <input type="button" value="2" @click="operation"/>
        <input type="button" value="3" @click="operation"/>
        <input type="button" class="operator" value="*" @click="operation"/>
        <input type="button" value="4" @click="operation"/>
        <input type="button" value="5" @click="operation"/>
        <input type="button" value="6" @click="operation"/>
        <input type="button" class="operator" value="+" @click="operation"/>
        <input type="button" value="7" @click="operation"/>
        <input type="button" value="8" @click="operation"/>
        <input type="button" value="9" @click="operation"/>
        <input type="button" class="operator" value="-" @click="operation"/>
        <input type="button" class="dot" value="." @click="operation"/>
        <input type="button" value="0" @click="operation"/>
        <input type="button" class="operator result" value="=" @click="operation"/>
      </form>
    </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #ffffff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator {
  width: 287px;
  border: 1px solid #333;
  background-color: #ccc;
  padding: 5px;
}

.calculator form {
  display: grid;
  grid-template-columns: repeat(4, 65px);
  grid-auto-rows: 65px;
  grid-gap: 5px;
}

.calculator form input {
  border: 2px solid #333;
  cursor: pointer;
  font-size: 19px;
}

.calculator form input:hover {
  box-shadow: 1px 1px 2px #333;
}

.calculator form .clear {
  background-color: #ed4848;
}

.calculator form .operator {
  background-color: orange;
}

.calculator form .dot {
  background-color: green;
}

.calculator form input[type='text'] {
  grid-column: span 4;
  text-align: right;
  padding: 0 10px;
}

.calculator form .clear {
  grid-column: span 3;
}

.calculator form .result {
  grid-column: span 2;
}






body.dark-mode {
  background-color: #1e1e1e;
  color: white;
}

body.dark-mode .calculator {
  background-color: #333;
  border-color: #aaa;
}

body.dark-mode .calculator form input {
  background-color: #555;
  color: white;
  border-color: #888;
}

body.dark-mode .calculator form input:hover {
  box-shadow: 1px 1px 3px #aaa;
}

body.dark-mode .calculator form .operator {
  background-color: #ff9800;
}

body.dark-mode .calculator form .clear {
  background-color: #f44336;
}

body.dark-mode .calculator form .dot {
  background-color: #4caf50;
}

</style>
