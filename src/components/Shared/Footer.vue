<template>
<div class="col-xs-12">
	<footer>
		<p>Server action logs:</p>
		<ul>
			<li v-for="log in logs" v-html="log"></li>
		</ul>
	</footer>
</div>
</template>

<script>
	export default{
		props: ['logs']
	}
</script>
