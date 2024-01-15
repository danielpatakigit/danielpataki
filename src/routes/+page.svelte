<script lang="ts">
	import Icon from "@iconify/svelte";
	import Resume from "$lib/documents/Dániel Pataki - Resume.pdf";
	import { blur, fade, fly } from "svelte/transition";
	import { onMount } from "svelte";
	let projects: any = [
		{
			type: "website",
			name: "Naspolya Photography",
			description:
				"Photographer portfolio website made for a relative. Sveltekit as frontend, Planetscale as storage for the dynamic gallery section.",
			show: true,
			url: "https://www.naspolyaphoto.hu",
			icon: "/naspolya_favicon.png",
			img: [],
			column: 2,
		},
		{
			type: "website",
			name: "Enrol Website",
			description:
				"Company website design and implementation for a small Hungarian IT firm with vanilla technologies. Soon to be ported over to Svelte.",
			show: true,
			url: "https://www.enrol.hu",
			icon: "/enrol_favicon.png",

			img: [],
			column: 3,
		},
		{
			type: "website",
			name: "FS Winf",
			description:
				"Soon to be finished modernization of the TUW business informatics student union website.",
			show: true,
			url: "https://fswinf-at.vercel.app/en",
			icon: "/fswinf_favicon.png",

			img: [],
			column: 1,
		},
		{
			type: "design",
			name: "Microkit Logo",
			description:
				"Logo designed for Microkit, a small business dealing in veterniary products.",
			show: false,
			url: "",
			icon: "",

			img: [
				"microkit_businesscard_mockup.jpg",

				"microkit_logo_blue.png",
			],
			column: 3,
		},
		{
			type: "design",
			name: "Winfnachten Poster",
			description:
				"Poster designed to promote the Christmas party of FS Winf throughout the TUW campus.",
			show: false,
			url: "",
			icon: "",
			img: ["winfnachten_poster.png"],
			column: 2,
		},

		{
			type: "app",
			name: "Svelte Gomoku",
			description:
				"My starter Svelte project. Simple Gomoku game. Can only be played with 2 players.",
			show: true,
			url: "https://gomokusvelte.vercel.app/",
			icon: "",

			img: [],
			column: 2,
		},
		{
			type: "design",
			name: "Enrol Logo",
			description: "Logo designed for Enrol.",
			show: false,
			url: "",
			icon: "/enrol_favicon.png",

			img: ["enrol logo 1.png"],
			column: 1,
		},
		// {
		// 	type: "app",
		// 	name: "Oracle Database Developer",
		// 	description:
		// 		"My starter JS project. Allows you to easily model a simple database and generate Oracle SQL.",
		// 	show: false,
		// 	url: "",
		// 	icon: "",

		// 	img: [],
		// 	column: 1,
		// },
	];

	let ready = false;
	onMount(() => {
		ready = true;
	});
</script>

<main
	id="page-wrapper"
	class="  flex justify-center items-center gradient bg-zinc-950 text-white"
>
	{#if ready}
		<div class="h-full w-full grain p-4">
			<div
				class=" w-[min(100%,_55rem)] m-auto h-full flex flex-col gap-12"
			>
				<div
					in:fade={{ duration: 1800, delay: 600 }}
					class="flex flex-col md:flex-row items-center text-center mt-32 md:mt-40 md:text-left gap-12"
				>
					<img
						class="w-80 rounded-full h-full"
						src="/danielpataki.jpg"
						alt="Daniel Pataki"
					/>
					<div class="flex flex-col my-auto">
						<span class="italic font-light text-xl">
							Hello
							<span class="text-fuchsia-500">!</span>
						</span>
						<h1
							class="font-bold text-6xl mt-4 decoration-fuchsia-500 underline underline-offset-8"
						>
							Dániel Pataki
						</h1>
						<ul class=" mt-8 gap-2 flex flex-col italic">
							<li>
								<span class="text-fuchsia-500 font-bold">-</span>
								Maturing full-stack developer
							</li>
							<li>
								<span class="text-fuchsia-500 font-bold">-</span>
								Enrolled in TU Wien business informatics
							</li>
						</ul>
					</div>
				</div>

				<div
					in:fly={{
						delay: 150,
						duration: 1500,
						x: 0,
						y: 50,
						opacity: 0,
					}}
					class=" w-max mx-auto rounded-full p-4 flex flex-wrap justify-center gap-6 md:bg-zinc-900 mt-4"
					style="background-color: 0"
				>
					<a
						href={Resume}
						download="Dániel Pataki CV English"
						class="quicklink"
					>
						<Icon
							icon="mdi:resume"
							width="30"
						></Icon>
						<span class="font-semibold">Resume Download</span>
					</a>
					<a
						href="https://github.com/danielpatakigit"
						target="_blank"
						class="quicklink"
					>
						<Icon
							icon="mdi:github"
							width="30"
						></Icon>
						<span class="font-semibold">GitHub</span>
					</a>
					<a
						href="https://www.linkedin.com/in/d%C3%A1niel-pataki-55b35124b/"
						target="_blank"
						class="quicklink"
					>
						<Icon
							icon="mdi:linkedin"
							width="30"
						></Icon>
						<span class="font-semibold">LinkedIn</span>
					</a>
				</div>
				<h2
					in:fly={{
						delay: 300,
						duration: 1200,
						x: 0,
						y: 50,
						opacity: 0,
					}}
					class="font-bold mx-auto text-3xl mt-8"
				>
					Check out my work
					<span class="text-fuchsia-500">!</span>
				</h2>
				<div
					in:fly={{
						delay: 500,
						duration: 2000,
						x: 0,
						y: 50,
						opacity: 0,
					}}
					class="h-full w-full p-4 rounded-3xl gap-4 grid md:grid-cols-3 grid-cols-1 bg-zinc-900"
				>
					{#each Array(3) as _, i}
						<div class="flex flex-col gap-4">
							{#each projects as project, j}
								{#if project.column - 1 === i}
									<article
										class="bg-zinc-950 p-4 rounded-2xl flex flex-col gap-3"
									>
										{#if project.img.length >= 1}
											<div class="flex flex-col gap-4">
												{#each project.img as src, k}
													<img
														class="bg-white rounded-lg p-2"
														src="/{src}"
														alt="{project.title} illustration"
														loading="lazy"
													/>
												{/each}
											</div>
										{/if}

										<div class="flex items-center gap-4">
											<div
												class="aspect-square h-12 bg-zinc-900 rounded-lg flex justify-center text-center items-center"
											>
												{#if project.icon}
													{#if project.icon.charAt(0) === "/"}
														<img
															class="rounded-lg"
															src={project.icon}
															alt="project icon"
															loading="lazy"
														/>
													{:else}
														<Icon
															width="36"
															icon={project.icon}
														></Icon>
													{/if}
												{:else}
													<span
														class="font-bold text-xl italic font-serif text-fuchsia-300"
													>
														{project.name.charAt(0)}
													</span>
												{/if}
											</div>
											<h3 class="font-semibold text-xl">
												{project.name}
											</h3>
										</div>
										<div class="font-normal text-gray-300">
											{project.description}
										</div>
										<div>
											{#if project.url}
												<a
													target="_blank"
													href={project.url}
													class="hover:text-fuchsia-500 underline italic font-bold decoration-fuchsia-500 underline-offset-4"
												>
													check it out
												</a>
											{/if}
										</div>
									</article>
								{/if}
							{/each}
						</div>
					{/each}
				</div>
				<div
					class="mx-auto font-thin flex justify-center items-center gap-2"
				>
					made with Svelte and <span
						class="font-bold text-fuchsia-500"
					>
						<Icon icon="mdi:heart"></Icon>
					</span>
				</div>
			</div>
		</div>

		<!-- <article class="w-[min(100%,_45rem)] flex flex-col gap-5">
		<div
			id="heading"
			class="flex gap-5 flex-col items-center"
		>
			<h1 class="text-5xl">Dániel Pataki</h1>
			<a
				href={Resume}
				download="Dániel Pataki CV English"
				class="bg-white hover:bg-zinc-200 text-black font-bold py-2 px-4 rounded-2xl inline-flex items-center gap-1 transition-all w-min"
			>
				<svg
					class="fill-black w-4 h-4 mr-2"
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 20 20"
				>
					<path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z" />
				</svg>
				<span class="text-inherit">Resume</span>
			</a>
		</div>
		<section class=" flex flex-col gap-8 items-center">
			<h2 class="text-xl mt-4">Some of my work</h2>
			<div class="flex flex-col gap-8">
				{#each projects as project, i}
					<a
						id="work"
						href={project.url == ""
							? "javascript:void(0);"
							: project.url}
						target={project.url == "" ? "" : "_blank"}
						class={project.url == ""
							? ""
							: "hover:opacity-70 transition-opacity"}
					>
						<h3 class="text-lg inline-flex gap-3 items-center">
							<span>{project.name}</span>
							<span
								class="{project.tag == 'Online'
									? 'bg-white text-black'
									: 'bg-zinc-400 text-zinc-800'}
								text-sm font-sans rounded-full px-2 py-[1px] flex items-center h-min font-medium gap-1"
							>
								<span class="text-inherit">{project.tag}</span>

								{#if project.tag == "Online"}
									<iconify-icon
										icon="mdi:open-in-new"
										class="text-inherit"
									></iconify-icon>
								{/if}
							</span>
						</h3>
						<p class="font-extralight">{project.description}</p>
					</a>
				{/each}
			</div>
		</section>
	</article> -->
	{/if}
</main>

<style lang="postcss">
	* {
		@apply transition-colors;
	}

	.quicklink {
		@apply flex w-max items-center gap-2 rounded-full border px-3 py-1 hover:border-fuchsia-500 hover:text-fuchsia-500;
	}
	.gradient {
		/* background-image: radial-gradient(
			circle farthest-corner at 10% 20%,
			rgb(81, 31, 95) 0%,
			rgba(4, 0, 4, 1) 90%
		); */
	}

	.grain {
		/* background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAMAAAAp4XiDAAAAUVBMVEWFhYWDg4N3d3dtbW17e3t1dXWBgYGHh4d5eXlzc3OLi4ubm5uVlZWPj4+NjY19fX2JiYl/f39ra2uRkZGZmZlpaWmXl5dvb29xcXGTk5NnZ2c8TV1mAAAAG3RSTlNAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEAvEOwtAAAFVklEQVR4XpWWB67c2BUFb3g557T/hRo9/WUMZHlgr4Bg8Z4qQgQJlHI4A8SzFVrapvmTF9O7dmYRFZ60YiBhJRCgh1FYhiLAmdvX0CzTOpNE77ME0Zty/nWWzchDtiqrmQDeuv3powQ5ta2eN0FY0InkqDD73lT9c9lEzwUNqgFHs9VQce3TVClFCQrSTfOiYkVJQBmpbq2L6iZavPnAPcoU0dSw0SUTqz/GtrGuXfbyyBniKykOWQWGqwwMA7QiYAxi+IlPdqo+hYHnUt5ZPfnsHJyNiDtnpJyayNBkF6cWoYGAMY92U2hXHF/C1M8uP/ZtYdiuj26UdAdQQSXQErwSOMzt/XWRWAz5GuSBIkwG1H3FabJ2OsUOUhGC6tK4EMtJO0ttC6IBD3kM0ve0tJwMdSfjZo+EEISaeTr9P3wYrGjXqyC1krcKdhMpxEnt5JetoulscpyzhXN5FRpuPHvbeQaKxFAEB6EN+cYN6xD7RYGpXpNndMmZgM5Dcs3YSNFDHUo2LGfZuukSWyUYirJAdYbF3MfqEKmjM+I2EfhA94iG3L7uKrR+GdWD73ydlIB+6hgref1QTlmgmbM3/LeX5GI1Ux1RWpgxpLuZ2+I+IjzZ8wqE4nilvQdkUdfhzI5QDWy+kw5Wgg2pGpeEVeCCA7b85BO3F9DzxB3cdqvBzWcmzbyMiqhzuYqtHRVG2y4x+KOlnyqla8AoWWpuBoYRxzXrfKuILl6SfiWCbjxoZJUaCBj1CjH7GIaDbc9kqBY3W/Rgjda1iqQcOJu2WW+76pZC9QG7M00dffe9hNnseupFL53r8F7YHSwJWUKP2q+k7RdsxyOB11n0xtOvnW4irMMFNV4H0uqwS5ExsmP9AxbDTc9JwgneAT5vTiUSm1E7BSflSt3bfa1tv8Di3R8n3Af7MNWzs49hmauE2wP+ttrq+AsWpFG2awvsuOqbipWHgtuvuaAE+A1Z/7gC9hesnr+7wqCwG8c5yAg3AL1fm8T9AZtp/bbJGwl1pNrE7RuOX7PeMRUERVaPpEs+yqeoSmuOlokqw49pgomjLeh7icHNlG19yjs6XXOMedYm5xH2YxpV2tc0Ro2jJfxC50ApuxGob7lMsxfTbeUv07TyYxpeLucEH1gNd4IKH2LAg5TdVhlCafZvpskfncCfx8pOhJzd76bJWeYFnFciwcYfubRc12Ip/ppIhA1/mSZ/RxjFDrJC5xifFjJpY2Xl5zXdguFqYyTR1zSp1Y9p+tktDYYSNflcxI0iyO4TPBdlRcpeqjK/piF5bklq77VSEaA+z8qmJTFzIWiitbnzR794USKBUaT0NTEsVjZqLaFVqJoPN9ODG70IPbfBHKK+/q/AWR0tJzYHRULOa4MP+W/HfGadZUbfw177G7j/OGbIs8TahLyynl4X4RinF793Oz+BU0saXtUHrVBFT/DnA3ctNPoGbs4hRIjTok8i+algT1lTHi4SxFvONKNrgQFAq2/gFnWMXgwffgYMJpiKYkmW3tTg3ZQ9Jq+f8XN+A5eeUKHWvJWJ2sgJ1Sop+wwhqFVijqWaJhwtD8MNlSBeWNNWTa5Z5kPZw5+LbVT99wqTdx29lMUH4OIG/D86ruKEauBjvH5xy6um/Sfj7ei6UUVk4AIl3MyD4MSSTOFgSwsH/QJWaQ5as7ZcmgBZkzjjU1UrQ74ci1gWBCSGHtuV1H2mhSnO3Wp/3fEV5a+4wz//6qy8JxjZsmxxy5+4w9CDNJY09T072iKG0EnOS0arEYgXqYnXcYHwjTtUNAcMelOd4xpkoqiTYICWFq0JSiPfPDQdnt+4/wuqcXY47QILbgAAAABJRU5ErkJggg==); */
	}
</style>
