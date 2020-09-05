<template>
  <ul id="countdown">
    <li id="days" v-show="days">
      <div class="label">Days</div>
      <div class="number">{{ days }}</div>
    </li>
    <li id="hours">
      <div class="label">hours</div>
      <div class="number">{{ hours }}</div>
    </li>
    <li id="minutes">
      <div class="label">Minutes</div>
      <div class="number">{{ minutes }}</div>
    </li>
    <li id="seconds">
      <div class="label">Secondes</div>
      <div class="number">{{ seconds }}</div>
    </li>
  </ul>
</template>

<script>
import moment from "moment";
export default {
  data() {
    return {
      actualTime: moment().format("X"),
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    };
  },
  methods: {
    addOneSecondToActualTimeEverySecond() {
      var component = this;
      component.actualTime = moment().format("X");
      setTimeout(function() {
        component.addOneSecondToActualTimeEverySecond();
      }, 1000);
    },
    getDiffInSeconds() {
      return moment("2020-09-23 00:00:00").format("X") - this.actualTime;
    },
    compute() {
      var duration = moment.duration(this.getDiffInSeconds(), "seconds");
      this.days = duration.days() > 0 ? duration.days() : 0;
      this.hours = duration.hours() > 0 ? duration.hours() : 0;
      this.minutes = duration.minutes() > 0 ? duration.minutes() : 0;
      this.seconds = duration.seconds() > 0 ? duration.seconds() : 0;
    },
  },
  created() {
    this.compute();
    this.addOneSecondToActualTimeEverySecond();
  },
  watch: {
    actualTime(val, oldVal) {
      this.compute();
      console.log("Old value is:" + oldVal + " New value is: " + val);
    },
  },
};
</script>
<style scopped>
html {
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: inherit;
}

html,
body {
  width: 100%;
  height: 100%;
  background: linear-gradient(270deg, #296958, #a0b6b0);
  background-size: 400% 400%;
  -webkit-animation: AnimationName 14s ease infinite;
  -moz-animation: AnimationName 14s ease infinite;
  -o-animation: AnimationName 14s ease infinite;
  animation: AnimationName 14s ease infinite;
}
@-webkit-keyframes AnimationName {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
@-moz-keyframes AnimationName {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
@-o-keyframes AnimationName {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
@keyframes AnimationName {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
ul#countdown {
  position: relative;
  top: 50%;
  transform: translateY(-50%);
  width: 50%;
  margin: 333px auto;
  padding: 15px 0 20px 0;
  color: #fff;
  border: 1px solid #adafb2;
  border-width: 1px 0;
  overflow: hidden;
  font-family: "Arial Narrow", Arial, sans-serif;
  font-weight: bold;
}
li {
  margin: 0 -3px 0 0;
  padding: 0;
  display: inline-block;
  width: 25%;
  font-size: 72px;
  font-size: 6vw;
  text-align: center;
}
.label {
  color: #414347;
  font-size: 18px;
  font-size: 1.5vw;
  text-transform: uppercase;
}
</style>
