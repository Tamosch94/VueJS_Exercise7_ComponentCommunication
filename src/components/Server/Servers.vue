<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
			<server-list
				v-for="(object, value) in servers"
				:serverId= "object.id"
				:serverStatus = "object.status"
				>
			</server-list>
        </ul>
    </div>
</template>

<script>
	// Tasks:
	// 1. create custom component which holds the list item
	// 2. define an array of servers (id and val) and fill in the props in the server.vue file
	import Server from './Server.vue';
	import { eventBus } from '../../main.js';
	export default {
		// NOTE: instead of using multiple event busses you could have used the servers data prop as props also keep in mind that you
		// could have changed the object directly in the  serverdetails vue cause an object or array is a ref type !!
		// That means it referenced by a pointer
		data: function() {
			return {
				servers: [
					{id: 1, status: 'Normal'},
					{id: 2, status: 'Critical'},
					{id: 3, status: 'Unknown'},
					{id: 4, status: 'Normal'},
					{id: 5, status: 'Pending'},
				]
			}
		},
		components: {
			'server-list': Server
		},
		methods: {
		},
		created() {
			eventBus.$on('changeServerStatus', (data) => {
				this.servers[data[0] - 1].status = data[1];
			});
		}
	}
</script>

<style>

</style>
