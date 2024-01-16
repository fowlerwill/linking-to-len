<script>
	import { Container, Image, Button, Input } from 'sveltestrap';
	import { browser } from '$app/environment';
	
	import coverTop from '$lib/images/cover_front-no-title.png';
	import coverBottom from '$lib/images/cover_back.png';
	
	const epub = 'https://linking-to-len.s3.amazonaws.com/Linking_To_Len.epub';
	const pdf = 'https://linking-to-len.s3.amazonaws.com/Linking_To_Len.pdf';
	const fundraiser = 'https://www.justgiving.com/campaign/ccef-donboscoschool?utm_source=copyLink&utm_medium=one_page&utm_content=campaign/ccef-donboscoschool&utm_campaign=pfp-share&utm_term=ee727817bb294315b12147b6f77e2ff1';
	const softcover = 'https://www.amazon.ca/dp/B0CR7W1BF3';

	let stepOne = false;
	let stepTwo = false;

	import JSConfetti from 'js-confetti'
	
	function confetti() {
		if (!browser) return;
		const jsConfetti = new JSConfetti();
		jsConfetti.addConfetti();
	}


	
</script>

<svelte:head>
	<title>Linking To Len</title>
	<meta name="description" content="Linking To Len" />
	<script src="https://cdn.jsdelivr.net/npm/js-confetti@latest/dist/js-confetti.browser.js"></script>
</svelte:head>

<section>
	<Container sm class="py-5 mx-auto" style="max-width: 768px;">
		<h1 class="display-5 fw-bold">
			Linking to Len
		</h1>
		
		<Image fluid src={coverTop} style="width: 100%;" />

		<h2 class="my-4">
			A project by the students, parents, and teachers of Don Bosco School to
			raise awareness for our playground fundraiser.
		</h2>

		<p class="my-4">
			We are raising money to build a playground for the students of Don Bosco 
			School in Calgary. To help raise awareness, we have created a children's 
			book with artwork created by the students themselves, a sprinkle of text from
			ChatGPT, and some extensive editing from the parents.
		</p>



		<div class="h-100 my-4 p-5 bg-body-tertiary border rounded-3">
		
		<h2 class="my-4">
			How you can help in a three simple steps:
		</h2>
		
		<ol class="my-4">
			<li>Make a donation at the <a target="_blank" href={fundraiser}>fundraiser page</a>, then</li>
			<li>Share this page with your friends and family, then</li>
			<li>Download the eBook here, or order a printed copy</li>
		</ol>

	</div>


		<h2 class="my-4">
			Ready?
		</h2>

		<h3 class="my-4">
			Step 1: Make your donation
		</h3>

		<Button color="primary" size="lg" target="_blank" href={fundraiser} class="mx-auto">
			Click here to donate
		</Button>

		<p class="my-4">
			When you make your donation, you will be asked to leave a message. You can
			write whatever you like, but we suggest you write something to <i>...link</i> back to the book:
			<br />
			"Let's build a playground! #LinkingToLen"
		</p>

		<div class="my-4 p-2 bg-body-tertiary border rounded-3" on:click={confetti}>
			<Input type="checkbox" label="I promise I have made a donation, and am ready to continue" bind:checked={stepOne} />
		</div>

		{#if stepOne}

		<h3 class="my-4">
			Step 2: Share this page
		</h3>

		<p class="my-4">
			The best driver of donations is word of mouth. The more people who know
			about this project, the more likely we are to reach our goal! So please 
			share this page with your friends and family and ask them to do the same.
		</p>

		<p class="my-4">
			You can share this page using Facebook, Twitter, Instagram, TikTok, 
			LinkedIn, or any other social media platform you like.
		</p>

		<div class="my-4 p-2 bg-body-tertiary border rounded-3" on:click={confetti}>
			<Input type="checkbox" label="I promise I have shared this page, and am ready to continue" bind:checked={stepTwo} />
		</div>
		
		{/if}

		{#if stepOne && stepTwo}
		<h3 class="my-4">
			Step 3: Get a copy of the book
		</h3>

		<p class="my-4">
			We have created a digital version, which you can download for free here 👇
		</p>

		<div class="mx-auto">

			<Button color="primary" size="lg" target="_blank" href={epub}>
				Download (.epub)
			</Button>
			
			<Button color="primary" size="lg" target="_blank" href={pdf}>
				Download (.pdf)
			</Button>
		</div>

		<h4 class="my-4">
			-- AND / OR --
		</h4>

		<p class="my-4">
			We have also created a printed version of the book on Amazon that is being
			sold at cost.
		</p>

		<p class="my-4">
			We make no money from this, the cost only covers printing and shipping, so please make sure you've donated (you promised!).
		</p>

		<Button color="primary" size="lg" target="_blank" href={softcover}>
			Order (Amazon)
		</Button>

		<Image fluid src={coverBottom} style="width: 100%;" />

		<p class="h1 my-5 text-center">
			Thank you for your support!
		</p>

		{/if}

	</Container>
	

</section>

<style>
</style>
