<script>
    import { fade } from 'svelte/transition';
    
    export let open;
  
    export let left;
    export let openButtonColor;
    export let closeButtonColor;
    export let buttonTransitionTime;
    let textFadeTime=Number(buttonTransitionTime);
  
    buttonTransitionTime = buttonTransitionTime + "s";
  
  
  </script>
  
  
  <div style="--openButtonColor:{openButtonColor}; --closeButtonColor:{closeButtonColor};--buttonTransitionTime:{buttonTransitionTime}">
      <button type="button" class="nav-button" class:open class:left/>
      {#if open==false}
      <p class="nav-text" transition:fade="{{duration: textFadeTime*1000}}" style class:left>menu</p>
      {/if}
  </div>
  
  
  <style>
  
  .left{
    left:10px;
  }
  
  .nav-button{
    position: fixed;
    /* Specify the location */
    top: 15px;
    right:10px;
    display: block;
    padding: 0;
    outline: none;
    border: none;
    width: 36px;
    height: 0px;
    cursor: pointer;
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
    z-index: 100;
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
    top: 10px;
    right:10px;
    display: block;
    padding: 0;
    cursor: pointer;
    font-size: 14px;
    color:var(--openButtonColor);
    transition: var(--naviTransitionTime) ease-in-out;
  }
  
  @media(min-width: 768px){
    .nav-button,.nav-text{
      display:none;
    }
  }
  
  </style>