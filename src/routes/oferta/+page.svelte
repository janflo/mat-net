<script>
    import {
      Card,
      CardTitle,
      CardSubtitle,
      CardActions,
      Button,
      Row,
      Col,
      AppBar,
      Icon,
    Divider,
    MaterialApp } from 'svelte-materialify';
    import { slide } from 'svelte/transition';
  import { mdiChevronDown , mdiDotsHorizontal} from '@mdi/js';
  import {  Menu, ListItem } from 'svelte-materialify';
	import { mdiBrightness6, mdiMenu, mdiStar } from '@mdi/js';
	let theme = 'light';
  let active = false;
	function toggleNavigation() {
		active = !active;
	}
  
  let active1 = false;
  function toggle() {
    active1 = !active1;
  }
  function toggleTheme() {
		if (theme === 'light') theme = 'dark';
		else theme = 'light';
	}
    const songs = [
      { name: 'Tuba Angel', author: 'Wieczka termoformowane', color: 'blue' },
      { name: 'Tuba Mech', author: 'Suchy lód', color: 'red' },
      { name: 'Tuba Archmage', author: 'Rożki wysokocukrowe', color: 'green' },
      { name: 'List Openheimera', author: 'Owijki', color: 'grey' },
    ];
  </script>
  
  <MaterialApp {theme}>
    <AppBar>
			<div slot="icon">
			<Menu class="d-flex flex-column">
				<div slot="activator">
				  <Button fab depressed on:click={toggleNavigation}>
					<Icon path={mdiMenu} />
				  </Button>
				</div>
				<ListItem ><a href="/">
					<Button  depressed>
						
							<Icon path={ mdiDotsHorizontal} class="mr-4" />
						
						Strona Główna
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

  <div class="d-flex justify-center mt-4 mb-4">
    <div class="rounded elevation-2  pa-14 d-flex justify-center flex-wrap" style="flex-grow:1;max-width:800px;gap: 20px;">
      {#each songs as song, i}
        <!-- <Card class=" pa-4">
          <Row>
            <Col cols={8}>
              <CardTitle>{song.name}</CardTitle>
              <CardSubtitle>{song.author}</CardSubtitle>
              <CardActions>
                <Button text>Play</Button>
              </CardActions>
            </Col>
            <Col cols={4}><img src="//picsum.photos/100?random={i}" alt="cover" /></Col>
          </Row>
        </Card> -->
        <Card style="max-width:300px;">
          <img src="//picsum.photos/300?random={i}" alt="background" />
          <CardTitle>Top western road trips {song.name}</CardTitle>
          <CardSubtitle>1,000 miles of wonder {song.author}</CardSubtitle>
          <CardActions>
            <Button text class={song.color}>Button</Button>
            <Button text fab size="small" class="ml-auto" on:click={toggle}>
              <Icon path={mdiChevronDown} rotate={active ? 180 : 0} />
            </Button>
          </CardActions>
          {#if active1}
            <div transition:slide>
              <Divider />
              <div class="pl-4 pr-4 pt-2 pb-2">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita autem,
                asperiores dolores, doloremque ea atque suscipit dolore, ut adipisci amet
                possimus dicta at voluptas consequatur!
              </div>
            </div>
          {/if}
        </Card>
        <br />
      {/each}
    </div>
  </div>
  </MaterialApp>