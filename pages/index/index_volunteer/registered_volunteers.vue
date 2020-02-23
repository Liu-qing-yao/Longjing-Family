<template>
	<view>
		<basics v-if="PageCur=='basics'"></basics>
		<components v-if="PageCur=='component'"></components>
		<plugin v-if="PageCur=='plugin'"></plugin>
		<view class="box top">
			<view class="cu-bar bg-white search" style="border-top: #DDDDDD 1upx solid;">
				<view class="action" @tap="goMore('/pages/index/index_volunteer/index_volunteer')">
					<image src="../../../static/input/return.png" mode="" style="width: 46rpx; height: 45rpx;"></image>
				</view>
				<view class="content text-bold text-red">
					注册志愿者
				</view>
				<view class="action" @tap="goMore('/pages/index/index_longjing/search')">
					<image src="../../../static/input/search.png" mode="" style="width: 45rpx; height: 45rpx;"></image>
				</view>
			</view>
		</view>
		<view class="bg-orange" style="height: 60upx;"></view>
		<view class="bg-orange">
			<view class="padding ">
				<view class="padding-lr bg-white" style="border: #555555 1upx solid; border-radius: 15upx;">
					<view class="vol_img">
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_1" style="width: 50upx; height: 80upx;"></image>
						<image src="../../../static/input/圆角矩形11拷贝2.png" mode="" class="img_2" style="width: 50upx; height: 80upx;"></image>
					</view>
					<view class="text-center margin-top">
						<text class="text-xl text-black ">注册</text>
					</view>
					<form  @submit="formSubmit">
						<view class="" style="margin: 10upx 60upx;">
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										用户名
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" maxlength="8"  name="user" focus />
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										密码
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" maxlength="50"  name="pass" focus password type="text"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										确认密码
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input"  maxlength="50" name="passcheck" focus password type="text" />
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										电子邮箱
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" maxlength="20" name="mail" focus/>
							</view>
							
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										真实姓名
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input"  name="nickname" focus/>
							</view>
							<view class="padding-top" >
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										证件类型
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input"  name="idtype" focus/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										证件号码
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" focus maxlength="18"  name="idnum" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										手机号码
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" focus  maxlength="11"  name="num" type="number"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										详情地址
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<input class="uni-input" focus  name="address" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										出生日期
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<picker mode="date" id="date" name="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
									<view class="uni-input align-center" style="line-height: 60upx;">{{date}}</view>
								</picker>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										国家/地区
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" >
								       <xfl-select name="country"
								           :list="list1"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										政治面貌
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="political">
								       <xfl-select 
								           :list="list2"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										民族
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="national">
								       <xfl-select 
								           :list="list3"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										籍贯
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" >
								       <xfl-select 
								           :list="list4"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							
							<view class="padding-top">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">固定号码</text>
								</view>
								<input class="uni-input" focus  name="numcar" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">邮编</text>
								</view>
								<input class="uni-input" focus  name="zip" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">QQ</text>
								</view>
								<input class="uni-input" focus  name="qq" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">微博</text>
								</view>
								<input class="uni-input" focus  name="weibo" type="idcard"/>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										居住区域
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="live">
								       <xfl-select 
								           :list="list5"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										最高学历
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="degree">
								       <xfl-select 
								           :list="list6"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										从业状况
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="practitioner">
								       <xfl-select 
								           :list="list7"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										志愿服务区域
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists" name="volunteer">
								       <xfl-select 
								           :list="list8"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										服务时间
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view class="input-lists"  name="time">
								       <xfl-select 
								           :list="list9"
								           :clearable="false"
								           :showItemNum="5" 
								           :listShow="false"
								           :isCanInput="true"  
								           :style_Container="'height: 60upx; width:500upx;'"
								           :placeholder = "'placeholder'"
								           :initValue="''"
								           :selectHideType="'hideAll'"
								       >
								       </xfl-select>
								   </view>
							</view>
							<view class="padding-top">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">服务特长</text>
								</view>
								<input class="uni-input" name="service" focus type="idcard"/>
							</view>
							
							<view class="padding-top">
								<view class="flex" style="height: 50upx;">
									<view class="text-left">
										性别
									    <text class="text-left text-red" style="font-size: 40upx;">*</text>
									</view>
								</view>
								<view>
									<view class="uni-form-item uni-column">
										<radio-group name="gender">
											<label>
												<radio value="男" style=" transform:scale(0.9)"/><text>男</text>
											</label>
											<label>
												<radio value="女" style="margin-left: 210upx;transform:scale(0.9)"/><text>女</text>
											</label>
										</radio-group>
									</view>
								</view>
							</view>
							<view class="bg-white">
								<view class="padding-top flex justify-between" @tap="showModal" data-target="Modal">
									<view class="flex" style="height: 50upx;">
										<view class="text-left">
											上传头像
										    <text class="text-left text-red" style="font-size: 40upx;">*</text>
										</view>
									</view>			
								</view>
								<view class="cu-modal" :class="modalName=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
											<!-- <view class="action">
												<text class="cuIcon-close text-red"></text>
											</view> -->
										</view>
										<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
											图像大小不得大于90kb，图像尺寸应在413*295之间，当前尺寸为××（最好为本人大头贴）
										</view>
										<view class=""  @tap="hideModal" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view>
							</view>
							<view class="cu-form-group" style="height: 200upx;">
								<view class="grid col-4 grid-square flex-sub padding-left">
									<view class="bg-img" v-for="(item,index) in imgList" :key="index" @tap="ViewImage" :data-url="imgList[index]">
									    <image :src="imgList[index]" mode="aspectFill"></image>
									    <view class="cu-tag bg-red" @tap.stop="DelImg" :data-index="index">
										     <text class='cuIcon-close'></text>
									    </view>
									</view>
									<view class="solids" @tap="ChooseImage" v-if="imgList.length<1">
										<text class='cuIcon-cameraadd'></text>
									</view>
								</view>
							</view>
							<view class="margin-bottom-sm">
								<view class="flex" style="height: 40upx;">
									<text class="text-left">验证码</text>
								</view>
								<input class="uni-input" focus type="idcard"/>
							</view>
							<view class="img-align flex justify-left">
								<image src="../../../static/input/图片验证码.png" style="width: 200upx;height: 70upx;" mode=""></image>
								<view style="color: #4284b5;margin: 15upx 0 0 5upx;">看不清？换一个</view>
							</view>
							<view class="margin-tb-sm text-bold">
								<checkbox-group class="block" name="agreement" @change="CheckboxChange">
									<view class="margin-top">
										<checkbox  :class="checkbox[0].checked?'checked':''" :checked="checkbox[0].checked?true:false" value="A" color="#FFCC33" style="transform:scale(0.7)"></checkbox>已阅读并同意协议内容
									</view>
								</checkbox-group>
							</view>
							<view class="solid" style="border-radius: 30upx;padding: 10upx; font-size: 26upx;margin-top: 15upx;">
								本网站及与本网站链接的网站，仅提供志愿、志愿服务团队...本网站概不负其他责任
							</view>
							<view class="margin-top flex justify-between">
								<view class="text-red">(加*为必填项)</view>
							</view>
							
							<view >
								<view>
									<button class="" style="margin: 30upx 0; background-color: #fe934c;color: #FFFFFF;height: 70upx; line-height: 70upx; width: 500upx;" form-type="submit">注&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;册</button>
								</view>
								<!-- <view class="cu-modal" :class="modalNameS=='Modal'?'show':''">
									<view class="cu-dialog solid">
										<view class="cu-bar bg-white justify-start">
											<view class="text-bold margin-lr" style="font-size: 34upx;">提示信息</view>
										</view>
										<view class="solid-bottom solid-top text-left" style="padding: 30upx;" >
											注册成功！
										</view>
										<view class=""  @tap="hideModalS" style="margin: 20upx 0 15upx 550upx;">
											<button style="width: 90upx;height: 50upx; line-height: 50upx; background-color: #fe9148;color: #FFFFFF;font-size: 28upx;padding: 0;">关闭</button>
										</view>
									</view>
								</view> -->
							</view>
						</view>
						
					</form>
					
					<view style="height: 40upx;"></view>
				</view>
			</view>
		</view>
		<view style="height: 100upx;"></view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="goMore('/pages/index/index')" data-cur="Home">
				<view class='cuIcon-cu-image'>
				<image :src="'../../../static/nav/Home' + [PageCur=='Home'?'_change':''] + '.png'" style="width: 42rpx; height: 41rpx;" mode="" class="img-logo"></image>
				</view>
				<view :class="PageCur=='Home'?'text-red':'text-gray'">首页</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Call_me')" data-cur="报事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/消息' + [PageCur=='报事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='报事'?'text-red':'text-gray'">报事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_people/Community_service')" data-cur="办事">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/办事' + [PageCur=='办事'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='办事'?'text-red':'text-gray'" >办事</view>
			</view>
			<view class="action" @click="goMore('/pages/index/index_play/index_play')" data-cur="发现">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/发现' + [PageCur=='发现'?'_change':''] + '.png'" style="width: 43rpx; height: 38rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='发现'?'text-red':'text-gray'">发现</view>
			</view>
			<view class="action" @click="goMore('/pages/index/Personal-center/Personal-center')" data-cur="我的">
				<view class='cuIcon-cu-image'>
					<image :src="'../../../static/nav/我的' + [PageCur=='我的'?'_change':''] + '.png'" style="width: 42rpx; height: 42rpx;" mode="" class="img-logo" ></image>
				</view>
				<view :class="PageCur=='我的'?'text-red':'text-gray'">我的</view>
			</view>
		</view>
	</view>
</template>

<script>
	import xflSelect from '../../../components/xfl-select/xfl-select.vue'
	var  graceChecker = require("../../../common/graceChecker.js");
	export default {
		data() {
			return {
				title: 'checkbox 复选框',
				PageCur: 'Home',
				CustomBar: this.CustomBar,
				modalName: null,
				modalNameS: null,
				date: getDate({
					format: true
				}),
				startDate:getDate('start'),
				endDate:getDate('end'),
				imgList: [],
				switchA: false,
				switchB: true,
				switchC: false,
				switchD: false,
				radio: 'A',
				checkbox: [{
					value: 'A',
					checked: false
				}, {
					value: 'B',
					checked: true
				}, {
					value: 'C',
					checked: false
				}],
				width:120,
				height:45,
				list1: [ //国家地区 {value: '香蕉', disabled: true},
				    '中国',
				    '中国香港',
				    '中国澳门',
				    '中国台湾',
				],
				list2: [ 
				    '中国共产党党员',
				    '中国共产党预备党员',
				    '中国共产党员（保留团籍)',
				    '中国共产主义青年团团员',
					'中国国民党革命委员会会员',
					'中国民主同盟会会员',
					'中国民主建国会会员',
					'中国民主促进会会员',
					'中国农工民主党党员',
					'中国致公党党员',
					'九三学社社员',
					'台湾民主自治同盟盟员',
					'无党派民主人士',
					'中国少年先锋队队员',
					'群众'
				],
				list3: [ //
				    '汉族',
				    '藏族',
				    '苗族',
				    '维吾尔族',
					'彝族',
					'壮族',
					'蒙古族',
					'回族',
					'土家族'
				],
				list4: [ //
				    '四川省',
				    '北京市',
				    '天津市',
				    '河北省',
					'重庆市'
				],
				list5: [
				    '自贡市','成都市', '绵阳市', '德阳市','宜宾市','资阳市',
					'泸州市','攀枝花市','广元市','遂宁市','内江市','巴中市',
					'乐山市','南充市','眉山市','广安市','达州市','雅安市','阿坝藏族羌族自治州'
				],
				list6: [ //
				    '博士研究生','硕士研究生','大学本科', 
				    '大学专科','中等专科','职业高中','技工学校',
					'高中','初中','小学','其他'
				],
				list7: [ 
				    '国家公务员','专业技术人员','职员','企业管理人员',
					'工人','农民','学生','教师',
					'现役军人','自由职业者','个体经营者','无业人员','退休（离休）人员','其他'
				],
				list8: [ 
				    '大安街道办事处',
				    '凉高山街道办事处',
				    '龙井街道办事处',
				    '马冲口街道办事处',
				],
				list9: [
				    '半小时',
				    '一小时',
				    '半天',
				    '一天',
					'两天'
				],
			}
		},
		mounted:function(){
			var _self=this;
			setTimeout(function(){
				// _self.init();
			},2000)
		},
		components: { xflSelect },  //注册为子组件
		methods: {
			goMore(url) {
				uni.navigateTo({
					url: url
				});
			},
			 PickerChange(e) {
				this.index = e.detail.value
			},
			SwitchA(e) {
				this.switchA = e.detail.value
			},
			SwitchB(e) {
				this.switchB = e.detail.value
			},
			SwitchC(e) {
				this.switchC = e.detail.value
			},
			SwitchD(e) {
				this.switchD = e.detail.value
			},
			CheckboxChange(e) {
				var items = this.checkbox,
					values = e.detail.value;
				for (var i = 0, lenI = items.length; i < lenI; ++i) {
					items[i].checked = false;
					for (var j = 0, lenJ = values.length; j < lenJ; ++j) {
						if (items[i].value == values[j]) {
							items[i].checked = true;
							break
						}
					}
				}
			},
			
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			showModalS(e) {
				this.modalNameS = e.currentTarget.dataset.target
			},
			hideModalS(e) {
				this.modalNameS = null
			},
			ChooseCheckbox(e) {
				let items = this.checkbox;
				let values = e.currentTarget.dataset.value;
				for (let i = 0, lenI = items.length; i < lenI; ++i) {
					if (items[i].value == values) {
						items[i].checked = !items[i].checked;
						break
					}
				}
			},
			RadioChange(e) {
				this.radio = e.detail.value
			},
			DateChange(e) {
				this.date = e.detail.value
			},
			bindDateChange: function(e) {
				this.date = e.target.value
			},
			onKeyInput: function(event) {
			    this.inputValue = event.target.value
			  },
			ChooseImage() {
				uni.chooseImage({
					count: 4, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: (res) => {
						if (this.imgList.length != 0) {
							this.imgList = this.imgList.concat(res.tempFilePaths)
						} else {
							this.imgList = res.tempFilePaths
						}
					}
				});
			},
			ViewImage(e) {
				uni.previewImage({
					urls: this.imgList,
					current: e.currentTarget.dataset.url
				});
			},
			DelImg(e) {
				uni.showModal({
					title: '照片',
					content: '确定要删除该照片吗？',
					cancelText: '取消',
					confirmText: '删除',
					success: res => {
						if (res.confirm) {
							this.imgList.splice(e.currentTarget.dataset.index, 1)
						}
					}
				})
			},
			checkboxChange: function (e) {
			                var items = this.items,
			                    values = e.detail.value;
			                for (var i = 0, lenI = items.length; i < lenI; ++i) {
			                    const item = items[i]
			                    if(values.includes(item.value)){
			                        this.$set(item,'checked',true)
			                    }else{
			                        this.$set(item,'checked',false)
			        }
			    }
			},
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
			    //定义表单规则
			    var rule = [
				    {name:"user", checkType : "int", checkRule:"1,8",  errorMsg:"用户名为必填项"},
					{name:"pass", checkType : "string", checkRule:"1,50",  errorMsg:"密码为必填项"},
					{name:"passcheck", checkType : "string", checkRule:"1,50",  errorMsg:"确认密码为必填项"},
					{name:"mail", checkType : "email", checkRule:"1,50",  errorMsg:"邮箱为必填项"},
					{name:"nickname", checkType : "string", checkRule:"1,4",  errorMsg:"姓名应为1-4个字符"},
					{name:"idtype", checkType : "string", checkRule:"1,50",  errorMsg:"证件类型为必填项"},
					{name:"idnum", checkType : "byid", checkRule:"1,50",  errorMsg:"证件号码为必填项"},
					{name:"num", checkType : "phoneno", checkRule:"1,50",  errorMsg:"手机号码为必填项"},
					{name:"address", checkType : "string", checkRule:"1,50",  errorMsg:"详细地址为必选项"},
					{name:"date", checkType : "dating", checkRule:"1,8",  errorMsg:"出生日期为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"country", checkType : "notnull", checkRule:"1,50",  errorMsg:"加*的下拉列表为必选项"},
					{name:"gender", checkType : "in", checkRule:"男,女",  errorMsg:"请选择性别"},
					{name:"agreement", checkType : "notnull",  checkRule:"",  errorMsg:"请同意勾选协议"},
			    ];
			    //进行表单检查
			    var formData = e.detail.value;
			    var checkRes = graceChecker.check(formData, rule);
			    if(checkRes){
			        uni.showToast({title:"验证通过!", icon:"none"});
			    }else{
			        uni.showToast({ title: graceChecker.error, icon: "none" });
			    }
			},
					
		}
	}
</script>

<style>	
.cu-form-group .title {
   		min-width: calc(4em + 15px);
   	}
.input-lists{
	background:url(../../../static/input/triangle.png) no-repeat 0 0;
	background-position: 450upx 20upx;
	line-height:20px;
	background-size:30upx 20upx;
	}
.img_1{
	position: absolute;
	left: 120upx;
	top: 170upx;
}
.img_2{
	position: absolute;
	right: 120upx;
	top: 170upx;
}
.uni-input{
	border-radius: 10upx;
	border: #b5b1b1 1upx solid;
	margin-top: 10upx;
	height: 60upx;
	width: 500upx;
	text-align: left;
	text-indent: 60upx;
	
}
.solid-bottom{
	padding: 15upx 20upx;
	margin: 0 auto;
}
.img-align *{
	display: inline-block;
	vertical-align: middle;
	font-size: 28upx;
}
</style>
