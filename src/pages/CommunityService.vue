<template>
  <v-app>
        <v-tabs icons-and-text centered dark color="cyan" @change="testIt">
        <v-tabs-slider color="black"></v-tabs-slider>
        <v-tab href="#tab-1">
            New
            <v-icon>create_new_folder</v-icon>
        </v-tab>
        <v-tab href="#tab-2">
            Existing
            <v-icon>edit</v-icon>
        </v-tab>
        <v-tab href="#tab-3">
            Future
            <v-icon>date_range</v-icon>
        </v-tab>
        <v-tab-item 
                  v-for="i in 3"
                  :key="i"
                  :id="'tab-' + i"
                >
                  <v-card flat >
                    <v-card-text><create-log></create-log></v-card-text>
                  </v-card>
                </v-tab-item>
        </v-tabs>    
  </v-app>
</template>

<script>
import createLog from '@/components/createLog';
import editLog from '@/components/editLog';
import futureLog from '@/components/futureLog';
export default { 
  components: {
    createLog,
    editLog,
    futureLog
  },
  data () {
    return {
      myComponent: createLog
    };
  },
  methods: {
    goHome () {
      this.$router.push({ path: '/' });
    },
    testClick () {
      console.log('Click');
    },
    testIt () {
      console.log('here');
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
