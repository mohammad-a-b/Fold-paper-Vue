<script setup>
import { ref } from "vue";

const foldCount = ref(0);
const thickness = ref(0.1);
const unit = ref("mm");
const comparisonText = ref("");
const comparisonImage = ref(image1);

import image1 from "@/assets/images/paper.jpg";
import hair from "@/assets/images/hair.jpg";
import sand from "@/assets/images/sand.jpg";
import pencil from "@/assets/images/pencil.jpg";
import smartphone from "@/assets/images/smartphone.jpg";
import ladybug from "@/assets/images/ladybug.jpg";
import sunflowerSeed from "@/assets/images/sunflower-seed.jpg";
import coffeeBean from "@/assets/images/coffee-bean.jpg";
import penny from "@/assets/images/penny.jpg";
import egg from "@/assets/images/egg.jpg";
import hummingbird from "@/assets/images/hummingbird.jpg";
import basketball from "@/assets/images/basketball.jpg";
import bowlingPin from "@/assets/images/bowling-pin.jpg";
import cheetah from "@/assets/images/cheetah.jpg";
import woman from "@/assets/images/woman.jpg";
import vwBeetle from "@/assets/images/vw-beetle.jpg";
import giraffe from "@/assets/images/giraffe.jpg";
import oakTree from "@/assets/images/oak-tree.jpg";
import blueWhale from "@/assets/images/blue-whale.jpg";
import boeing747 from "@/assets/images/boeing-747.jpg";
import statueOfLiberty from "@/assets/images/statue-of-liberty.jpg";
import gatewayArch from "@/assets/images/gateway-arch.jpg";
import burjKhalifa from "@/assets/images/burj-khalifa.jpg";
import kentuckyDerby from "@/assets/images/kentucky-derby.jpg";
import centralPark from "@/assets/images/central-park.jpg";
import vegasStrip from "@/assets/images/vegas-strip.jpg";
import mountEverest from "@/assets/images/mount-everest.jpg";
import marianaTrench from "@/assets/images/mariana-trench.jpg";
import rhodeIsland from "@/assets/images/rhode-island.jpg";
import space from "@/assets/images/space.jpg";
import grandCanyon from "@/assets/images/grand-canyon.jpg";
import indianapolis from "@/assets/images/indianapolis.jpg";
import california from "@/assets/images/california.jpg";
import pluto from "@/assets/images/pluto.jpg";
import mars from "@/assets/images/mars.jpg";
import nyToSydney from "@/assets/images/ny-to-sydney.jpg";
import wrapEarth from "@/assets/images/wrap-earth.jpg";
import neptune from "@/assets/images/neptune.jpg";
import saturn from "@/assets/images/saturn.jpg";
import proximaCentauri from "@/assets/images/proxima-centauri.jpg";
import moon from "@/assets/images/moon.jpg";

const comparisons = [
  { text: "", img: image1 },
  { text: "The thickness of a strand of human hair.", img: hair },
  { text: "The width of a grain of sand.", img: sand },
  { text: "The width of a pencil's tip.", img: pencil },
  { text: "as thick as a spaghetti", img: smartphone },
  { text: "The height of a ladybug.", img: ladybug },
  { text: "The thickness of a sunflower seed.", img: sunflowerSeed },
  { text: "The length of a coffee bean.", img: coffeeBean },
  { text: "The width of a penny.", img: penny },
  { text: "The height of a chicken egg.", img: egg },
  { text: "It's now the height of a hummingbird.", img: hummingbird },
  { text: "The height of a basketball.", img: basketball },
  { text: "The height of a bowling pin", img: bowlingPin },
  { text: "The height of a cheetah", img: cheetah },
  { text: "It's now the height of an average woman.", img: woman },
  { text: "The length of a Volkswagen Beetle.", img: vwBeetle },
  { text: "The height of a giraffe.", img: giraffe },
  { text: "About the height of an oak tree.", img: oakTree },
  { text: "The length of a blue whale.", img: blueWhale },
  { text: "The wingspan of a Boeing 747.", img: boeing747 },
  { text: "About the height of the Statue of Liberty.", img: statueOfLiberty },
  { text: "About the height of the Gateway Arch.", img: gatewayArch },
  { text: "It's now as tall as the Burj Khalifa.", img: burjKhalifa },
  { text: "The length of the Kentucky Derby.", img: kentuckyDerby },
  { text: "The length of Central Park.", img: centralPark },
  { text: "The length of the Las Vegas Strip.", img: vegasStrip },
  { text: "Taller than Mount Everest.", img: mountEverest },
  { text: "Deeper than the Mariana Trench.", img: marianaTrench },
  { text: "About the length of Rhode Island.", img: rhodeIsland },
  { text: "The altitude at which space begins.", img: space },
  { text: "It's now as long as the Grand Canyon.", img: grandCanyon },
  { text: "500 laps around Indianapolis Motor Speedway.", img: indianapolis },
  { text: "Longer than California.", img: california },
  { text: "Longer than the diameter of Pluto.", img: pluto },
  { text: "About the diameter of Mars.", img: mars },
  { text: "The distance from New York to Sydney.", img: nyToSydney },
  { text: "Tall enough to wrap around the Earth.", img: wrapEarth },
  { text: "Longer than the diameter of Neptune.", img: neptune },
  { text: "The diameter of Saturn without its rings.", img: saturn },
  {
    text: "The diameter of Proxima Centauri, a red star.",
    img: proximaCentauri,
  },
  {
    text: "Congratulations, after only 42 folds your piece of paper has reached the moon!",
    img: moon,
  },
];
const fold = () => {
  foldCount.value++;
  thickness.value *= 2;
  updateUnit();
  updateComparison();
};

const unfold = () => {
  if (foldCount.value > 0) {
    foldCount.value--;
    thickness.value /= 2;
    updateUnit();
    updateComparison();
  }
};

const updateUnit = () => {
  if (thickness.value >= 1000 && unit.value === "m") {
    thickness.value /= 1000;
    unit.value = "km";
  } else if (thickness.value >= 100 && unit.value === "cm") {
    thickness.value /= 100;
    unit.value = "m";
  } else if (thickness.value >= 10 && unit.value === "mm") {
    thickness.value /= 10;
    unit.value = "cm";
  } else if (thickness.value < 1 && unit.value !== "mm") {
    if (unit.value === "cm") {
      thickness.value *= 10;
      unit.value = "mm";
    } else if (unit.value === "m") {
      thickness.value *= 100;
      unit.value = "cm";
    } else if (unit.value === "km") {
      thickness.value *= 1000;
      unit.value = "m";
    }
  }
};

const updateComparison = () => {
  const comparison = comparisons[foldCount.value];
  comparisonText.value = comparison.text;
  comparisonImage.value = comparison.img;
};
</script>

<template>
  <div class="container">
    <h1 class="title">Paper</h1>
    <div>
      <h2>{{ foldCount }} folds</h2>
      <img
        :src="comparisonImage"
        alt="Comparison Image"
        class="comparison-image"
      />
      <p>Your paper is now {{ thickness.toFixed(1) }} {{ unit }} Tall.</p>
      <p style="font-weight: 600" class="description">{{ comparisonText }}</p>
      <button @click="unfold" :disabled="foldCount === 0" class="unfold-button">
        Unfold
      </button>
      <button @click="fold" :disabled="foldCount >= 42" class="fold-button">
        Fold
      </button>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  line-height: 1.6em;
}
.container div {
  background: #fff;
  padding: 20px;
}
.container p {
  font-weight: 500;
  font-size: 18px;
}
.container img {
  max-width: 100%;
  height: 300px;
  object-fit: cover;
  margin-block: 10px;
  user-select: none;
  overflow: hidden;
}
h2 {
  font-size: 40px;
  margin: 10px 0 20px 0;
}

.title {
  text-align: center;
  font-size: 32px;
  font-weight: 700;
  background: #fff;
  padding: 30px 20px;
  margin-bottom: 10px;
  line-height: 1.6em;
}

.description {
  margin: 10px 0 20px 0;
}
.thickness {
  font-size: 18px;
  color: #777;
  margin-bottom: 20px;
}

button {
  margin: 3px;
  padding: 12px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
  transition: background-color 0.3s, transform 0.3s;
  user-select: none;
}

.unfold-button {
  background-color: #f53b57;
  color: white;
}

.unfold-button:hover {
  background-color: #e53935;
  transform: scale(1.05);
}

.unfold-button:disabled {
  background-color: #f1f2f6;
  color: #333;
  cursor: not-allowed;
}

.fold-button {
  background-color: #05c46b;
  color: white;
}

.fold-button:hover {
  background-color: #04b44d;
  transform: scale(1.05);
}

.fold-button:disabled {
  background-color: #f1f2f6;
  color: #333;
  cursor: not-allowed;
}
</style>
