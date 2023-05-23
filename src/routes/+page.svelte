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
	import { mdiMenu } from '@mdi/js';
	let theme = 'light';

	function toggleTheme() {
		if (theme === 'light') theme = 'dark';
		else theme = 'light';
	}
	function toggleTheme11() {
		if (value < 50) theme = 'dark';
		else theme = 'light';
	}
	let value = 20;

	let active = false;
	function toggleNavigation() {
		active = !active;
	}
</script>

<MaterialApp {theme}>
	<Container>
	
		<AppBar>
			<div slot="icon">
			<Menu class="d-flex flex-column">
				<div slot="activator">
				  <Button fab depressed on:click={toggleNavigation}>
					<Icon path={mdiMenu} />
				  </Button>
				</div>
				<ListItem >Item 1</ListItem>
				<ListItem >Item 2</ListItem>
				<ListItem>Item 3</ListItem>
			  </Menu>
			</div>
			<span slot="title">Title</span>
		</AppBar>
		<!-- <NavigationDrawer style="position: relative" {active}>  Content</NavigationDrawer>
		<Overlay {active} absolute on:click={toggleNavigation} index={1} /> -->
	
	
		<Row>
			<Col><h3 class="mb-4">Svelte Materialify</h3></Col>
			<Col>
				<br />
				<Slider thumb persistentThumb bind:value on:change={toggleTheme11} />
			</Col>
		</Row>
	</Container>
	<br />

	<Divider />

	<br />
	<div class="text-center">
		<a href="//github.com/TheComputerM/svelte-materialify/stargazers">
			<Button class="primary-color">
				Star on GitHub {value}
			</Button>
		</a>
		<Button on:click={toggleTheme}>Toggle Theme</Button>
	</div>
	<br />
</MaterialApp>
