<template>
	<uni-indexed-list :options="list" :show-select="false" @click="bindClick" />
</template>

<script>
	import uniIndexedList from './uni-indexed-list.vue';
    import { router, toast } from '@/common/util.js';
    
    import { mapState, mapActions, mapMutations } from 'vuex';
    
	export default {
		components: {
			uniIndexedList
		},
		data() {
			return {
				list: []
			}
		},
        computed: mapState(['dictionaryTempData']),
        async onLoad(options) {
            toast.loading('加载中');
            if(!this.dictionaryTempData.hasOwnProperty('banks') || !this.dictionaryTempData.banks.length){
                await this.getBankType();
            }
            this.list = this.dictionaryTempData.banks;
            toast.hideLoading();
        },
		methods: {
            ...mapActions(['getBankType']),
            ...mapMutations(['PAGE_TEMP_UPDATA']),
			bindClick(e) {
                this.PAGE_TEMP_UPDATA(e.item.name);
                router.navigateBack();
			}
		}
	}
</script>

<style>
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4
	}

	view {
		font-size: 28upx;
		line-height: inherit
	}

	.example {
		padding: 0 30upx 30upx
	}

	.example-title {
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 32upx;
		color: #464e52;
		padding: 30upx 30upx 30upx 50upx;
		margin-top: 20upx;
		position: relative;
		background-color: #fdfdfd;
		border-bottom: 1px #f5f5f5 solid
	}

	.example-title__after {
		position: relative;
		color: #031e3c
	}

	.example-title:after {
		content: '';
		position: absolute;
		left: 30upx;
		margin: auto;
		top: 0;
		bottom: 0;
		width: 6upx;
		height: 32upx;
		background-color: #ccc
	}

	.example .example-title {
		margin: 40upx 0
	}

	.example-body {
		padding: 30upx;
		background: #fff
	}

	.example-info {
		padding: 30upx;
		color: #3b4144;
		background: #fff
	}
</style>