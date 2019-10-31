<template>
  <v-app>
    <v-app-bar app dense flat color="indigo lighten-2">
        <v-toolbar-title>
            <span class="ma-1"> Heat Map Visualization</span>
        </v-toolbar-title>

        <v-tooltip bottom>
            <template v-slot:activator="{ on }">
                <v-btn tile ripple="false" color="transparent" depressed dark height="48" v-on="on">
                    <v-icon left>{{icon_1}}</v-icon>
                    TO TON
                </v-btn>
            </template>
            <span>Redirect to TON heatmap</span>
        </v-tooltip>

        <v-tooltip bottom>
            <template v-slot:activator="{ on }">
                <v-btn  tile ripple="false" color="transparent" depressed dark height="48" v-on="on">
                    TO GPM
                    <v-icon right>{{icon_1}}</v-icon>
                </v-btn>
            </template>
            <span>Redirect to GPM heatmap</span>
        </v-tooltip>

        <v-btn class="ml-7" tile ripple="false" color="transparent" depressed dark height="48" @click.stop="dialog = true">
            <v-icon left>{{icon_3}}</v-icon>
            START
            <v-dialog v-model="dialog" max-width="290">
                <v-date-picker v-model="date" no-title @input="menu1 = false"></v-date-picker>
            </v-dialog>
        </v-btn>
        <v-btn tile ripple="false" color="transparent" depressed dark height="48" @click.stop="dialog = true">
            END
            <v-icon right>{{icon_2}}</v-icon>
            <v-dialog v-model="dialog" max-width="290">
                <v-date-picker v-model="date" no-title @input="menu1 = false"></v-date-picker>
            </v-dialog>
        </v-btn>

        <v-spacer></v-spacer>

        <v-tooltip bottom>
            <template v-slot:activator="{ on }">
                <v-btn tile ripple="false" color="transparent" depressed dark height="48" v-on="on">
                    <v-icon left>{{icon_4}}</v-icon>
                    UPLOAD
                </v-btn>
            </template>
            <span>Upload csv to the database</span>
        </v-tooltip>
        <v-tooltip bottom>
            <template v-slot:activator="{ on }">
                <v-btn tile ripple="false" color="transparent" depressed dark height="48" v-on="on">
                    NULL BLDG
                    <v-icon right>{{icon_5}}</v-icon>
                </v-btn>
            </template>
            <span>Include /Exclude building with no data</span>
        </v-tooltip>
    </v-app-bar>

    <v-content>
        <v-toolbar elevation="0" class="font-weight-medium" color="white">
            <v-tabs>
                <v-tabs-slider color="transparent"></v-tabs-slider>
                <v-tab
                        v-for="item in items"
                        :key="item"
                        :ripple="false"
                >
                    {{ item }}
                </v-tab>
            </v-tabs>
        </v-toolbar>

        <v-card>

        </v-card>

    </v-content>
  </v-app>
</template>

<script>
    import Vue from 'vue'
    import HelloWorld from './components/HelloWorld';
    import { mdiUpdate } from '@mdi/js';
    import { mdiStepForward } from '@mdi/js';
    import { mdiStepBackward } from '@mdi/js';
    import { mdiUpload } from '@mdi/js';
    import { mdiClose } from '@mdi/js';

    import 'echarts/lib/chart/heatmap';

    export default {
      name: 'App',
      components: {
        HelloWorld,
      },

      data: () => ({
          icon_1: mdiUpdate,
          icon_2: mdiStepForward,
          icon_3: mdiStepBackward,
          icon_4: mdiUpload,
          icon_5: mdiClose,
          dialog: false,
          picker: new Date().toISOString().substr(0, 10),
          items: ['ID','BUILDING','GROUP','AVG'],
      }),
    };
</script>
