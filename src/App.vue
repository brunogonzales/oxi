<template>
  <h1>Lugares donde recargan oxigeno durante la pandemia de COVID-19</h1>
  <div>
    <input
      type="text"
      v-model="search"
      placeholder="Busqueda por palabra claves"
    />
    <button @click="search = ''">X</button>
  </div>
  <p v-if="search">
    {{ filteredPlaces.length }} resultados para "{{ search }}"
  </p>

  <div v-for="place in filteredPlaces" :key="place.name">
    <h3>{{ place.name }}</h3>
    <p>{{ place.address }}</p>
    <p v-if="place.description">{{ place.description }}</p>
    <p>Contacto: {{ place.contactInfo }}</p>
    <p v-if="place.price">Precio: {{ place.price }}</p>
    <p v-if="place.openHours">Atencion: {{ place.openHours }}</p>
    <hr />
  </div>
  <footer>
    <a href="https://github.com/brunogonzales/oxi"
      >Editar esta pagina en GitHub</a
    >
  </footer>
</template>

<script>
export default {
  name: "App",
  computed: {
    filteredPlaces() {
      if (!this.search) return this.places;
      return this.places.filter(({ name, address, description }) => {
        console.log(name + address + description);
        return (name + address + description)
          .toLowerCase()
          .includes(this.search.toLowerCase());
      });
    },
  },
  data() {
    return {
      search: "",
      places: [
        {
          name: "OXIROMERO GROUP S.A.C",
          contactInfo: "012851961 – 947154437 -  947154357 - 990375572",
          openHours: "7:30am a 3:00pm",
          address:
            "Defensores de Lima 601 – Pamplona Alta (Salvador Allende - Pista Nueva) – SJM ",
          price: "S/.15.00",
          description:
            "Recarga hasta 5m3. Cola desde las 4:00am. Recarga de 10m3 con espera de 1 o 2 días.",
        },
        {
          name: "Oxígenos y Derivados S.R.L",
          contactInfo: "014466018 - 989302191",
          openHours:
            "L-V -> 9:00am a 3:30pm (2 a 3 hora de almuerzo). Sab -> 9:00am a 12:00pm",
          address: "Javier Gallardo Av. República de Panamá 5603 – Miraflores",
          price: "S/.17.00",
          description: "Solo recargan 2 m3 o 3 m3 por balón.",
        },
        {
          name: "ANTEROXIGENO",
          contactInfo: "943189437",
          openHours: "Mañana y Tardes",
          address: "Calle Virú 264, Altura Cd 29 Av. La Marina – San Miguel",
          price: null,
          description: null,
        },
        {
          name: "DIVERSAL",
          contactInfo: "Sr. Hugo Valdivia",
          openHours: "Mañanas",
          address:
            "Urb. Alameda Portuaria Mz E1 Lt 1. Cruce Faucett con Canta Callao – Callao",
          price: "S/ 15.00",
          description: "100 personas por día, Hasta 5 m3 ",
        },
        {
          name: "CRIOGAS COMERCIAL S.A.C",
          contactInfo:
            "014650080 - 998164653 -  99 816 4654 - Sr. Luis Barsalio",
          openHours: "Mañanas",
          address:
            "Av. Alfredo Palacios, cd 6, Mz B, Lt 8 (Cruce Jirón Supe a 100 metros del óvalo Urb. Centenario) – Callao",
          price: "S/ 15.00",
          description: "100 personas por día, Hasta 5 m3 ",
        },
        {
          name: "OXÍGENO SOLIDARIO",
          contactInfo: "924042712 - Sr. Roberto Fabian ",
          openHours: "A partir 4:00pm. Previa coordinación",
          address: "Centro de Lima / Espalda de Hosp. Layza",
          price: "S/ 30.00",
          description:
            "Se entrega al centro de acopio, tiempo de recarga 4-5 horas, Pago contra entrega en transferencia, Recarga de 10m3",
        },
        {
          name: "PRONASA SALUD (Cruz Verde)",
          contactInfo: "994226413 - 013856668 ",
          openHours: "Tarde",
          address: "Altura Puente Nuevo",
          price: "S/ 30.00",
          description: null,
        },
        {
          name: "Gases de Ma... Oxígeno Medicinal",
          contactInfo: "955542989",
          openHours: "8:00am a 5:30pm ",
          address:
            "Calle Manuel Arispe 375, La Chalaca – Callao (Cerca a Criogas Local Principal 237), Alt. Av. Argentina con Óvalo.",
          price: "S/ 30.00 (recargan solo si compran un producto de la tienda)",
          description:
            "Balón de 5 m3 -> S/ 5300,  Balón 1 m3 -> S/ 1800. Recarga a partir de 6 m3.",
        },
        {
          name: "Alquiler GAR INGENIEROS S.A.C ",
          contactInfo: "940609214",
          openHours: null,
          address:
            "Juan Miranda Av. Parque Block 29, Mz A, Lt 1, Dep.303, Urb. Los Eucaliptos – El Agustino.",
          description:
            "Balón 10 m3 lleno x 7 días -> S/ 1300. Balón de 8 m3 a 6 m3 x 7 días -> S/ 1000",
          price: "Llena primera vez, No hace recargas.",
        },
        {
          name: "Oxígeno para uso industrial: OXIGRAMA E.I.R.L ",
          contactInfo: "987203468",
          openHours: "24 horas",
          address:
            "Urb. 200 Millas Mz K, Lt7, Óvalo Cantolao, Entre Faucet y Gambeta",
          description: "Pago extra por servicio nocturno (cerrado – preguntar)",
          price: "S/30.00",
        },
        {
          name: "Oxígeno para uso industrial: OXIRED",
          contactInfo: "012914191 – 990774477 - Leonardo",
          openHours: "8:00am",
          address:
            "Av. Pachacutec Mz. 3 Lt. 1, Parque Industrial (con Av. El Sol), Villa El Salvador",
          description: "Preguntar si hay stock de oxígeno.",
          price: "S/20.00",
        },
        {
          name: "BALONES DE OXIGENOS AMERICANOS",
          contactInfo: "938415315 - 987111730 - 954775370",
          openHours: null,
          address: "Mz E lote 4 Pasaje Baquijano. Ref. frente de Minka",
          description: "Valvulas, Kit Completo, Capuchón estandar. Delivery",
          price: null,
        },
        {
          name: "OXIGENO GERLAD SANCHEZ",
          contactInfo: "947293731",
          openHours: null,
          address: null,
          description: "Venta de balones de oxigeno - Recargas",
          price: null,
        },
        {
          name: "OXIYACH",
          contactInfo: "968806404 - 936265566 - 955545111",
          openHours: null,
          address: null,
          description: "Recargas - Alquiler",
          price: null,
        },
        {
          name: "OXIGENO MEDICINAL - ASOC. DE LAS BIENAVENTURANZAS",
          contactInfo: "988818728 Alex Rodriguez - 964324694 Karina Castilla",
          openHours: null,
          address: null,
          description: "Recargas - Prestamos de Tanques de Oxigeno.",
          price: "COMPLETAMENTE GRATIS - SE ACEPTAN DONACIONES",
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.search {
  display: flex;
}
</style>
