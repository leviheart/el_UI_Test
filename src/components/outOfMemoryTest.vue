<template>
  <div class="container">
    <div>
      {{ "hhhhhhhh" }}
      <!-- 显示字符串 -->
      <!-- Display string -->
    </div>
  </div>
</template>

<script>
import lineData from "@/assets/geoData/lineData"; // 导入线数据 Import line data

let testMeomery = []; // 定义数组用于测试内存 Define array for memory test

export default {
  data() {
    return {};
  },

  mounted() {
    let data = new Map(); // 定义Map对象 Define Map object

    // 循环添加数据到Map
    // Loop to add data to Map
    for (let index = 0; index < 10; index++) {
      data.set(index, index + 10);
    }

    // 遍历Map 的两种方式 for of和forEach
    // Iterate Map
    for (const [key, value] of data) {
      console.log(key, value);
    }

    data.forEach((value, key, mapSelf) => {
      console.log(value, key, mapSelf);
    });

    console.log(data, data?.get(1));

    let abc = {
      // 定义对象 Define object
      a: {
        b: {
          c: ["213"],
        },
        d: {
          c: ["123"],
        },
      },
    };

    // let ta = abc.a.b.c[0]; //只是字符串 没有引用传递 Only string no reference pass

    // let ta = abc.a.b.c //数组,有引用传递 Array has reference pass

    // ta = "124325435"; //只是字符串 没有引用传递 Only string no reference pass

    // ta[0] = "!23445453" //数组,有引用传递 Array has reference pass

    // ta = ['21332'] //赋值对象,开辟了新的引用地址 Assign object, new reference

    let geo = [
      // 定义数组 Define array
      {
        a: {
          b: [["0", "1"]],
        },
      },
      {
        a: {
          b: [["2", "3"]],
        },
      },
    ];

    geo.forEach((el, index) => {
      // 遍历数组 Iterate array
      if (index == 0) {
        el.a.b = [["@3", "4554"]];
      }
    });

    console.log(abc, geo);

    let one = 3; // 定义变量 Define variable
    let two = 2;
    let testThree = one == 1 ? "32" : "55"; // 条件运算 Conditional operation

    console.log(testThree, lineData);

    testMeomery = lineData.features; // 赋值数组 Assign array

    this.test1();
  },

  methods: {
    test1() {
      let big = "big"; // 定义变量 Define variable

      // 循环数组 Iterate array
      for (let index = 0; index < lineData.features.length; index++) {
        testMeomery[index].properties.sum = big; // 修改数组元素属性 Modify array element property
      }

      console.log(testMeomery);

      this.test2(big); // 调用方法 Invoke method
    },

    test2(big) {
      // 循环数组 Iterate array
      for (let index = 0; index < lineData.features.length; index++) {
        testMeomery[index].properties.sum = big; // 修改数组元素属性 Modify array element property
      }

      console.log(testMeomery);
    },
  },
};
</script>

<style scoped></style>

<!-- 总结 Summary:

1. 导入数据 Import data
2. 定义变量和数组 Define variables and arrays 
3. 遍历数据 Iterate data
4. 条件判断 Conditional logic
5. 修改数据 Modify data
6. 调用方法 Invoke methods

-->

