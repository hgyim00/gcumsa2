<template>

    <v-card outlined>
        <v-card-title>
            HelloStatus # {{$route.params.id }}
        </v-card-title>

        <v-card-text>
            <div>
                <Number label="Helloid" v-model="item.helloid" :editMode="editMode" @change="change" />
            </div>
            <div>
                <Number label="Worldid" v-model="item.worldid" :editMode="editMode" @change="change" />
            </div>
        </v-card-text>
    </v-card>

</template>

<script>
  const axios = require('axios').default;

  export default {
    name: 'HelloStatusViewDetail',
    props: {
      value: Object,
    },
    data: () => ({
        item : [],
    }),
    async created() {
      var params = this.$route.params;
      var temp = await axios.get(axios.fixUrl('/helloStatuses/' + params.id))

      this.item = temp.data;

    },
    methods: {
    }
  }
</script>

