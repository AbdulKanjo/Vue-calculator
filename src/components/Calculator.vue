<template>

  <div class="Calculator">
    <div class="display">
      {{current|| '0'}}
    </div>
    <div @click="clear" class="buttons">
      C
    </div>
    <div @click="sign" class="buttons">
      +/-
    </div>
    <div @click="percent" class="buttons">
      %
    </div>
    <div @click="divide" class=" operator buttons">
      /
    </div>
    <div @click="append('7')" class="buttons">
      7
    </div>
    <div @click="append('8')" class="buttons">
     8
    </div>
    <div @click="append('9')" class="buttons">
     9
    </div>
     <div @click="times" class=" operator buttons">
     x
    </div>
     <div @click="append('4')" class="buttons">
     4
    </div>
     <div @click="append('5')" class="buttons">
     5
    </div>
     <div @click="append('6')" class="buttons">
     6
    </div>
     <div @click="minus" class=" operator buttons">
     -
    </div>
     <div @click="append('1')" class="buttons">
     1
    </div>
     <div @click="append('2')" class="buttons">
     2
    </div>
     <div @click="append('3')" class="buttons">
     3
    </div>
     <div @click="add"  class=" operator buttons">
     +
    </div>
     <div @click="append('0')" class="zero buttons">
     0
    </div>
     <div @click="dot" class="buttons">
     .
    </div>
     <div @click="equal" class=" operator buttons">
     =
    </div>

    
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      previous: null,
      operator: null,
      operatorClicked: false
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      this.current.indexOf(".") === -1 ? this.append(".") : this.current;
    },
    setPreviouse() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPreviouse();
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPreviouse();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPreviouse();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPreviouse();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.Calculator {
  width: 400px;
  margin: 0 auto;
  font-size: 20px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display {
  grid-column: 1/5;
  background-color: #333;
  color: white;
}
.zero {
  grid-column: 1/3;
}
.buttons {
  background-color: #eee;
  border: 1px solid #999;
}
.operator {
  background-color: orange;
  color: white;
}
</style>

</style>
