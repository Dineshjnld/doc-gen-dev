<script lang="ts">
	import Intro from '$lib/Intro.svelte';

	export let data;

	// start
	let companyName = '';
	let websiteName = '';
	let cookies = '';
	let policyUrl = '';
	let email = '';
	let showTerms = true; // A variable to control the visibility of the h2 and Copy button


	let CookiesPolicy = '';

	function handleSubmit() {
		// Capture the user's input
		companyName = companyName.trim();
		websiteName = websiteName.trim();
		policyUrl = policyUrl.trim();

		const companyNameBold = `<strong>${companyName}</strong>`;

		// Generate the terms and policy content
		CookiesPolicy = `
	
	<strong>Cookies Policy for ${websiteName}</strong>

	What are cookies?

	Cookies are small text files that are placed on your computer by websites that you visit. They are used to store information about your browsing session, such as your language preferences, login information, and items in your shopping cart.

	Why do we use cookies?

	We use cookies to improve your user experience on our website. For example, we use cookies to:

	- Remember your language preferences so that you don't have to reset them each time you visit our website.
	- Keep you logged in so that you don't have to enter your login information each time you visit our website.
	- Track the items in your shopping cart so that you can easily checkout.
	- Collect analytics data so that we can understand how our website is being used and make improvements.

	<b><i>What types of cookies do we use?</i></b>

	We use two types of cookies on our website:

	- <b>Session cookies:</b> These cookies are deleted when you close your browser.
	- <b>Persistent cookies:</b> These cookies remain on your computer until they expire or are deleted.

	<b><i>How can I control my cookie settings?</i></b>

	You can control your cookie settings in your browser settings. Most browsers allow you to block or allow all cookies, or to block or allow cookies from specific websites. You can also clear your cookies at any time.

	<b>How to opt out of cookies</b>

	If you do not want to receive cookies from our website, you can opt out by changing your browser settings. However, please note that if you opt out of cookies, you may not be able to use all of the features of our website.

	<b>More information</b>

	For more information about cookies, please visit the following websites:

	- [All About Cookies](https://www.allaboutcookies.org)
	- [About Cookies](https://www.aboutcookies.org.uk)

	<b>Contact us</b>

	If you have any questions about our cookies policy, please contact us at ${email}.

    `;
		console.log(companyName);

		showTerms = false;
	}
</script>

<Intro heading={data.meta.title} description={data.meta.description} />

<div class=" bg-[#323A49] mt-2 w-1/2 container mx-auto py-8 flex flex-col items-center">
	<h1 class="text-3xl comp font-semibold mb-4 tw-text-red">Company Information</h1>
	<form on:submit={handleSubmit} class="space-y-4">
		<div class="flex flex-col">
			<label for="companyName" class="text-lg text-white">Company Name:</label>
			<input
				type="text"
				id="companyName"
				bind:value={companyName}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
			/>
		</div>
		<div class="flex flex-col">
			<label for="websiteName" class="text-lg text-white">Website Name:</label>
			<input
				type="text"
				id="websiteName"
				bind:value={websiteName}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
			/>
		</div>
		<div class="flex flex-col">
			<label for="websiteUrl" class="text-lg text-white">Cookies:</label>
			<input
				type="text"
				id="Cookies"
				bind:value={cookies}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
				required
			/>
		</div>
		<div class="flex flex-col">
			<label for="email" class="text-lg text-white">Company Email</label>
			<input
				type="email"
				id="email"
				bind:value={email}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
				placeholder="john.doe@company.com"
				required
			/>
		</div>
		<button
			type="submit"
			class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
		>
			Generate Cookies Policy
			<svg
				class="w-3.5 h-3.5 ml-2"
				aria-hidden="true"
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 14 10"
			>
				<path
					stroke="currentColor"
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M1 5h12m0 0L9 1m4 4L9 9"
				/>
			</svg>
		</button>
	</form>
</div>

<div class=" result w-1/2 content flex flex-col items-center justify-center mx-auto mt-8">
	{#if !showTerms}
			<button
				type="button"
				class="text-gray-900 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-200 font-medium rounded-full text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus:ring-gray-700"
				>Copy</button>
				{/if}
		{#if showTerms}
			<h2>Cookies Policy Will go here</h2>
			{/if}
			<div class="">{@html CookiesPolicy}</div>
</div>

<style>
	.content {
		padding: 20px;
		background-color: lightgray;
	}
	.comp {
		color: white;
	}
</style>
