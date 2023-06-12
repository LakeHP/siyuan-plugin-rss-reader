<script lang="ts">

const RSS_URL = "http://www.ruanyifeng.com/blog/atom.xml";
let blog ;

import { parseString } from 'xml2js';

// Replace the URL with your own XML file URL
const url = RSS_URL;

fetch(url)
  .then(response => response.text())
  .then(xml => {
    parseString(xml, (err, result) => {
      if (err) {
        console.error(err);
        return;
      }
      console.log(result); // This should output a JavaScript object
    });
  })
  .catch(error => {
    console.error(error);
  });




</script>

<div id="hello">
    {blog}
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
