<template>
	<section class="home">
		<div class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
			<div class="flex flex-col w-full xl:w-5/12 justify-center lg:items-start overflow-y-hidden">
				<div v-html="$md.render(welcomeText)" class="home__welcome markdown"/>
			</div>
			<div class="flex flex-col w-full xl:w-7/12">
				<img class="rounded shadow-xl" src="https://source.unsplash.com/random/720x400?code"/>
			</div>
		</div>

		<div class="py-20 pb-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-start">
			<div class="flex flex-col pr-10 w-full xl:w-3/6 justify-start lg:items-start overflow-y-hidden">
				<div v-html="$md.render(tailoredText)" class="home__about markdown"/>
			</div>

			<div class="flex flex-col pl-10 w-full xl:w-3/6 justify-start lg:items-start overflow-y-hidden">
				<div v-html="$md.render(developedText)" class="home__about markdown"/>
			</div>
		</div>
	</section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import settings from '@/content/settings/general.json';

@Component({
	transition() {
		return 'slide-left';
	},
})
export default class Home extends Vue {
	welcomeText = settings.welcomeText;

	tailoredText = settings.tailoredText;

	developedText = settings.developedText;

	get posts(): Post[] {
		return this.$store.state.posts;
	}
}
</script>
