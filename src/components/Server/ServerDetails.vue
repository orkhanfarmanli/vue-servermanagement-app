<template>
<div>
	<div  v-if="server" class="panel panel-default">
		<div class="panel-heading">
			{{ server.name }}
			<button class="pull-right btn" :class="server.status ? 'btn-success' : 'btn-danger'"></button>
		</div>
		<div class="panel-body">
			<p>CPU: {{ server.specs.cpu }}</p>
			<p>RAM: {{ server.specs.ram }}</p>
			<p>STORAGE: {{ server.specs.storage }}</p>
		</div>
	</div>
</div>
</template>
<script>
	export default{
		props: ['server']
	}
</script>