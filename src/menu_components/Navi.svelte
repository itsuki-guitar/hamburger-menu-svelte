<script>
    import { each } from "svelte/internal";
    export let open;
    export let menu_list;
  
    export let pcNaviColor;
    export let smNaviColor;
    export let backgroundColor;
    export let naviFadeTime;
  
    naviFadeTime = naviFadeTime + "s";
  </script>
  
  <div style="--pcNaviColor:{pcNaviColor}; --smNaviColor:{smNaviColor}; --backgroundColor:{backgroundColor}; --naviFadeTime:{naviFadeTime}">
    <nav class:open>
      <ul>
        {#each menu_list as { name, url }}
          <li><a href={url}>{name}</a></li>
        {/each}
      </ul>
    </nav>
  </div>
  
  <style>
    @media (max-width: 767px) {
      nav {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        background: var(--backgroundColor);
        display: flex;
        justify-content: center;
        align-items: center;
        /* 初期：非表示 */
        visibility: hidden;
        opacity: 0;
        /* ふわっと表示 */
        transition: var(--naviFadeTime) ease-in-out;
      }
      nav ul {
        list-style: none;
      }
      nav li:not(:last-child) {
        margin-bottom: 30px;
      }
      nav a {
        color: var(--smNaviColor);
      }
  
      .open {
        visibility: visible;
        opacity: 1;
      }
    }
    @media (min-width: 768px) {
      /* メニューを右に寄せる */
      nav {
        /* 右寄せ */
        margin-left: auto;
      }
      nav ul {
        display: flex;
        list-style: none;
      }
      nav ul li:not(:first-child) {
        margin-left: 20px;
      }
      nav ul li a {
        color: var(--pcNaviColor);
      }
    }
  </style>
  