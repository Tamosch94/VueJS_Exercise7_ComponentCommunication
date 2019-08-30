<template>
    <div class="col-xs-12 col-sm-6">
        <p>{{ serverId }} {{ serverStat }}</p>
		<button
			type="button"
			name="button"
			v-if="serverStat != ''"
			@click="changeServerStat">Change Stat to normal
		</button>
    </div>

</template>

<script>
	import { eventBus } from '../../main.js';
	export default {
		data: function() {
			return {
				serverId: '',
				serverStat: ''
			}
		},
		methods: {
			changeServerStat() {
				eventBus.$emit('changeServerStatus', [this.serverId, 'Normal'])
			}
		},
		created() {
			eventBus.$on('sendServerId', (data) => {
				this.serverId = data
			});
			eventBus.$on('sendServerStatus', (data) => {
				this.serverStat = data
			});
		},

	}
</script>

<style>

</style>
