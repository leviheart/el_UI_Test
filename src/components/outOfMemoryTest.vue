<template>
  <div class="container">
    <div>
    {{ "hhhhhhhh" }}
    </div>
  </div>
</template>
<script>
import lineData from "@/assets/geoData/lineData";
let testMeomery = [];
export default {
  data() {
    return {};
  },
  mounted() {
    let data = new Map();
    for (let index = 0; index < 12; index++) {
      data.set(index, index + 10);
    }
    for (const [key, value] of data) {
      console.log(key, value);
    }
    data.forEach((value, key, index, index1) => {
      console.log(value, key, index, index1);
    });
    console.log(data, data?.get(11));

    let abc = {
      a: {
        b: {
          c: ["213"],
        },
        d: {
          c: ["123"],
        },
      },
    };
    // let ta = abc.a.b.c[0]; //只是字符串 没有引用传递
    // let ta = abc.a.b.c //数组，有引用传递
    // ta = "124325435"; //只是字符串 没有引用传递
    // ta[0] = "!23445453" //数组，有引用传递
    // ta = ['21332'] //赋值对象，开辟了新的引用地址
    let geo = [
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
      if (index == 0) {
        el.a.b = [["@3", "4554"]];
      }
    });
    console.log(abc, geo);

    let one = 3;
    let two = 2;
    let testThree = one == 1 ? "32" : "55";
    console.log(testThree, lineData);
    testMeomery = lineData.features;
    this.test1();
  },

  methods: {
    test1() {
        let big = "big"
        for (let index = 0; index < lineData.features.length; index++) {
        testMeomery[index].properties.sum = big;
      }
      console.log(testMeomery);
        this.test2(big);
    },
    test2(big){
        for (let index = 0; index < lineData.features.length; index++) {
        testMeomery[index].properties.sum = big;
      }
      console.log(testMeomery);
    }
  },
};
</script>
<style scoped></style>
