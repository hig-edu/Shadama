# Shadama

<script>
  var container = lively.query(this, "lively-container")
  var rootURL = container.getURL().toString()
</script>

<link rel="stylesheet" type="text/css" href="shadama.css">
<link rel="stylesheet" type="text/css" href="codemirror/codemirror.css">

<textarea style="float: left" id="code"></textarea>

<div style="float: left">
              <canvas id="shadamaCanvas"></canvas>
</div>
<div style="float: left" id="controlBox">
  <select id="myDropdown" class="dropdown-content"></select>
  <hr>
  <div id="watcherList"></div>
  <hr>
  <div id="envList"></div>
</div>
<div id="readout"></div>

                
<script>

this.parentElement.addEventListener("keydown", evt => {
  if (evt.ctrlKey && evt.key == "s") {
    evt.stopPropagation()
    evt.preventDefault()
    lively.notify("NOT SAVED")  
  }
});


(async () => {
  var baseURL = "https://lively-kernel.org/lively4/shadama/"
  
  window.ohm = (await System.import(baseURL + "thirdparty/ohm.min.js")).default
  await lively.loadJavaScriptThroughDOM("shadamaPapa", baseURL + "thirdparty/papaparse.min.js")
  await lively.loadJavaScriptThroughDOM("shadamaShadama", baseURL + "shadama.js")
  await lively.loadJavaScriptThroughDOM("shadamaTest", baseURL +  "shadama-tests.js")
  window.shadama = ShadamaFactory(null, 2, this.parentElement, "13-Ribbons.shadama", true, this.parentElement, rootURL);
})()
</script>
          
<!-- <button onclick="shadama.goFullScreen()">Full Screen</button> -->
<!-- <canvas id="debugCanvas1"></canvas> -->
