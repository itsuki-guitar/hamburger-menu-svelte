# hamburger-menu-svelte

I have developed hamburger menu for Svelte. This menu is very simple and easy to use. Depending on the size of the screen, hamburger menu and global menu are switched. You can customize it using props.

RIPL: [Example of how to use hamburger-menu-svelte](https://svelte.dev/repl/f4bbc54bdb1b470c8aaafae6145a5537?version=3.43.2)
![](https://media.giphy.com/media/couYpkokoLxGGezgYW/giphy.gif)

## Update infomation

- Add some useful props

	- buttonTopSize
	- buttonSideSize
	- zIndexSize  
- Change standard values

# 1. How to use?

## 1.1. Install
Type the following command in terminal and execute it.

```bash
npm i hamburger-menu-svelte
```

## 1.2. Import

Import this package into your program. Please add the following code between `<script> `and `</script>`.
```bash
<script>
	import Hamburger from "hamburger-menu-svelte";
	const menu_list = [
		{ name: "Sample1", url: "./" },
		{ name: "Sample2", url: "./" },
		{ name: "Sample3", url: "./" },
		{ name: "Sample4", url: "./" },
	];
</script>
```
Menu items assign to menu_list then hamburger menu will reflect them. There is no limit to the number of menu items.

## 1.3. Use

When you use `<Hamburger/>`, you should export menu_list. Please write the following.

```bash
<Hamburger {menu_list}/>
```
If you don't export this list, the menu items isn't reflected in hamburger menu.

# 2. Props
You can customize hamburger menu by using props. The following props are available for hamburger-menu-svelte. Feel free to use them.

| Prop  | Default | Example of use |Description                                            |
|-------|---------|---------|--------------------------------------------------------|
| left  | false   | `<Hamburger {menu_list} left="true"/>` | You can change the position of hamburger menu. The default position is right.|
| openButtonColor | #444444 | `<Hamburger {menu_list} openButtonColor="#FFFFFF"/>`| You can change the color of open button.|
| closeButtonColor | #EDEDED | `<Hamburger {menu_list} closeButtonColor="#AA0000"/>`| You can change the color of close button. |
| buttonTransitionTime | 0.3 | `<Hamburger {menu_list} buttonTransitionTime="10"/>`| You can change transition time of buttons. This time unit is second so default time is 0.3s. <span style="color: red; ">When assigning a value to a variable, you mustn't write a time-unit(s, ms and h etc...)</span>|
| pcNaviColor | #444444 | `<Hamburger {menu_list} pcNaviColor="#000000"/>`| You can change the text color in global menu.|
| smNaviColor | #EDEDED | `<Hamburger {menu_list} pcNaviColor="#ABCDE0"/>`| You can change the text color in opened hamburger menu. |
| backgroundColor | #171717 | `<Hamburger {menu_list} backgroundColor="#00FF00"/>`| You can change the background of opened hamburger menu.|
| naviFadeTime | 0.5 | `<Hamburger {menu_list} naviFadeTime="1.0"/>`| You can change transition time of navi. This time unit is second so default time is 0.5s. <span style="color: red; ">When assigning a value to a variable, you mustn't write a time-unit(s, ms and h etc...)</span>|
| buttonTopSize | 15 | `<Hamburger {menu_list} buttonTopSize="100"/>` | This is a variable for adjusting the height of the button position. You don't need to write "px".|
| buttonSideSize | 10 | `<Hamburger {menu_list} buttonSideSize="100"/>` | This is a variable for adjusting the width of the button position. You don't need to write "px". It's the distance from the right. If you write left="true", It's the distance from the left.|
| zIndexSize | 100 | `<Hamburger {menu_list} zIndexSize="10"/>`| This props determines the value of the z-index. |