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
    <div class="buttons">
      %
    </div>
    <div class=" operator buttons">
      /
    </div>
    <div class="buttons">
      7
    </div>
    <div class="buttons">
     8
    </div>
    <div class="buttons">
     9
    </div>
     <div class=" operator buttons">
     x
    </div>
     <div class="buttons">
     4
    </div>
     <div class="buttons">
     5
    </div>
     <div class="buttons">
     6
    </div>
     <div class=" operator buttons">
     -
    </div>
     <div class="buttons">
     1
    </div>
     <div class="buttons">
     2
    </div>
     <div class="buttons">
     3
    </div>
     <div class=" operator buttons">
     +
    </div>
     <div class="zero buttons">
     0
    </div>
     <div class="buttons">
     .
    </div>
     <div class=" operator buttons">
     =
    </div>

    
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "1231"
    };
  },
  methods: {
    clear() {
      this.current = "";
    }
  },
  sign() {
    this.current = this.current.charAt(0) === "-" ? this.current.slice(1) : ``;
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
