<script>
	export const prerender = true;
	import {
		MaterialApp,
		Container,
		Row,
		Col,
		AppBar,
		Divider,
		Slider,
		Button
	} from 'svelte-materialify';
	import { Icon, NavigationDrawer, Overlay, Menu, ListItem, Select, Footer } from 'svelte-materialify';
	import { mdiBrightness6, mdiDotsHorizontal, mdiMenu, mdiStar } from '@mdi/js';
	let theme = 'light';
	let fluid = true;
	const items = [
    { name: 'Light', value: 'light' },
    { name: 'Dark', value: 'dark' }];
    const links = [{name:'Home', link:'/'}, {name:'Oferta', link:'/oferta'}, {name:'Contact us', link:'/oferta'}];
	function toggleTheme() {
		if (theme === 'light') theme = 'dark';
		else theme = 'light';
		value1 = theme;
	}
	// function toggleTheme11() {
	// 	 if (value1 === 'light') theme = 'light';
	// 	 else theme = 'dark';
	// }
	let value = 20;
	 let value1 = 'light';

	let active = false;
	function toggleNavigation() {
		active = !active;
	}
$: if (value >= 50) {theme = 'dark'; }
	else {theme = 'light'; }


	 $: (theme = value1);
	
	
</script>

<MaterialApp {theme}>
	<Container   style="width:100%;height:auto;">
	
		<AppBar>
			<div slot="icon">
			<Menu class="d-flex flex-column">
				<div slot="activator">
				  <Button fab depressed on:click={toggleNavigation}>
					<Icon path={mdiMenu} />
				  </Button>
				</div>
				<ListItem ><a href="/oferta">
					<Button  depressed>
						
							<Icon path={ mdiDotsHorizontal} class="mr-4" />
						
						Nasza Oferta
					</Button>
				</a></ListItem>
				<ListItem >Item 2</ListItem>
				<ListItem>Item 3</ListItem>
			  </Menu>
			</div>
			<span slot="title">Title</span>
			<div style="flex-grow:1" />
  			<Button fab depressed on:click={toggleTheme}>
					<Icon path={mdiBrightness6} />
				  </Button>
		</AppBar>
		<!-- <NavigationDrawer style="position: relative" {active}>  Content</NavigationDrawer>
		<Overlay {active} absolute on:click={toggleNavigation} index={1} /> -->
	
	
		<Row>
			<Col cols={12} sm={12} md={4}><h3 class="mb-4">Svelte Materialify</h3></Col>
			<Col cols={12} sm={12} md={4}>
				<br />
				<Slider thumb persistentThumb bind:value  />
				<!-- on:change={toggleTheme11} -->
			</Col>
			<Col cols={12} sm={12} md={4}>  <Select solo {items} bind:value={value1}  placeholder="Choose Theme" /></Col>
		</Row>
	
	<br />

	<Divider />

	<br />
	<Row>
			<Col cols={12} sm={12} md={6}>
				<div class="text-center ">
		<a href="">
			<Button class="primary-color ">
				Star on GitHub {value1}
			</Button>
		</a>
		</div>
			</Col>
			<Col cols={12} sm={12} md={6}>
				<div class="text-center ">
				<Button on:click={toggleTheme} class="primary-color ">
					Toggle Theme
				</Button>
				</div>
			</Col>
		</Row>
	
		<br />
		<div class="mt-4 mb-4"></div>
	
	<Footer padless absolute class="indigo theme--dark justify-center flex-column">
		<div class="mt-2 mb-2">
			{#each links as link}
			<a href="{link.link}">
			<Button text rounded>{link.name}</Button>
		  </a>
			{/each}
		  </div>
		<div class="indigo lighten-1 pa-2 text-center" style="width:100%">
		  2023 -
		  <b>JanFlo</b>
		</div>
	  </Footer>
	  
	</Container>
</MaterialApp>
