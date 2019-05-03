<script>
import Vue from 'vue'
import applicationConstants from '@/components/constants/ApplicationConstants'

export default {
  name: 'RestService',
  methods: {
    getUsers () {
      return Vue.http.get(applicationConstants.baseUrl + 'api/user')
    }
  }
}
</script>
