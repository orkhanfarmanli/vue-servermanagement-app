<template>
<div>
	<div class="row">
		<server-header :offline="offlineServers" :online="onlineServers"></server-header>
	</div>
	<hr>
	<div class="row">
		<div class="col-xs-12 col-sm-6">
			<ul class="list-group">
				<li v-for="server in servers" class="list-group-item">
					<a class="pull-left">
						<i :style="{ color: server.status ? '#00c853' : '#d50000' }" class="fa fa-linux" aria-hidden="true"></i>
					</a>
					&nbsp; {{ server.name }}
					<a class="pull-right" @click="changeServerStatus(server)">
						<span class="btn btn-default badge">Switch State</span>
					</a>
					<a class="pull-right" @click="showServer(server)">
						<span class="btn btn-default badge">Show</span>
					</a>
				</li>
			</ul>
		</div>
		<div class="col-xs-12 col-sm-6">
			<server-details :server="currentServer"></server-details>
		</div>
	</div>
	<hr>
	<div class="row">
		<server-footer :logs="serverLog"></server-footer>
	</div>
</div>
</template>
<script>
	import ServerDetails from "./ServerDetails.vue";
	import ServerHeader from "../Shared/Header.vue";
	import ServerFooter from "../Shared/Footer.vue";
	export default {

		components: {
			"server-details": ServerDetails,
			"server-header": ServerHeader,
			"server-footer": ServerFooter
		},

		data(){
			return {
				servers: [
					{
						name: "Zakirin serveri",
						status: true,
						specs: {
							cpu: "8 core",
							ram: "16gb",
							storage: "256gb"
						}
					},
					{
						name: "Kamilin Serveri",
						status: false,
						specs: {
							cpu: "12 core",
							ram: "32gb",
							storage: "512gb"
						}
					},
					{
						name: "Amilin Serveri",
						status: true,
						specs: {
							cpu: "2 core",
							ram: "2gb",
							storage: "20gb"
						}
					},
					{
						name: "Akifin Serveri",
						status: true,
						specs: {
							cpu: "28 core",
							ram: "64gb",
							storage: "1tb"
						}
					}
				],
				currentServer: '',
				serverLog: []
			}
		},

		methods: {
			changeServerStatus(server){
				server.status = !server.status;
				this.showServer(server);
				this.logAction(server);
			},
			showServer(server){
				this.currentServer = server;
			},
			logAction(server){
				this.serverLog.push("<b>"+server.name+"</b>" + " turned " + (server.status ? "on" : "off"));
			}
		},

		computed: {
			onlineServers: function(){
				var onlines = this.servers.filter(function(server){
					return server.status === true
				});
				return onlines.length;
			},
			offlineServers: function(){
				var offlines = this.servers.filter(function(server){
					return server.status === false
				});
				return offlines.length;
			}
		}

	}
</script>
