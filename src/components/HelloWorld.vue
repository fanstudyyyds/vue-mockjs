<template>
  <div class="hello"></div>
</template>

<script>
export default {
  name: "HelloWorld",
  mounted() {
    var Mock = require("mockjs");
    var Random = Mock.Random;
    console.log(Random);
    Mock.Random.extend({
      phone: function () {
        var phonePrefixs = ["132", "135", "189"]; // 自己写前缀哈
        return this.pick(phonePrefixs) + Mock.mock(/\d{8}/); //Number()
      },
    });

    var data = Mock.mock({
      "list|1-2": [
        {
          "id|+10": 1,
          title: "@ctitle(5,8)",
          name: "@cname()",
          nameyw: "@first()",
          date: "@date(yyyy-MM-dd A HH:mm:ss)",
          time: "@time(yyyy-MM-dd A HH:mm:ss)",
          city: "@city(true)",
          url: "@url()",
          guid: "@guid()",
          idCard: Random.id(),
          phone: Mock.Random.phone(),
          email: "@email()",
          dataImage: "dataImage()",
          "sex|0-1": 1, //随机性别
          nowDateYear: Random.now("year"),
          nowDateMonth: Random.now("month"),
          nowDateWeek: Random.now("week"),
          nowDateDay: Random.now("day"),
          nowDateHour: Random.now("hour"),
          nowDateMinute: Random.now("minute"),
          nowDateSecond: Random.now("second"),
        },
      ],
    });
    console.log(JSON.stringify(data, null, 4));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
