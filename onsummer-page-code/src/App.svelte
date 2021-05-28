<script>
  import logo from "/logo.webp";
  import routes from "./data/routes.json";
  import { onMount } from "svelte";
  let env = import.meta.env.MODE
  let contentDiv;
  onMount(() => {
    contentDiv.onClick = () => {
      console.log(345);
    };
    const paras = contentDiv.querySelectorAll("p");
    paras.forEach((para, i) => {
      para.onclick = function () {
        const tab = window.open(routes[`${i + 1}`][env], "_blank");
      };
    });
  });
</script>

<div id="container">
  <div id="title" class="unselectable">
    <img src={logo} alt="我的logo" />
    你好啊，欢迎来到我的站点
  </div>
  <div id="content" bind:this={contentDiv}>
    <p class="unselectable"><span>笔记：WebGPU</span>（需要 Chrome / Edge 的 Canary 版本浏览器）</p>
    <p class="unselectable"><span>作品：ts-3dtiles</span></p>
  </div>
</div>

<style>
  @font-face {
    font-family: FiraCode;
    src: url("/fonts/FiraCode-Regular.woff2"),
      url("/fonts/FiraCode-Regular.woff");
  }

  @font-face {
    font-family: Helvetica;
    src: url("/fonts/Helvetica.woff");
  }

  #container {
    font-family: Helvetica;
    width: 70vw;
    height: 70vh;
  }

  #title {
    font-size: 3rem;
    padding: 2rem 0;
  }

  #title img {
    width: 2.5rem;
    height: 2.5rem;
    transform: translate(0, -0.5rem) rotate(56deg) scale(1.5);
  }

  #content p {
    padding-left: 1.2rem;
    font-size: 1.2rem;
  }

  #content p span {
    padding: 0.5rem;
    border-radius: 0.5rem;
    cursor: pointer;
  }

  #content p span:hover {
    transition: all 0.1s;
    cursor: pointer;
    border-radius: 0;
    border-bottom: 0.5rem solid rgba(24, 24, 24, 0.63);
  }

  .unselectable {
    -moz-user-select: -moz-none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -o-user-select: none;
    user-select: none;
  }
</style>
