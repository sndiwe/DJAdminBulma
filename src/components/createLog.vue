<template>
  <v-app>
      <v-form v-model="valid">
      <!-- <v-container fluid> -->
        <v-layout align-center justify-center row>
                  <v-flex xs8>
                    <v-text-field
                      name="input-3"
                      label="Service Name"
                      color="pink"
                      value=""
                      v-model="formModel.name"
                    ></v-text-field>
                    <v-text-field
                      name="input-3"
                      label="Location"
                      color="pink"
                      value=""
                      v-model="formModel.location"
                    ></v-text-field>
                    <v-dialog
                      ref="dialog"
                      persistent
                      v-model="modal"
                      lazy
                      full-width
                      width="290px"
                      :return-value.sync="startDate"
                    >
                      <v-text-field
                        slot="activator"
                        label="Start Time"
                        v-model="startDate"
                        prepend-icon="event"
                        readonly
                      ></v-text-field>
                      <v-time-picker v-model="startDate" scrollable>
                        <v-spacer></v-spacer>
                        <v-btn flat color="primary" @click="startModal = false">Cancel</v-btn>
                        <v-btn flat color="primary" @click="$refs.dialog.save(startDate),checkIt($refs.dialog)">OK</v-btn>
                      </v-time-picker>
                    </v-dialog>
                    <v-dialog
                      ref="dialog"
                      persistent
                      v-model="modal"
                      lazy
                      full-width
                      width="290px"
                      :return-value.sync="endDate"
                    >
                      <v-text-field
                        slot="activator"
                        label="End Time"
                        v-model="endDate"
                        prepend-icon="event"
                        readonly
                      ></v-text-field>
                      <v-time-picker v-model="endDate" scrollable>
                        <v-spacer></v-spacer>
                        <v-btn flat color="primary" @click="modal = false">Cancel</v-btn>
                        <v-btn flat color="primary" @click="$refs.dialog.save(endDate),checkIt($refs.dialog)">OK</v-btn>
                      </v-time-picker>
                    </v-dialog>
                    <v-select
                      :items="serviceTypes"
                      v-model="serviceType"
                      label="Service Type"
                      item-text="type"
                      item-value="abbr"                      
                      class="input-group--focused mb-3"
                    ></v-select>
                     <v-spacer></v-spacer>
         
                  </v-flex>
                  
        </v-layout>
             <div class="form-btn">
      <v-btn @click="submit" color="success">Submit</v-btn>
      <v-btn @click="clear" color="error">Clear</v-btn>
    </div>
      </v-form>
      <!-- </v-container> -->
  </v-app>
</template>

<script>
export default {
  name: 'createLog',
  data () {
    return {
      startDate: null,
      endDate: null,
      menu: false,
      startModal: false,
      modal: false,
      serviceType: null,
      items: [],
      serviceTypes: [
        {
          'type': 'Voluntary',
          'abbr': 'VO'
        },
        {
          'type': 'Mandantory',
          'abbr': 'MA'
        },
      ],
      valid: true,
      formModel: {
        name: null,
        location: null
      }
    };
  },
  methods: {
    goHome () {
      this.$router.push({ path: '/' });
    },
    checkIt (item) {
      console.log(item);
    },
    submit () {
      this.$validator.validateAll();
    },
    clear () {
      this.formModel = {};
      this.$validator.reset();
    }    
  }
};
</script>
<style scoped lang="css">
  h1 {
    font-size: 150px;
    line-height: 150px;
    font-weight: 700;
    color: #252932;
    text-shadow: rgba(61, 61, 61, 0.3) 1px 1px, rgba(61, 61, 61, 0.2) 2px 2px, rgba(61, 61, 61, 0.3) 3px 3px;    
  }
</style>