<template>
    <view class="list__cell" @tap="_clickMessage()">
        <view class="list__head">
            <view class="list__name">
                {{options.ship_name}}
                <view class="list__helper">
                    {{options.ship_type}}
                </view>
                <view class="list__helper">
                    {{options.load_amount}}吨
                </view>
            </view>
            <text class="list__update">
                {{options.resDate}}
            </text>
        </view>
        <view class="list__main">
            <view class="list__info list__hr">
                <view class="list__label">
                    空船期
                </view>
                <view class="list__note">
                    {{options.resEmpty}}
                </view>
            </view>
            <view class="list__info">
                <view class="list__label">
                    空船地
                </view>
                <view class="list__note" style="fontsize: 5upx">
                    {{options.departure_na}}
                </view>
            </view>
            <image class="list__imgRight" src="/static/img/sail_right.png" mode="scaleToFill"></image>
            <view class="list__info">
                <view class="list__label">
                    目的地
                </view>
                <view class="list__note" style="fontsize:5upx ">
                    {{options.target_na}}
                </view>
            </view>
        </view>
    </view>
</template>

<script>
    export default {
        props: {
            options: {
                type: Object
            },
            index: {
                type: Number
            }
        },
        computed:{
            
        },
        methods: {
            _clickMessage() {
				this.$emit('click', {index: this.index, type: 'ship_market'});
            }
        },
    }
</script>

<style lang="scss">
    @import '@/style/mixin/flex.scss';
    @import '@/style/mixin/hr.scss';
    @import '@/style/mixin/text-overflow.scss';
    
    .list{
        &__cell{
            @include flex(null, null, column);
            margin-bottom: $uni-spacing-col-base;
            background-color: #fff;
        }
        
        &__head{
            @include flex(between, center);
            position: relative;
            height: 48px;
            padding: 0 $uni-spacing-row-base;
            color: $uni-text-color-grey;
            font-size: $uni-font-size-sm;
            
            &::after{
                @include hr(bottom, 24rpx);
            }
        }
        
        &__name{
            @include flex();
            color: $color-main;
            font-size: $uni-font-size-base;
        }
        
        &__helper{
            padding-left: $uni-spacing-row-base;
            color: #aaa;
        }
        
        &__update{
            font-size: $uni-font-size-xs;
            color: #ccc;
        }
        
        &__main{
            @include flex(null, center);
            padding: $uni-spacing-col-lg $uni-spacing-row-base 36rpx;
        }
        
        &__info{
            flex: auto;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            min-height: 48px;
            width: 180rpx;
            line-height: 1;
        }
        
        &__label{
            color: #aaa;
            font-size: $uni-font-size-sm;
        }
        
        &__note{
            text-align: center;
            color: $uni-text-color;
            font-size: 16px;
            line-height: 16px;
            font-weight: 700;
            @include text-overflow(100%);
        }
        
        &__imgRight{
            flex: none;
            display: block;
            width: 50rpx;
            height: 10px;
            margin: 0 $uni-spacing-row-base;
        }
        
        &__hr{
            flex: none;
            position: relative;
            box-sizing: border-box;
            padding-right: $uni-spacing-row-base;
            margin-right: $uni-spacing-row-base;
            min-width: 180rpx;
            
            &::after{
                @include hr(right);
            }
        }
    }
</style>
