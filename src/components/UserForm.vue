<template>
  <v-form ref="form" v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field
            v-model="width"
            :rules="numberRule"
            label="Width"
            required
          ></v-text-field>
        </v-col>

        <v-col cols="12" sm="6">
          <v-text-field
            v-model="height"
            :rules="numberRule"
            label="Height"
            required
          ></v-text-field>
        </v-col>
      </v-row>
      <v-autocomplete
        v-model="fabric"
        :items="fabrics"
        :rules="[(v) => !!v || 'Item is required']"
        label="Fabric"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="color"
        :items="colors"
        :rules="[(v) => !!v || 'Item is required']"
        label="Color"
        required
        item-text="name"
        item-value="name"
      >
        <template slot="item" slot-scope="data">
          <!-- Divider and Header-->
          <template v-if="typeof data.item !== 'object'">
            <v-list-item-content v-text="data.item" />
          </template>

          <template v-else>
            <!-- <v-list-item-content>
              <v-list-item-title v-html="data.item.name" />
              <div class="colors"></div>
            </v-list-item-content> -->

            <div class="color-item-container">
              <div>{{ data.item.name }}</div>
              <div
                class="colors"
                :style="{ backgroundColor: data.item.color }"
              ></div>
            </div>
          </template>
        </template>
      </v-autocomplete>

      <v-autocomplete
        v-model="drive"
        :items="drives"
        :rules="[(v) => !!v || 'Item is required']"
        label="Drive"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="position"
        :items="positions"
        :rules="[(v) => !!v || 'Item is required']"
        label="Drive chain position"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="mechanism"
        :items="mechanisms"
        :rules="[(v) => !!v || 'Item is required']"
        label="Drive mechanism"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="bracket"
        :items="brackets"
        :rules="[(v) => !!v || 'Item is required']"
        label="Length Brackets"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="colorLong"
        :items="colorLongs"
        :rules="[(v) => !!v || 'Item is required']"
        label="Color long brackets"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="wallType"
        :items="wallTypes"
        :rules="[(v) => !!v || 'Item is required']"
        label="Type of wall or ceiling plugs"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="fabricDrop"
        :items="fabricDrops"
        :rules="[(v) => !!v || 'Item is required']"
        label="Fabric drop"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="counterweight"
        :items="counterweights"
        :rules="[(v) => !!v || 'Item is required']"
        label="Lower counterweight"
        required
        item-text="name"
        item-value="name"
      >
        <template slot="item" slot-scope="data">
          <!-- Divider and Header-->
          <template v-if="typeof data.item !== 'object'">
            <v-list-item-content v-text="data.item" />
          </template>

          <template v-else>
            <v-list-item-content>
              <v-list-item-title v-html="data.item.name" />
            </v-list-item-content>
          </template>
        </template>
      </v-autocomplete>

      <v-autocomplete
        v-model="metal"
        :items="metals"
        :rules="[(v) => !!v || 'Item is required']"
        label="Metal or PVC chain?"
        required
      ></v-autocomplete>

      <v-autocomplete
        v-model="chain"
        :items="chains"
        :rules="[(v) => !!v || 'Item is required']"
        label="Chain counterweight"
        required
      ></v-autocomplete>
      <v-btn color="primary" @click="okay" :disabled="!valid"> Okay </v-btn>
    </v-container>
  </v-form>
</template>

<script>
export default {
  name: "UserForm",

  data: () => ({
    valid: true,
    width: 60,
    height: 60,
    numberRule: [
      (v) => !!v || "This field is required!",
      (v) => /^-?\d*\.?\d*$/.test(v) || "This field is should be number!",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    fabric: null,
    fabrics: ["Zenit", "Loneta resinada", "Shantung", "Lino", "Penélope"],
    color: null,
    colors: [
      {
        header: "BLANCOS",
      },
      {
        name: "Blanco nuclear",
        color: "#ffffff",
      },
      {
        name: "Blanco roto",
        color: "#ebebe7",
      },
      { divider: true },
      {
        header: "BEIGES Y MARRONES",
      },
      {
        name: "Beige claro",
        color: "#e8e3d3",
      },
      {
        name: "Beige",
        color: "#e3dbc3",
      },
      {
        name: "Marrón yute",
        color: "#baaf99",
      },
      {
        name: "Arena",
        color: "#bfa890",
      },
      {
        name: "Beige grisaceo",
        color: "#a39b8e",
      },
      {
        name: "Ocre claro",
        color: "#ab8b6b",
      },
      {
        name: "Marrón tierra",
        color: "#7d6455",
      },
      {
        name: "Marrón oscuro",
        color: "#524d4b",
      },
      {
        name: "Marrón rojizo",
        color: "#7c4148",
      },
      { divider: true },
      {
        header: "GRISES Y NEGRO",
      },
      {
        name: "Gris perla",
        color: "#c1c1b8",
      },
      {
        name: "Gris piedra",
        color: "#bdb7ae",
      },
      {
        name: "Gris plata",
        color: "#afb3b4",
      },
      {
        name: "Gris medio",
        color: "#878e93",
      },
      {
        name: "Gris oscuro",
        color: "#727476",
      },
      {
        name: "Gris basalto",
        color: "#54585a",
      },
      {
        name: "Negro noche",
        color: "#3b3c3c",
      },
      { divider: true },
      {
        header: "AZULES",
      },
      {
        name: "Azul vaquero",
        color: "#40486d",
      },
      {
        name: "Azul mar profundo",
        color: "#424e60",
      },
      {
        name: "Azul zafiro",
        color: "#46648f",
      },
      {
        name: "Azul celeste",
        color: "#86a5bf",
      },
      { divider: true },
      {
        header: "VERDES",
      },
      {
        name: "Verde salvia",
        color: "#b2c7a8",
      },
      {
        name: "Verde trébol",
        color: "#1c885a",
      },
      {
        name: "Verde alga",
        color: "#436058",
      },
      {
        name: "Verde helecho",
        color: "#94b270",
      },
      {
        name: "Verde oliva",
        color: "#7a8567",
      },
      {
        name: "Verde lima",
        color: "#ccca62",
      },
      { divider: true },
      {
        header: "SALMÓN, AMARILLOS Y NARANJAS",
      },
      {
        name: "Salmón pálido",
        color: "#e29e79",
      },
      {
        name: "Amarillo trigo",
        color: "#efd9ab",
      },
      {
        name: "Amarillo pálido",
        color: "#F0D16B",
      },
      {
        name: "Amarillo limón",
        color: "#edc252",
      },
      {
        name: "Calabaza",
        color: "#D17D4F",
      },
      { divider: true },
      {
        header: "ROSAS, VIOLETAS Y ROJOS",
      },
      {
        name: "Rojo",
        color: "#bc2c42",
      },
      {
        name: "Rosa violeta intenso",
        color: "#a24777",
      },
      {
        name: "Rosa violeta pálido",
        color: "#b68696",
      },
      {
        name: "Rosa pétalo",
        color: "#e2bac6",
      },
      {
        name: "Lavanda",
        color: "#a5a2be",
      },
      {
        name: "Malva",
        color: "#816983",
      },
    ],
    drive: null,
    drives: ["With chain", "With motor"],
    position: null,
    positions: ["Left", "Right"],
    mechanism: null,
    mechanisms: ["Fluid drive", "Fluid + drive"],
    bracket: null,
    brackets: ["Normal wall or ceiling brackets", "Long wall brackets"],
    colorLong: null,
    colorLongs: ["White", "Beige", "Grey", "Black", "Brown", "Metallic"],
    wallType: null,
    wallTypes: [
      "Universal dowels",
      "Fisher Duoblade plasterboard dowels (4 pcs)",
    ],
    fabricDrop: null,
    fabricDrops: [
      "Fabric drop behind the tube",
      "Fabric drop in front of tube",
    ],
    counterweight: null,
    counterweights: [
      { header: "Standard counterweights" },
      { name: "Concealed oval" },
      { name: "Seen oval beige" },
      { header: "Decorative counterweights" },
      { name: "Silver sandpaper oval view" },
      { name: "Champagne oval view" },
      { name: "Rectangular silver sandpaper view" },
      { name: "Rectangular champagne view" },
    ],
    metal: null,
    metals: ["PVC chain", "Metal chain"],
    chain: null,
    chains: ["Normal counterweight", "Child safety chain tensioner"],
  }),

  methods: {
    okay() {
      console.log("~~~~OKAY~~~~");
    },
  },
};
</script>

<style lang="scss">
.v-form {
  padding: 30px;
}

.color-item-container {
  display: flex;
  align-items: center;
}

.colors {
  width: 20px;
  height: 20px;
  background-color: red;
  margin-left: 20px;
}
</style>
