<template>
		<view class="text_box" v:for="i in steps">
		  {{i.instruction}}
		</view>


</template>

<script>
	var amapFile = require('../../common/amap-wx.130.js');
	// var config = require('../../common/config.js');
	
	Page({
	  data: {
	    steps: {}
	  },
	  onLoad: function() {
	    var that = this;
	    // var key = config.Config.key;
	    var myAmapFun = new amapFile.AMapWX({key:'986e3e528e41c7db57356cc78a3727a9'});
	    myAmapFun.getDrivingRoute({
	      origin: '116.481028,39.989643',
	      destination: '116.434446,39.90816',
	      success: function(data){
	        if(data.paths && data.paths[0] && data.paths[0].steps){
	          that.setData({
	            steps: data.paths[0].steps
	          });
	        }
	          
	      },
	      fail: function(info){
	
	      }
	    })
	  }
	})
</script>

<style>
.flex-style{
  display: -webkit-box;
  display: -webkit-flex;
  display: flex;
}
.flex-item{
  height: 35px; 
  line-height: 35px;
  text-align: center;
  -webkit-box-flex: 1;
  -webkit-flex: 1;
  flex: 1
}
.flex-item.active{
  color:#0091ff;
}
.text_box{
  margin: 0 15px;
  padding: 15px 0;
  border-bottom: 1px solid #c3c3c3;
  font-size: 13px;
}
.text_box .text_item{display:inline-block;line-height: 8px;}

</style>
