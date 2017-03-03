<template>
<div class="col-xs-12">
	<footer>
		<p>All Servers are managed here:</p>
		<p>Online Servers: {{ online }}</p>
		<p>Offline Servers: {{ offline }}</p>
	</footer>
</div>
</template>
<script>
	export default{
		props: ['offline', 'online'],
		data(){
			return {
			}
		}
	}
	
</script>