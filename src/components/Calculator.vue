<template>
  <div id="background">
    <div id="result">{{display}}</div>
    <div id="main">
      <div id="first-rows">
        <button id="del" class="del" @click="del" >Del</button>
        <button value="%" class="btn-style operator opera-bg">%</button>
        <button @click="add" class="btn-style opera-bg value operator">+</button>
      </div>

      <div class="rows">
        <button  @click="append(7)" class="btn-style  num first-child">7</button>
        <button @click="append(8)" class="btn-style num">8</button>
        <button  @click="append(9)" class="btn-style num">9</button>
        <button @click="take" class="btn-style opera-bg operator">-</button>
      </div>

      <div class="rows">
        <button  @click="append(4)" class="btn-style num first-child">4</button>
        <button  @click="append(5)" class="btn-style num">5</button>
        <button  @click="append(6)" class="btn-style num">6</button>
        <button @click="multiply" class="btn-style opera-bg operator">x</button>
      </div>

      <div class="rows">
        <button @click="append(1)" id="button" class="btn-style num first-child">1</button>
        <button @click="append(2)" class="btn-style num">2</button>
        <button @click="append(3)" class="btn-style num">3</button>
        <button @click="devide" class="btn-style opera-bg operator">/</button>
      </div>

      <div class="rows">
        <button value="0" class="zero" id="delete">0</button>
        <button value="." class="btn-style period opera-bg ">.</button>
        <button @click="equal" class="eqn">=</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      previous: null,
      display: 0,
      operator: null,
      operatorClicked: false

    }
  },
  methods: {
    append(number){
      if (this.operatorClicked === true) {
        this.display = '';
        this.operatorClicked = false;
      }
      this.display = this.display === 0
          ? (this.display = number)
          : '' + this.display + number;
    },
    del(){
      this.display = 0
    },
    add() {
      this.operator = (a, b) => a + b;
      this.previous = this.display;
      this.display='+';
      this.operatorClicked = true;
    },
    equal() {
      this.display = this.operator(Number(this.previous), Number(this.display));
      this.previous = null;
      this.operatorClicked = true;
    },
    devide() {
      this.operator = (a, b) => a / b;
      this.previous = this.display;
      this.display='/';
      this.operatorClicked = true;
    },
    take() {
      this.operator = (a, b) => a - b;
      this.previous = this.display;
      this.display='-';
      this.operatorClicked = true;
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.previous = this.display;
      this.display='*';
      this.operatorClicked = true;
    },



  }


}
</script>

<style scoped>
body {
  background:#777;
}

#background {
  width:290px;
  height:400px;
  background:gray;
  margin:50px auto;
}

button {
  border:0;
  color:#fff;
}

#result {
  display:block;
  font-family: sans-serif;
  width:230px;
  height:40px;
  margin:10px auto;
  text-align: right;
  border:0;
  background:#3b3535;
  color:#fff;
  padding-top:10px;
  font-size:20px;
  margin-left: 25px;
  outline: none;
  overflow: hidden;
  letter-spacing: 4px;
  position: relative;
  top:10px;
}

#result:hover {
  cursor: text;
}

#first-rows {
  margin-bottom: 20px;
  position: relative;
  top:10px;
  margin-top: 30px;
}

.rows {
  width:260px;
  margin-top:10px;
}

#delete {
  width:110px;
  height:50px;
  margin-left:25px;
  border-radius:4px;
  background:#24b4de;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  /*outline:none;*/
  border-bottom:3px solid #399cb9;
}

.btn-style {
  width:50px;
  height:50px;
  margin-left:5px;
  border-radius:4px;
}

.eqn {
  width:50px;
  height:50px;
  margin-left:5px;
  border-radius:4px;
  background:#17a928;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  border-bottom:3px solid #1f7a29;
}
#eqn:active {
  background:#17a928;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #1f7a29;
}
.first-child {
  margin-left:25px;
}
/* Adding background color to the number values */
.num{
  background:#000;
  color:#fff;
  font-size:26px;
  cursor:pointer;
  outline:none;
  border-bottom:3px solid #333;
}
.num:active {
  background:#000;
  color:#fff;
  font-size:26px;
  cursor:pointer;
  outline:none;
  box-shadow: inset 5px 5px 5px #555;
}

/*Adding background color to the operator values */
.opera-bg {
  background:#333;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  border-bottom:3px solid #555;
}

.opera-bg:active {
  background:#333;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #555;
}
.del{
  width:110px;
  height:50px;
  border-radius:4px;
  background:#24b4de;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  /*outline:none;*/
  border-bottom:3px solid #399cb9;
}
</style>