<script lang="ts">

const RSS_URL = "http://www.ruanyifeng.com/blog/atom.xml";
let xmlText ;

const url = RSS_URL;

fetch(url)
  .then(response => response.text())
  .then(data => {
    console.log(xmlText = data); // This should output the response body as text
  })
  .catch(error => {
    console.error(error);
  });



</script>

<div id="hello">
    {xmlText}
</div>
<!-- 
<style lang="scss">
    #hello {
        margin: 20px;
        div {
            margin-bottom: 10px;
        }
    }
    .__text-right {
        text-align: right;
    }
</style> -->
