<script lang="ts"> 
  import Dad2048 from "./lib/Dad2048.svelte";
  import PopDad from "./lib/PopDad.svelte";

  let image_url = "";

  let display_d1 = "block";
  let display_d2 = "block";
  let display_d3 = "block";

  function downloadExtension() {
    let n = data.length;
    let selected_index = (Math.random() * 1e10).toFixed(0) % n
    let selected_img = data[selected_index].image_url;
    
    image_url = selected_img;
  }

  function click_d1(d_name) {
    if(d_name === "1") {
      display_d1 = "block";
      display_d2 = display_d2 === "none" ? "block" : "none";
      display_d3 = display_d3 === "none" ? "block" : "none";
    }else if(d_name === "2") {
      display_d1 = display_d1 === "none" ? "block" : "none";
      display_d2 = "block";
      display_d3 = display_d3 === "none" ? "block" : "none";
    }else if(d_name === "3") {
      display_d1 = display_d1 === "none" ? "block" : "none";
      display_d2 = display_d2 === "none" ? "block" : "none";
      display_d3 = "block";
    }
  }
</script>

<body>
  <div class="container">
    <h1>Extension for Dad (ส่วนเสริมเพื่อพ่อ)</h1>
    <div style="display: flex; gap: 1rem; align-items: baseline;">
      <details style="display: {display_d1};">
        <summary on:click={() => click_d1("1")}>Features (?)</summary>
        <ul style="background-color: rgb(239, 239, 0); padding: 1rem 1.5rem">
          <li>เปลี่ยนรูปภาพในเว็บเป็นรูปพ่อ</li>
          <li>เปลี่ยนวิดีโอในเว็บเป็นเพลงสรรเสริญพระบารมี</li>
          <li>มีคำว่า "ทรงพระเจริญ" ขึ้นเมื่อเข้าเว็บไซต์</li>
          <li>เปลี่ยนเลขในเว็บให้เป็นเลขไทย</li>
          <li>เปลี่ยนคำทับศัพท์เป็นคำศัพท์บัญญัติ เช่น คอมพิวเตอร์ -> คณิตกรณ์</li>
          <li>เปลี่ยนธีมของเว็บไซต์ให้เป็นสีเหลือง</li>
          <li>ใส่ ๙ ไว้ด้านบนสุดของเว็บไซต์</li>
        </ul>
      </details>

      <details style="display: {display_d2};">
        <summary on:click={() => click_d1("2")}>เกมจิ้มพ่อ</summary>
        <PopDad />
      </details>

      <details style="display: {display_d3};">
        <summary on:click={() => click_d1("3")}>เกมรวมพ่อ</summary>
        <Dad2048 />
      </details>
    </div>
  
    <p></p>
    <a href="https://github.com/hack-for-dad/extension-chrome/releases/tag/1.0.0">
      <button class="download-button" on:click={downloadExtension}>
        Download Extension!
      </button>
    </a>
  </div>
</body>

<style>
  .container { 
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .download-button {
    border: 0px;
    border: black 1px solid;
    border-radius: 10rem;
    padding: 1rem 2rem;
    background-color: transparent;
  }

  .download-button:hover {
    cursor: pointer;
    background-color: rgb(239, 239, 0);
  }
</style>