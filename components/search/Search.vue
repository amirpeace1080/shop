<template>
	<div class="ml-6">
		<p class="control has-icons-left">
		<input
			class="input is-rounded"
			type="text"
			v-model="value"
			:placeholder="placeholder"
			@keyup="search(value)"
		>
		<span class="icon is-small is-left">
			<i class="fa fa-search"></i>
		</span>
	</p>
	</div>
</template>

<script>
export default {
  name: 'search',
	data () {
		return {
			value: ''
		}
	},

	computed: {
		placeholder () {
			if (this.$route.path === '/wishlist') {
				return 'جستجو در لیست علاقه مندی ها';
			} else {
				return 'جستجو...';
			}
		}
	},

	methods: {
		search (value) {
			if (value.length > 0) {
				this.$store.commit('setHasUserSearched', true);
				this.$store.commit('setProductTitleSearched', value);
			} else {
				this.$store.commit('setHasUserSearched', false);
				this.$store.commit('setProductTitleSearched', '');
			}
		}
	}
}
</script>

