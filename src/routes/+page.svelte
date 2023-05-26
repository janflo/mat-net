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
	import { Icon, NavigationDrawer, Overlay, Menu, ListItem } from 'svelte-materialify';
	import { mdiBrightness6, mdiMenu, mdiStar } from '@mdi/js';
	let theme = 'light';
	let fluid = true;

	function toggleTheme() {
		if (theme === 'light') theme = 'dark';
		else theme = 'light';
	}
	// function toggleTheme11() {
	// 	if (value < 50) theme = 'dark';
	// 	else theme = 'light';
	// }
	let value = 20;

	let active = false;
	function toggleNavigation() {
		active = !active;
	}
	$: if (value >= 50) theme = 'dark';
	else theme = 'light';
</script>

<MaterialApp {theme}>
	<Container {fluid}>
	
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
						
							<Icon path={mdiStar} class="mr-4" />
						
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
			<Col cols={12} sm={12} md={6}><h3 class="mb-4">Svelte Materialify</h3></Col>
			<Col cols={12} sm={12} md={6}>
				<br />
				<Slider thumb persistentThumb bind:value  />
				<!-- on:change={toggleTheme11} -->
			</Col>
		</Row>
	
	<br />

	<Divider />

	<br />
	<Row>
			<Col cols={12} sm={12} md={6}>
				<div class="text-center ">
		<a href="">
			<Button class="primary-color ">
				Star on GitHub {value}
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
	</Container>
</MaterialApp>
