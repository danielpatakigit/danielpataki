<script lang="ts">
	import Resume from "$lib/documents/Dániel Pataki - Resume.pdf";

	let projects: any = [
		{
			name: "Naspolya Photography",
			description:
				"Photographer portfolio website made for a relative. Sveltekit as frontend, Planetscale free tier as backend. Hosted on Vercel",
			tag: "Online",
			url: "https://www.naspolyaphoto.hu",
		},
		{
			name: "Enrol Consulting Website",
			description:
				"Company website design and implementation for a relative's IT firm.",
			tag: "Online",
			url: "https://www.enrol.hu",
		},
		{
			name: "Oracle Database Developer",
			description:
				"My starter JS project. Allows you to easily model a simple database and generate Oracle SQL.",
			tag: "Unavailable",
			url: "",
		},
		{
			name: "Svelte Gomoku",
			description:
				"My starter Svelte project. Simple Gomoku game. Can only be played with 2 players. Hosted on Vercel",
			tag: "Online",
			url: "https://gomokusvelte.vercel.app/",
		},
	];
</script>

<main
	id="page-wrapper"
	class=" h-screen flex justify-center items-center p-4"
>
	<article class="w-[min(100%,_45rem)] flex flex-col gap-5">
		<div
			id="heading"
			class="flex gap-5 flex-col items-center"
		>
			<h1 class="text-5xl">Dániel Pataki</h1>
			<a
				href={Resume}
				download="Dániel Pataki CV English"
				class="bg-white hover:bg-gray-200 text-black font-bold py-2 px-4 rounded-2xl inline-flex items-center gap-1 transition-all w-min"
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
									: 'bg-gray-400 text-gray-800'}
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
	</article>
</main>
