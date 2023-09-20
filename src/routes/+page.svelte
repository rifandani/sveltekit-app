<script lang="ts">
	import * as Accordion from '$lib/components/ui/accordion';
	import * as Alert from '$lib/components/ui/alert';
	import * as AlertDialog from '$lib/components/ui/alert-dialog';
	import * as AspectRatio from '$lib/components/ui/aspect-ratio';
	import * as Avatar from '$lib/components/ui/avatar';
	import { Badge } from '$lib/components/ui/badge';
	import { Button, buttonVariants } from '$lib/components/ui/button';
	import * as Card from '$lib/components/ui/card';
	import { Checkbox } from '$lib/components/ui/checkbox';
	import * as Collapsible from '$lib/components/ui/collapsible';
	import * as ContextMenu from '$lib/components/ui/context-menu';
	import * as Dialog from '$lib/components/ui/dialog';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu';
	import * as HoverCard from '$lib/components/ui/hover-card';
	import { Input } from '$lib/components/ui/input';
	import { Label } from '$lib/components/ui/label';
	import * as Menubar from '$lib/components/ui/menubar';
	import * as Popover from '$lib/components/ui/popover';
	import { Progress } from '$lib/components/ui/progress';
	import * as RadioGroup from '$lib/components/ui/radio-group';
	import * as Select from '$lib/components/ui/select';
	import { Separator } from '$lib/components/ui/separator';
	import * as Sheet from '$lib/components/ui/sheet';
	import { Skeleton } from '$lib/components/ui/skeleton';
	import { Slider } from '$lib/components/ui/slider';
	import { Switch } from '$lib/components/ui/switch';
	import * as Table from '$lib/components/ui/table';
	import * as Tabs from '$lib/components/ui/tabs';
	import { Textarea } from '$lib/components/ui/textarea';
	import { Toggle } from '$lib/components/ui/toggle';
	import * as Tooltip from '$lib/components/ui/tooltip';
	import Icon from '@iconify/svelte';

	const invoices = [
		{
			invoice: 'INV001',
			paymentStatus: 'Paid',
			totalAmount: '$250.00',
			paymentMethod: 'Credit Card'
		},
		{
			invoice: 'INV002',
			paymentStatus: 'Pending',
			totalAmount: '$150.00',
			paymentMethod: 'PayPal'
		}
	];

	let showBookmarks = false;
	let showFullURLs = true;
	let value = 'pedro';
	let position = 'bottom';
	let bookmarks = false;
	let fullUrls = true;
	const profileRadioValue = 'benoit';
	const SHEET_SIDES = ['top', 'right', 'bottom', 'left'] as const;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Home screen" />
</svelte:head>

<main class="flex flex-col p-5 space-y-5">
	<Accordion.Root>
		<Accordion.Item value="1">
			<Accordion.Trigger>Trigger 1</Accordion.Trigger>
			<Accordion.Content>Content 1</Accordion.Content>
		</Accordion.Item>

		<Accordion.Item value="2">
			<Accordion.Trigger>Trigger 2</Accordion.Trigger>
			<Accordion.Content>Content 2</Accordion.Content>
		</Accordion.Item>
	</Accordion.Root>

	<Alert.Root variant="destructive">
		<Icon icon="lucide:alert-circle" class="h-4 w-4" />
		<Alert.Title>Error</Alert.Title>
		<Alert.Description>Your session has expired. Please login again.</Alert.Description>
	</Alert.Root>

	<AlertDialog.Root>
		<AlertDialog.Trigger class={buttonVariants({ variant: 'default' })}>Open</AlertDialog.Trigger>
		<AlertDialog.Content>
			<AlertDialog.Header>
				<AlertDialog.Title>Are you absolutely sure?</AlertDialog.Title>
				<AlertDialog.Description>
					This action cannot be undone. This will permanently delete your account and remove your
					data from our servers.
				</AlertDialog.Description>
			</AlertDialog.Header>
			<AlertDialog.Footer>
				<AlertDialog.Cancel>Cancel</AlertDialog.Cancel>
				<AlertDialog.Action>Continue</AlertDialog.Action>
			</AlertDialog.Footer>
		</AlertDialog.Content>
	</AlertDialog.Root>

	<div class="h-[200px] w-[200px]">
		<AspectRatio.Root ratio={16 / 9} class="bg-muted">
			<img
				src="https://cataas.com/cat?type=square"
				alt="random cat"
				height="200"
				width="200"
				class="rounded-md object-contain"
			/>
		</AspectRatio.Root>
	</div>

	<Avatar.Root>
		<Avatar.Image src="https://github.com/shadcn.png" alt="@shadcn" />
		<Avatar.Fallback>CN</Avatar.Fallback>
	</Avatar.Root>

	<Badge variant="secondary" class="w-fit">Secondary</Badge>

	<Button variant="secondary">Button</Button>

	<Card.Root class="border">
		<Card.Header>
			<Card.Title>Card Title</Card.Title>
			<Card.Description>Card Description</Card.Description>
		</Card.Header>
		<Card.Content>
			<p>Card Content</p>
		</Card.Content>
		<Card.Footer>
			<p>Card Footer</p>
		</Card.Footer>
	</Card.Root>

	<div class="flex items-center space-x-2">
		<Checkbox id="terms" />
		<Label for="terms">Accept terms and conditions</Label>
	</div>

	<Collapsible.Root class="w-[350px] space-y-2">
		<div class="flex items-center justify-between space-x-4 px-4">
			<h4 class="text-sm font-semibold">@peduarte starred 3 repositories</h4>
			<Collapsible.Trigger asChild let:builder>
				<Button builders={[builder]} variant="ghost" size="sm" class="w-9 p-0">
					<Icon icon="lucide:chevrons-up-down" class="h-4 w-4" />
					<span class="sr-only">Toggle</span>
				</Button>
			</Collapsible.Trigger>
		</div>
		<div class="rounded-md border px-4 py-3 font-mono text-sm">@melt-ui/melt-ui</div>
		<Collapsible.Content class="space-y-2">
			<div class="rounded-md border px-4 py-3 font-mono text-sm">bits-ui</div>
			<div class="rounded-md border px-4 py-3 font-mono text-sm">@radix-ui/primitives</div>
		</Collapsible.Content>
	</Collapsible.Root>

	<ContextMenu.Root>
		<ContextMenu.Trigger
			class="flex h-[150px] w-[300px] items-center justify-center rounded-md border border-dashed text-sm"
		>
			Right click here
		</ContextMenu.Trigger>
		<ContextMenu.Content class="w-64">
			<ContextMenu.Item inset>
				Back
				<ContextMenu.Shortcut>⌘[</ContextMenu.Shortcut>
			</ContextMenu.Item>
			<ContextMenu.Item inset>
				Forward
				<ContextMenu.Shortcut>⌘]</ContextMenu.Shortcut>
			</ContextMenu.Item>
			<ContextMenu.Item inset>
				Reload
				<ContextMenu.Shortcut>⌘R</ContextMenu.Shortcut>
			</ContextMenu.Item>
			<ContextMenu.Sub>
				<ContextMenu.SubTrigger inset>More Tools</ContextMenu.SubTrigger>
				<ContextMenu.SubContent class="w-48">
					<ContextMenu.Item>
						Save Page As...
						<ContextMenu.Shortcut>⇧⌘S</ContextMenu.Shortcut>
					</ContextMenu.Item>
					<ContextMenu.Item>Create Shortcut...</ContextMenu.Item>
					<ContextMenu.Item>Name Window...</ContextMenu.Item>
					<ContextMenu.Separator />
					<ContextMenu.Item>Developer Tools</ContextMenu.Item>
				</ContextMenu.SubContent>
			</ContextMenu.Sub>
			<ContextMenu.Separator />
			<ContextMenu.CheckboxItem bind:checked={showBookmarks}>
				Show Bookmarks Bar
				<ContextMenu.Shortcut>⌘⇧B</ContextMenu.Shortcut>
			</ContextMenu.CheckboxItem>
			<ContextMenu.CheckboxItem bind:checked={showFullURLs}>
				Show Full URLs
			</ContextMenu.CheckboxItem>
			<ContextMenu.Separator />
			<ContextMenu.RadioGroup bind:value>
				<ContextMenu.Label inset>People</ContextMenu.Label>
				<ContextMenu.Separator />
				<ContextMenu.RadioItem value="pedro">Pedro Duarte</ContextMenu.RadioItem>
				<ContextMenu.RadioItem value="colm">Colm Tuite</ContextMenu.RadioItem>
			</ContextMenu.RadioGroup>
		</ContextMenu.Content>
	</ContextMenu.Root>

	<Dialog.Root>
		<Dialog.Trigger>Open</Dialog.Trigger>
		<Dialog.Content>
			<Dialog.Header>
				<Dialog.Title>Are you sure absolutely sure?</Dialog.Title>
				<Dialog.Description>
					This action cannot be undone. This will permanently delete your account and remove your
					data from our servers.
				</Dialog.Description>
			</Dialog.Header>
		</Dialog.Content>
	</Dialog.Root>

	<DropdownMenu.Root>
		<DropdownMenu.Trigger asChild let:builder>
			<Button variant="outline" builders={[builder]}>Open</Button>
		</DropdownMenu.Trigger>
		<DropdownMenu.Content class="w-56">
			<DropdownMenu.Label>Panel Position</DropdownMenu.Label>
			<DropdownMenu.Separator />
			<DropdownMenu.RadioGroup bind:value={position}>
				<DropdownMenu.RadioItem value="top">Top</DropdownMenu.RadioItem>
				<DropdownMenu.RadioItem value="bottom">Bottom</DropdownMenu.RadioItem>
				<DropdownMenu.RadioItem value="right">Right</DropdownMenu.RadioItem>
			</DropdownMenu.RadioGroup>
		</DropdownMenu.Content>
	</DropdownMenu.Root>

	<HoverCard.Root>
		<HoverCard.Trigger
			href="https://github.com/sveltejs"
			target="_blank"
			rel="noreferrer noopener"
			class="mx-auto hover:underline underline-offset-4 rounded-sm focus-visible:outline-2 focus-visible:outline-offset-8 focus-visible:outline-black"
		>
			@sveltejs
		</HoverCard.Trigger>
		<HoverCard.Content class="w-80">
			<div class="flex justify-between space-x-4">
				<Avatar.Root>
					<Avatar.Image src="https://github.com/sveltejs.png" />
					<Avatar.Fallback>SK</Avatar.Fallback>
				</Avatar.Root>
				<div class="space-y-1">
					<h4 class="text-sm font-semibold">@sveltejs</h4>
					<p class="text-sm">Cybernetically enhanced web apps.</p>
					<div class="flex items-center pt-2">
						<Icon icon="lucide:calendar-days" class="mr-2 h-4 w-4 opacity-70" />{' '}
						<span class="text-xs text-muted-foreground"> Joined September 2022 </span>
					</div>
				</div>
			</div>
		</HoverCard.Content>
	</HoverCard.Root>

	<Input type="email" placeholder="email" class="max-w-xs" />

	<Menubar.Root>
		<Menubar.Menu>
			<Menubar.Trigger>File</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.Item>
					New Tab <Menubar.Shortcut>⌘T</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Item>
					New Window <Menubar.Shortcut>⌘N</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Item>New Incognito Window</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Sub>
					<Menubar.SubTrigger>Share</Menubar.SubTrigger>
					<Menubar.SubContent>
						<Menubar.Item>Email link</Menubar.Item>
						<Menubar.Item>Messages</Menubar.Item>
						<Menubar.Item>Notes</Menubar.Item>
					</Menubar.SubContent>
				</Menubar.Sub>
				<Menubar.Separator />
				<Menubar.Item>
					Print... <Menubar.Shortcut>⌘P</Menubar.Shortcut>
				</Menubar.Item>
			</Menubar.Content>
		</Menubar.Menu>
		<Menubar.Menu>
			<Menubar.Trigger>Edit</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.Item>
					Undo <Menubar.Shortcut>⌘Z</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Item>
					Redo <Menubar.Shortcut>⇧⌘Z</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Sub>
					<Menubar.SubTrigger>Find</Menubar.SubTrigger>
					<Menubar.SubContent>
						<Menubar.Item>Search the web</Menubar.Item>
						<Menubar.Separator />
						<Menubar.Item>Find...</Menubar.Item>
						<Menubar.Item>Find Next</Menubar.Item>
						<Menubar.Item>Find Previous</Menubar.Item>
					</Menubar.SubContent>
				</Menubar.Sub>
				<Menubar.Separator />
				<Menubar.Item>Cut</Menubar.Item>
				<Menubar.Item>Copy</Menubar.Item>
				<Menubar.Item>Paste</Menubar.Item>
			</Menubar.Content>
		</Menubar.Menu>
		<Menubar.Menu>
			<Menubar.Trigger>View</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.CheckboxItem bind:checked={bookmarks}
					>Always Show Bookmarks Bar</Menubar.CheckboxItem
				>
				<Menubar.CheckboxItem bind:checked={fullUrls}>Always Show Full URLs</Menubar.CheckboxItem>
				<Menubar.Separator />
				<Menubar.Item inset>
					Reload <Menubar.Shortcut>⌘R</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Item inset>
					Force Reload <Menubar.Shortcut>⇧⌘R</Menubar.Shortcut>
				</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Item inset>Toggle Fullscreen</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Item inset>Hide Sidebar</Menubar.Item>
			</Menubar.Content>
		</Menubar.Menu>
		<Menubar.Menu>
			<Menubar.Trigger>Profiles</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.RadioGroup value={profileRadioValue}>
					<Menubar.RadioItem value="andy">Andy</Menubar.RadioItem>
					<Menubar.RadioItem value="benoit">Benoit</Menubar.RadioItem>
					<Menubar.RadioItem value="Luis">Luis</Menubar.RadioItem>
				</Menubar.RadioGroup>
				<Menubar.Separator />
				<Menubar.Item inset>Edit...</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Item inset>Add Profile...</Menubar.Item>
			</Menubar.Content>
		</Menubar.Menu>
	</Menubar.Root>

	<Popover.Root>
		<Popover.Trigger>Open</Popover.Trigger>
		<Popover.Content>Place content for the popover here.</Popover.Content>
	</Popover.Root>

	<Progress value={33} />

	<RadioGroup.Root value="option-one">
		<div class="flex items-center space-x-2">
			<RadioGroup.Item value="option-one" id="option-one" />
			<Label for="option-one">Option One</Label>
		</div>
		<div class="flex items-center space-x-2">
			<RadioGroup.Item value="option-two" id="option-two" />
			<Label for="option-two">Option Two</Label>
		</div>
	</RadioGroup.Root>

	<Select.Root>
		<Select.Trigger class="w-[180px]">
			<Select.Value placeholder="Theme" />
		</Select.Trigger>
		<Select.Content>
			<Select.Item value="light">Light</Select.Item>
			<Select.Item value="dark">Dark</Select.Item>
			<Select.Item value="system">System</Select.Item>
		</Select.Content>
	</Select.Root>

	<div>
		<div class="space-y-1">
			<h4 class="text-sm font-medium leading-none">Radix Primitives</h4>
			<p class="text-sm text-muted-foreground">An open-source UI component library.</p>
		</div>
		<Separator class="my-4" />
		<div class="flex h-5 items-center space-x-4 text-sm">
			<div>Blog</div>
			<Separator orientation="vertical" />
			<div>Docs</div>
			<Separator orientation="vertical" />
			<div>Source</div>
		</div>
	</div>

	<div class="grid grid-cols-2 gap-2">
		{#each SHEET_SIDES as side, _ (side)}
			<Sheet.Root>
				<Sheet.Trigger asChild let:builder>
					<Button builders={[builder]} variant="outline">{side}</Button>
				</Sheet.Trigger>
				<Sheet.Content {side}>
					<Sheet.Header>
						<Sheet.Title>Edit profile</Sheet.Title>
						<Sheet.Description>
							Make changes to your profile here. Click save when you're done.
						</Sheet.Description>
					</Sheet.Header>
					<div class="grid gap-4 py-4">
						<div class="grid grid-cols-4 items-center gap-4">
							<Label for="name" class="text-right">Name</Label>
							<Input id="name" value="Pedro Duarte" class="col-span-3" />
						</div>
						<div class="grid grid-cols-4 items-center gap-4">
							<Label for="username" class="text-right">Username</Label>
							<Input id="username" value="@peduarte" class="col-span-3" />
						</div>
					</div>
					<Sheet.Footer>
						<Sheet.Close asChild let:builder>
							<Button builders={[builder]} type="submit">Save changes</Button>
						</Sheet.Close>
					</Sheet.Footer>
				</Sheet.Content>
			</Sheet.Root>
		{/each}
	</div>

	<div class="flex items-center space-x-4">
		<Skeleton class="h-12 w-12 rounded-full" />
		<div class="space-y-2">
			<Skeleton class="h-4 w-[250px]" />
			<Skeleton class="h-4 w-[200px]" />
		</div>
	</div>

	<Slider value={[50]} max={100} step={1} class="max-w-[70%]" />

	<div class="flex items-center space-x-2">
		<Switch id="airplane-mode" />
		<Label for="airplane-mode">Airplane Mode</Label>
	</div>

	<Table.Root>
		<Table.Caption>A list of your recent invoices.</Table.Caption>
		<Table.Header>
			<Table.Row>
				<Table.Head class="w-[100px]">Invoice</Table.Head>
				<Table.Head>Status</Table.Head>
				<Table.Head>Method</Table.Head>
				<Table.Head class="text-right">Amount</Table.Head>
			</Table.Row>
		</Table.Header>
		<Table.Body>
			{#each invoices as invoice, i (i)}
				<Table.Row>
					<Table.Cell class="font-medium">{invoice.invoice}</Table.Cell>
					<Table.Cell>{invoice.paymentStatus}</Table.Cell>
					<Table.Cell>{invoice.paymentMethod}</Table.Cell>
					<Table.Cell class="text-right">{invoice.totalAmount}</Table.Cell>
				</Table.Row>
			{/each}
		</Table.Body>
	</Table.Root>

	<Tabs.Root value="account" class="w-[400px]">
		<Tabs.List class="grid w-full grid-cols-2">
			<Tabs.Trigger value="account">Account</Tabs.Trigger>
			<Tabs.Trigger value="password">Password</Tabs.Trigger>
		</Tabs.List>
		<Tabs.Content value="account">
			<Card.Root>
				<Card.Header>
					<Card.Title>Account</Card.Title>
					<Card.Description>
						Make changes to your account here. Click save when you're done.
					</Card.Description>
				</Card.Header>
				<Card.Content class="space-y-2">
					<div class="space-y-1">
						<Label for="name">Name</Label>
						<Input id="name" value="Pedro Duarte" />
					</div>
					<div class="space-y-1">
						<Label for="username">Username</Label>
						<Input id="username" value="@peduarte" />
					</div>
				</Card.Content>
				<Card.Footer>
					<Button>Save changes</Button>
				</Card.Footer>
			</Card.Root>
		</Tabs.Content>
		<Tabs.Content value="password">
			<Card.Root>
				<Card.Header>
					<Card.Title>Password</Card.Title>
					<Card.Description>
						Change your password here. After saving, you'll be logged out.
					</Card.Description>
				</Card.Header>
				<Card.Content class="space-y-2">
					<div class="space-y-1">
						<Label for="current">Current password</Label>
						<Input id="current" type="password" />
					</div>
					<div class="space-y-1">
						<Label for="new">New password</Label>
						<Input id="new" type="password" />
					</div>
				</Card.Content>
				<Card.Footer>
					<Button>Save password</Button>
				</Card.Footer>
			</Card.Root>
		</Tabs.Content>
	</Tabs.Root>

	<div class="grid w-full gap-1.5">
		<Label for="message-2">Your Message</Label>
		<Textarea placeholder="Type your message here." id="message-2" />
		<p class="text-sm text-muted-foreground">Your message will be copied to the support team.</p>
	</div>

	<Toggle aria-label="Toggle italic">
		<Icon icon="lucide:italic" class="mr-2 h-4 w-4" />
		Italic
	</Toggle>

	<Tooltip.Root>
		<Tooltip.Trigger asChild let:builder>
			<Button builders={[builder]} variant="outline">Hover</Button>
		</Tooltip.Trigger>
		<Tooltip.Content>
			<p>Add to library</p>
		</Tooltip.Content>
	</Tooltip.Root>
</main>
