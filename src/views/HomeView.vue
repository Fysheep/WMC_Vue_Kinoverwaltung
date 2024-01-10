
<script lang="ts">

export default {
   components: {
   },
   data() {
      return {
         data: [
            { id: "1", name: "Apollo" },
            { id: "2", name: "Wienaberg" }

         ] as Array<
            { id: string, name: string }
         >
      }
   },
   methods: {
      fieldConverter(val: string) {
         const res = val.replace(/([A-Z])/g, ' $1').split("");
         res.splice(0, 1, val.split("")[0].toUpperCase())

         return res.join("")
      },
      cellConverter(val: any) {
         if (typeof (val) == "object") return (val as Date).toLocaleDateString()
         return val
      }
   },
   computed: {
      columns() {
         let arr = [] as Array<string>;
         for (let a in this.data[0]) arr.push(a)
         return arr;
      }
   },
   mounted() {

   }
}
</script>

<template>
   <div class="d-flex">
      <div id="TableContainer">
         <table>
            <tr>
               <td :key="name" v-for="name in columns">
                  {{ fieldConverter(name) }}
               </td>
            </tr>
            <tr :key="el.id" v-for=" el  in  data" @click=" $router.push(`/edit?id=${el.id}`)">
               <td :key="name" v-for=" (name) in columns">
                  {{ cellConverter((el as any)[name]) }}
               </td>
            </tr>
         </table>
      </div>

   </div>
</template>

<style scoped>
table {
   border-collapse: collapse;
}

tr:nth-child(1) {
   font-weight: 900;
}

tr {
   transition-duration: 200ms;
   outline: var(--outline-color) 1px solid;
   background-color: var(--bg-color);
}

tr:not(:nth-child(1)):hover {
   filter: drop-shadow(5px 5px 5px gray) invert(0.8);
   cursor: pointer;
}

td {
   width: 150px;
   border: 1px solid var(--outline-color);
   padding: 0.25rem;
}

#TableContainer {
   max-height: calc(100vh - var(--Nav-Height) - 4rem);
   overflow: auto auto;
   width: fit-content;
}
</style>