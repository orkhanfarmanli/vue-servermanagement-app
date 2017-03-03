<template>
<div class="row">
	<div class="col-xs-12">
		<header>
			<h1>Server Management App</h1>
			<p class="pull-left">Online Servers: {{ online }} 	&nbsp;</p>
			<p class="pull-left">Offline Servers: {{ offline }} 	&nbsp;</p>
		</header>
	</div>
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
