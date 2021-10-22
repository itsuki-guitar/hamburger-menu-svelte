<script>

    import Button from "./menu_components/Button.svelte";
    import Navi from "./menu_components/Navi.svelte";
  
    export let menu_list;
  
    export let buttonTopSize="15";
    export let buttonSideSize="10";
    export let left=false;
    export let openButtonColor="#444444";
    export let closeButtonColor="#EDEDED";
    export let buttonTransitionTime="0.3";
    export let zIndexSize = "100";

    export let pcNaviColor="#444444";
    export let smNaviColor="#EDEDED";
    export let backgroundColor="#171717";
    export let naviFadeTime="0.5";
    export let navizIndexSize = Number(zIndexSize) - 1;

    let buttonProps = {
      left:left,
      buttonTopSize:buttonTopSize,
      openButtonColor:openButtonColor,
      closeButtonColor:closeButtonColor,
      buttonTransitionTime:buttonTransitionTime,
      zIndexSize:zIndexSize,
      buttonTopSize:buttonTopSize,
      buttonSideSize:buttonSideSize

    }

    let naviProps = {
      pcNaviColor:pcNaviColor,
      smNaviColor:smNaviColor,
      backgroundColor:backgroundColor,
      naviFadeTime:naviFadeTime,
      navizIndexSize:navizIndexSize
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