<template>
  <div v-for="d in dataApi">
    <h1>
      {{ d.name }}
    </h1>
    <p>
      {{ d.origin.name }}
    </p>
    <p>
      episodes: {{ d.episode.length.toString() }}
    </p>
    <a href="d.url"> {{ d.url }} </a>
  </div>
</template>

<script>

export default{
  name: 'HelloWorld',
  data(){
    return{
      dataApi: []
    }
  },
  methods: {
    getCharacter : function (done) {   
      const results = fetch("https://rickandmortyapi.com/api/character")
      
      results
            .then(response => response.json())
            .then(data => {
              done(data)
            })
    }
  },
  mounted(){
    this.getCharacter(data => {
      this.dataApi = data.results
    })
  },
  computed:{
    // dataApi(){
    //   return this.getCharacter(data => {
    //       return (data)
    //       console.log(data)
    //   }) 
    // }
  }
  
}

</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
