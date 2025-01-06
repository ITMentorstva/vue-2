<template>
  <p v-if="courseInfo[classNameLower]">Details: {{ className }} - {{ courseInfo[classNameLower].price }}&euro;</p>
  <p v-else>{{ className }}: Nemamo informacije za ovaj programerski jezik</p>
</template>


<script>

/**
 * Computed:
 *  const NAME = "Toma";
 *  const computedName = NAME.toLowerCase(); // vrednost od NAME koji je lowercase, modifikovani name
 *
 *  const num1 = 10;
 *  const num2 = 10;
 *
 *  const total = num1+num2; // computed zato sto je vrednost od num1+num2
 */

export default {
    name: "ClassInfoComponent",
    props: {
      className: {
        type: String,
        required: true,
      }
    },
    computed: {
      classNameLower() {
        return this.className.toLowerCase();
      }
    },
    data() {
      return {
        courseInfo: {
          reactjs: {
            price: 350,
            length: "3 months",
            numberOfLectures: 24
          },
          javascript: {
            price: 350,
            length: "3 months",
            numberOfLectures: 24
          },
          nodejs: {
            price: 350,
            length: "3 months",
            numberOfLectures: 24
          },
          vuejs: {
            price: 350,
            length: "3 months",
            numberOfLectures: 24
          },
        }
      }
    }
  }
</script>