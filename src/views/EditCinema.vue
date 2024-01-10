<script lang="ts">

export default {
  data() {
    return {
      data: [
        { id: "1", name: "Apollo" },
        { id: "2", name: "Wienaberg" }

      ] as Array<
        { id: string, name: string }
      >,
      cinema: undefined as any
    }

  },
  mounted() {
    this.cinema = this.data.find(f => f.id.toString() == this.$route.query.id?.toString());
    console.log(this.$route.query.id?.toString())
  }
}
</script>

<template>
  <div v-if="!cinema">

    <div class="alert">
      <span class="alerttitle">Nicht Gefunden</span> <br>
      Das Finding wurde nicht gefunden, bitte kehren Sie zurück zur
      <RouterLink to="/" class="rLink">Startseite</RouterLink>
    </div>

  </div>
  <div v-else>
    <!-- DESIGN benötigt Start -->
    {{ cinema.id }}
    {{ cinema.name }}
    <!-- DESIGN benötigt End -->
  </div>
</template>

<style scoped>
.alert {
  background-color: rgb(150, 20, 20);
  color: white;
  padding: 1rem;
  position: absolute;
  border-radius: 1rem;
  margin-top: auto;
  margin-left: auto;
  width: fit-content;
  height: fit-content;
  text-align: center;
  font-size: large;
  font-weight: bold;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.alerttitle {
  font-size: xx-large;
}

.rLink {
  color: darkkhaki;
}

.Title {
  font-weight: bold;
}
</style>