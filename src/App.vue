<script setup>
import { computed } from "@vue/reactivity";
import { reactive, ref, watch } from "vue";

// ----------Example1----------
// ref 可以接受任何型別的資料, 修改 ref 值必須使用 .value
// reactive 只可以接受 Object, Array
// const name = ref("Kathy");
// //console.log(name);
// setTimeout(() => {
//   name.value = "Robert"; // .value 可以明確知道資料有被 ref 綁定
// }, 1000);

// ----------Example2----------
// ref 和 reactive 物件(陣列)使用的差異, ref 沒有辦法用 watch 去監控裡面的內容有沒被改變(除非強制深度檢查)
// const age = ref(10);
// const people1 = ref({
//   num: 0,
// });

// const people2 = reactive({
//   num: 0,
// });

// setTimeout(() => {
//   age.value = 25;
//   people1.value.num = 100;
//   people2.num = 100;
// }, 2000);

// // watch 函數 => 第一個參數是要監聽的對象, 第二個參數是監聽對象有更改後執行的 callback
// watch(age, () => {
//   console.log("age 被改變了");
// });
// watch(
//   people1,
//   () => {
//     console.log("people1 被改變了");
//   }
//   //{ deep: true } // 透過深度監聽去查找
// );
// watch(people2, () => {
//   console.log("people2 被改變了");
// });

// ----------Example3----------
// const num = ref(0);
// const people2 = reactive({
//   num: num,
// });
// console.log("num", num);
// console.log("people2", people2);

// setTimeout(() => {
//   people2.num = 100; // 不需要.value, 因為 ref 被嵌套在一個響應式對象中，作為屬性被訪問或更改時，會自動解包
// }, 2000);

// computed 是一個函式, 但不能傳參數進去, 只能透過函式 return 資料, 如果需要傳參數請用 function
// computed 可以定義資料, 主要功能是用來重組和計算資料
// ----------Example4----------
// computed 定義資料
// const data = computed(() => {
//   return {
//     name: "kathy",
//     age: 33,
//   };
// });

// ----------Example5----------
// const name = ref("Kathy");
// const data = computed(() => {
//   return `請叫我${name.value}}`;
// });
// setTimeout(() => {
//   name.value = "Robert";
// }, 2000);

// ----------Example6----------
// const user = reactive({
//   name: "Kathy",
//   age: 33,
// });
// const data = computed(() => {
//   return `我是${user.name}, 我今年 ${user.age}歲`;
// });
// console.log(data.value);
// setTimeout(() => {
//   user.name = "Robert";
//   user.age = 35;
// }, 2000);
//

// ----------Example7----------
// getter / setter
// computed 是一個函式, 裡面包的是一個物件(前面包的是function), 物件裡有2個函式
const count = ref(1);
const plusOne = computed({
  get: () => {
    return count.value;
  },
  set: (val) => {
    count.value = val;
  },
});
console.log("1=>", plusOne.value);
plusOne.value = 5;
console.log("2=>", plusOne.value);
console.log("3=>", count.value);
</script>

<template>
  <div>
    <!-- ----------Example1---------- -->
    <!-- ref 在模板中作為頂層屬性被訪問時，會自動解包, 所以不需要 .value -->
    <!-- <h1>{{ name }}</h1>  -->

    <!-- ----------Example2---------- -->
    <!-- <h1>{{ people1.num }}</h1>
    <h1>{{ people2.num }}</h1> -->

    <!-- ----------Example3---------- -->
    <!-- <h1>{{ people2.num }}</h1> -->

    <!-- ----------Example4---------- -->
    <!-- <h1>{{ data.name }}</h1>
    <h1>{{ data.age }}</h1> -->

    <!-- ----------Example5---------- -->
    <!-- <h1>{{ data }}</h1> -->

    <!-- ----------Example6---------- -->
    <!-- <h1>{{ data }}</h1> -->
  </div>
</template>

<style></style>
