<template>
  <div>
      <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="margin: auto; background: none; display: block; shape-rendering: auto;" width="100px" height="200px" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid">
      <circle cx="50" cy="50" fill="none" stroke="#e15b64" stroke-width="10" r="35" stroke-dasharray="164.93361431346415 56.97787143782138">
        <animateTransform attributeName="transform" type="rotate" repeatCount="indefinite" dur="1s" values="0 50 50;360 50 50" keyTimes="0;1"/>
      </circle>
      </svg>
  </div>
</template>
<script>
import axios from "axios"
export default {
  data (){
    return {
      id: this.$route.params.id
    }
  },
  async created(){
    const data = await axios.get(`${process.env.VUE_APP_API_URL}/${this.id}`)
        .then(response => {
          (response.data)
          // Redirect to URL data if found
          window.location.href = response.data
        })
        .catch(error => {
            console.log(error)
            // 404 if not
            this.$router.push('/pages/not-found')
        });
      console.log(data)
  }
}
</script>