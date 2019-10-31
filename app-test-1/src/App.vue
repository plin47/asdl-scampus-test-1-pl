<template>
  <v-app>

    <v-app-bar app
               dense
               color="indigo lighten-2"
    >
        <v-toolbar-title>
<!--            <span class="font-weight-light"> Heat Map Visualization</span>-->
            <span class="ma-1"> Heat Map Visualization</span>
        </v-toolbar-title>

        <v-btn tile ripple="false" color="transparent" depressed dark height="48">
            <v-icon left>{{icon_1}}</v-icon>
            TO TON
        </v-btn>
        <v-btn  tile ripple="false" color="transparent" depressed dark height="48">
            TO GPM
            <v-icon right>{{icon_1}}</v-icon>
        </v-btn>

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

    </v-app-bar>

    <v-content>
		<v-toolbar
                dense
                flat
        >
            <v-card flat>
                <v-tabs>
                    <v-tabs-slider color="transparent"></v-tabs-slider>
                    <v-tab>ID</v-tab>
                    <v-tab>BUILDING</v-tab>
                    <v-tab>GROUP</v-tab>
                    <v-tab>AVG. TON</v-tab>
                </v-tabs>
            </v-card>

		</v-toolbar>

    </v-content>

  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import { mdiUpdate } from '@mdi/js';
import { mdiStepForward } from '@mdi/js';
import { mdiStepBackward } from '@mdi/js';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
      icon_1: mdiUpdate,
      icon_2: mdiStepForward,
      icon_3: mdiStepBackward,
      dialog: false,
      picker: new Date().toISOString().substr(0, 10),
  }),
};
</script>
