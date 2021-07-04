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

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="fabric"
            :items="fabrics"
            :rules="[(v) => !!v || 'Item is required']"
            label="Fabric"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
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
                <v-list-item-content>
                  <v-list-item-title v-html="data.item.name" />
                </v-list-item-content>
              </template>
            </template>
          </v-autocomplete>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="drive"
            :items="drives"
            :rules="[(v) => !!v || 'Item is required']"
            label="Drive"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="position"
            :items="positions"
            :rules="[(v) => !!v || 'Item is required']"
            label="Drive chain position"
            required
          ></v-autocomplete>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="mechanism"
            :items="mechanisms"
            :rules="[(v) => !!v || 'Item is required']"
            label="Drive mechanism"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="bracket"
            :items="brackets"
            :rules="[(v) => !!v || 'Item is required']"
            label="Length Brackets"
            required
          ></v-autocomplete>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="colorLong"
            :items="colorLongs"
            :rules="[(v) => !!v || 'Item is required']"
            label="Color long brackets"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="wallType"
            :items="wallTypes"
            :rules="[(v) => !!v || 'Item is required']"
            label="Type of wall or ceiling plugs"
            required
          ></v-autocomplete>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="fabricDrop"
            :items="fabricDrops"
            :rules="[(v) => !!v || 'Item is required']"
            label="Fabric drop"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
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
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="metal"
            :items="metals"
            :rules="[(v) => !!v || 'Item is required']"
            label="Metal or PVC chain?"
            required
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="6">
          <v-autocomplete
            v-model="chain"
            :items="chains"
            :rules="[(v) => !!v || 'Item is required']"
            label="Chain counterweight"
            required
          ></v-autocomplete>
        </v-col>
      </v-row>

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
      (v) =>
        (v && typeof v === "number") || "This field should be number value",
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
      },
      {
        name: "Blanco roto",
      },
      { divider: true },
      {
        header: "BEIGES Y MARRONES",
      },
      {
        name: "Beige claro",
      },
      {
        name: "Beige",
      },
      {
        name: "Marrón yute",
      },
      {
        name: "Arena",
      },
      {
        name: "Beige grisaceo",
      },
      {
        name: "Ocre claro",
      },
      {
        name: "Marrón tierra",
      },
      {
        name: "Marrón oscuro",
      },
      {
        name: "Marrón rojizo",
      },
      { divider: true },
      {
        header: "GRISES Y NEGRO",
      },
      {
        name: "Gris perla",
      },
      {
        name: "Gris piedra",
      },
      {
        name: "Gris plata",
      },
      {
        name: "Gris medio",
      },
      {
        name: "Gris oscuro",
      },
      {
        name: "Gris basalto",
      },
      {
        name: "Negro noche",
      },
      { divider: true },
      {
        header: "AZULES",
      },
      {
        name: "Azul vaquero",
      },
      {
        name: "Azul mar profundo",
      },
      {
        name: "Azul zafiro",
      },
      {
        name: "Azul celeste",
      },
      { divider: true },
      {
        header: "VERDES",
      },
      {
        name: "Verde salvia",
      },
      {
        name: "Verde trébol",
      },
      {
        name: "Verde alga",
      },
      {
        name: "Verde helecho",
      },
      {
        name: "Verde oliva",
      },
      {
        name: "Verde lima",
      },
      { divider: true },
      {
        header: "SALMÓN, AMARILLOS Y NARANJAS",
      },
      {
        name: "Salmón pálido",
      },
      {
        name: "Amarillo trigo",
      },
      {
        name: "Amarillo pálido",
      },
      {
        name: "Amarillo limón",
      },
      {
        name: "Calabaza",
      },
      { divider: true },
      {
        header: "ROSAS, VIOLETAS Y ROJOS",
      },
      {
        name: "Rojo",
      },
      {
        name: "Rosa violeta intenso",
      },
      {
        name: "Rosa violeta pálido",
      },
      {
        name: "Rosa pétalo",
      },
      {
        name: "Lavanda",
      },
      {
        name: "Malva",
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
</style>
