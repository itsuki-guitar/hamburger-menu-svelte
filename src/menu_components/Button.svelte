<script>
    import { fade } from 'svelte/transition';
    
    export let open;
  
    export let left;
    export let openButtonColor;
    export let closeButtonColor;
    export let buttonTransitionTime;
    let textFadeTime=Number(buttonTransitionTime);
    export let zIndexSize;
    export let buttonTopSize;
    export let buttonSideSize;
    let textTopSize = Number(buttonTopSize)-5;
  
    buttonTransitionTime = buttonTransitionTime + "s";
    buttonTopSize = buttonTopSize + "px";
    buttonSideSize = buttonSideSize + "px";
    textTopSize = textTopSize + "px";
  
  </script>
  
  
  <div style="--openButtonColor:{openButtonColor}; --closeButtonColor:{closeButtonColor};
              --buttonTransitionTime:{buttonTransitionTime}; --zIndexSize:{zIndexSize};
              --buttonTopSize:{buttonTopSize}; --textTopSize:{textTopSize}; --buttonSideSize:{buttonSideSize}">
      <button type="button" class="nav-button" class:open class:left/>
      {#if open==false}
      <p class="nav-text" transition:fade="{{duration: textFadeTime*1000}}" style class:left>menu</p>
      {/if}
  </div>
  
  
  <style>
  
  .left{
    left:var(--buttonSideSize);
  }
  
  .nav-button{
    position: fixed;
    /* Specify the location */
    top: var(--buttonTopSize);
    right:var(--buttonSideSize);
    display: block;
    padding: 0;
    outline: none;
    border: none;
    width: 36px;
    height: 0px;
    cursor: var(--zIndexSize);
  }
  
  .nav-button::before,
  .nav-button::after{
    /* made empty strings and draw two lines above and below it. */
    content : "";
    display: block;
    height: 2px;
    background-color: var(--openButtonColor);
    transform: translateY(4px);
    transition: var(--buttonTransitionTime) ease-in-out;
  }
  .nav-button::before{
    /* made a center line */
    transform: translateY(1px);
    box-shadow: 0 10px var(--openButtonColor);
  }
  
  .open{
    box-shadow: none;
    transform: translateY(10px);
    z-index: var(--zIndexSize);
  }
  .open::before{
    content: "";
    height: 1px;
    transform: rotate(45deg);
    background-color: var(--closeButtonColor);
    box-shadow: none;
  }
  .open::after{
    content: "";
    height: 1px;
    transform: rotate(-45deg);
    background-color: var(--closeButtonColor);
    box-shadow: none;
  }
  
  .nav-text{
    position: fixed;
    top: var(--textTopSize);
    right:var(--buttonSideSize);
    display: block;
    padding: 0;
    cursor: pointer;
    font-size: 14px;
    color:var(--openButtonColor);
    transition: var(--naviTransitionTime) ease-in-out;
    z-index: var(--zIndexSize);
  }
  
  @media(min-width: 768px){
    .nav-button,.nav-text{
      display:none;
    }
  }
  
  </style>