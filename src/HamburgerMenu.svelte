<script>

    import Button from "./menu_components/Button.svelte";
    import Navi from "./menu_components/Navi.svelte";
  
    export let menu_list;
  
    export let left=false;
    export let openButtonColor="#444444";
    export let closeButtonColor="#EDEDED";
    export let buttonTransitionTime="0.3";
  
    export let pcNaviColor="#444444";
    export let smNaviColor="#EDEDED";
    export let backgroundColor="#171717";
    export let naviFadeTime="0.5";
  
    let buttonProps = {
      left:left,
      openButtonColor:openButtonColor,
      closeButtonColor:closeButtonColor,
      buttonTransitionTime:buttonTransitionTime
    }
  
    let naviProps = {
      pcNaviColor:pcNaviColor,
      smNaviColor:smNaviColor,
      backgroundColor:backgroundColor,
      naviFadeTime:naviFadeTime
    }
  
    let open=false;
    function openClose(){
      open=!open;
    }
  
  </script>
  
  <div on:click={openClose}>
    <Button bind:open {...buttonProps}/>
    <Navi bind:open {menu_list} {...naviProps}/>
  </div>