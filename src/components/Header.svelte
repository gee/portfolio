<script lang="ts">
	import { onMount } from 'svelte';

	let currentSection = 'about';
	const offset = 144; // lg:mb-36

	onMount(() => {
		const onScroll = () => {
			const aboutSection = document.getElementById('about');
			const experienceSection = document.getElementById('experience');
			const projectsSection = document.getElementById('projects');

			const aboutPosition = aboutSection.getBoundingClientRect();
			const experiencePosition = experienceSection.getBoundingClientRect();
			const projectsPosition = projectsSection.getBoundingClientRect();

			if (aboutPosition.top - offset <= 0 && experiencePosition.top - offset > 0) {
				currentSection = 'about';
			} else if (experiencePosition.top - offset <= 0 && projectsPosition.top - offset > 0) {
				currentSection = 'experience';
			} else if (projectsPosition.top - offset <= 0) {
				currentSection = 'projects';
			}
			console.log(currentSection);
		};

		window.addEventListener('scroll', onScroll);
		return () => window.removeEventListener('scroll', onScroll);
	});
</script>

<header
	class="lg:sticky lg:top-0 lg:flex lg:max-h-screen lg:w-1/2 lg:flex-col lg:justify-between lg:py-24"
>
	<div>
		<h1 class="text-4xl font-bold tracking-tight text-slate-200 sm:text-5xl">
			<a href="/">Peter Gee</a>
		</h1>
		<h2 class="mt-3 text-lg font-medium tracking-tight text-slate-200 sm:text-xl">
			Software Engineer
		</h2>
		<p class="mt-4 max-w-xs leading-normal">
			I build exceptional and accessible digital experiences for the web.
		</p>
		<nav class="nav hidden lg:block" aria-label="In-page jump links">
			<ul class="mt-16 w-max">
				<li>
					<a class="group flex items-center py-3" href="#about"
						><span
							class={'nav-text text-lg font-bold uppercase tracking-widest group-hover:text-slate-200 group-focus-visible:text-slate-200' +
								(currentSection === 'about' ? ' text-slate-200' : ' text-slate-500')}>About</span
						></a
					>
				</li>
				<li>
					<a class="group flex items-center py-3" href="#experience"
						><span
							class={'nav-text text-lg font-bold uppercase tracking-widest group-hover:text-slate-200 group-focus-visible:text-slate-200' +
								(currentSection === 'experience' ? ' text-slate-200' : ' text-slate-500')}
							>Experience</span
						></a
					>
				</li>
				<li>
					<a class="group flex items-center py-3" href="#projects"
						><span
							class={'nav-text text-lg font-bold uppercase tracking-widest group-hover:text-slate-200 group-focus-visible:text-slate-200' +
								(currentSection === 'projects' ? ' text-slate-200' : ' text-slate-500')}
							>Projects</span
						></a
					>
				</li>
			</ul>
		</nav>
	</div>
	<ul class="ml-1 mt-8 flex items-center" aria-label="Social media">
		<li class="mr-5 text-xs">
			<a
				class="block hover:text-slate-200"
				href="https://www.linkedin.com/in/bchiang7/"
				target="_blank"
				rel="noreferrer noopener"
				aria-label="LinkedIn (opens in a new tab)"
				><span class="sr-only">LinkedIn</span><svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="currentColor"
					class="h-8 w-8"
					aria-hidden="true"
					><path
						d="M20.5 2h-17A1.5 1.5 0 002 3.5v17A1.5 1.5 0 003.5 22h17a1.5 1.5 0 001.5-1.5v-17A1.5 1.5 0 0020.5 2zM8 19H5v-9h3zM6.5 8.25A1.75 1.75 0 118.3 6.5a1.78 1.78 0 01-1.8 1.75zM19 19h-3v-4.74c0-1.42-.6-1.93-1.38-1.93A1.74 1.74 0 0013 14.19a.66.66 0 000 .14V19h-3v-9h2.9v1.3a3.11 3.11 0 012.7-1.4c1.55 0 3.36.86 3.36 3.66z"
					></path></svg
				></a
			>
		</li>
	</ul>
</header>
