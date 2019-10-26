<template>
  <div id="app">
    {{ info }}
  </div>
</template>

<script>
import axios from 'axios'

export default({ // eslint-disable-line no-new
  data () {
    return {
      info: null,
      state: 'Y@&E#^IDB#YBDYD@(SN@'
    }
  },
  mounted () {
    axios({
      method: 'get',
      url: 'https://api.tradier.com/v1/markets/quotes',
      headers: {
        Authorization: 'Bearer q1MudAtYloMpux8HbD7PMt2pSG6l',
        Accept: 'application/json'
      },
      params: {
        symbols: 'AAPL',
        greeks: 'false'
      },
      transformRequest: [(data, headers) => { delete headers.common.ContenType}]
    })
      .then(response => (this.info = response))
  }
})
</script>

