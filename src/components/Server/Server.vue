<template lang="html">
	<li class="list-group-item" @click="loadServer">
		ServerId: {{ serverId }} - ServerStatus: {{ serverStatus }}
	</li>
</template>

<script>
	import { eventBus } from '../../main.js';
	export default {

		props: ['serverId', 'serverStatus'],
		methods: {
			loadServer() {
				eventBus.$emit('sendServerId', this.serverId);
				eventBus.$emit('sendServerStatus', this.serverStatus);
			}
		}

	}
</script>

<style lang="css" scoped>
</style>
