<template>
	<div>
		<div class="container" :style='{"minHeight":"100vh","padding":"20px","alignItems":"center","background":"url(http://codegen.caihongy.cn/20240330/83e54fd0c14b48a6a366638d7e19a66d.jpg)","display":"flex","width":"auto","backgroundSize":"100% 100%","backgroundPosition":"center top","backgroundRepeat":"no-repeat","justifyContent":"flex-end"}'>
			<el-form v-if="pageFlag=='register'" :style='{"boxShadow":"0 1px 20px rgba( 255,  255, 255, .8)","padding":"20px 0","margin":"0px 90px 0px 0px","borderRadius":"4px","background":"#fff","width":"500px","height":"auto"}' ref="rgsForm" class="rgs-form" :model="rgsForm" :rules="rules">
				<div v-if="true" :style='{"width":"100%","margin":"0 0 10px 0","lineHeight":"44px","fontSize":"20px","color":"#374254","textAlign":"center"}' class="title">团队协作系统注册</div>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('tuanduimingcheng')?'required':''">团队名称：</div>
					<el-input  v-model="ruleForm.tuanduimingcheng"  autocomplete="off" placeholder="团队名称"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('tuanzhangxingming')?'required':''">团长姓名：</div>
					<el-input  v-model="ruleForm.tuanzhangxingming"  autocomplete="off" placeholder="团长姓名"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('mima')?'required':''">密码：</div>
					<el-input  v-model="ruleForm.mima"  autocomplete="off" placeholder="密码"  type="password"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('mima')?'required':''">确认密码：</div>
					<el-input  v-model="ruleForm.mima2" autocomplete="off" placeholder="确认密码" type="password" />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('xingbie')?'required':''">性别：</div>
                    <el-select v-model="ruleForm.xingbie" placeholder="请选择性别" >
                        <el-option
                            v-for="(item,index) in fuzerenxingbieOptions"
                            v-bind:key="index"
                            :label="item"
                            :value="item">
                        </el-option>
                    </el-select>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('nianling')?'required':''">年龄：</div>
					<el-input  v-model.number="ruleForm.nianling"  autocomplete="off" placeholder="年龄"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('touxiang')?'required':''">头像：</div>
                    <file-upload
                        tip="点击上传头像"
                        action="file/upload"
                        :limit="3"
                        :multiple="true"
                        :fileUrls="ruleForm.touxiang?ruleForm.touxiang:''"
                        @change="fuzerentouxiangUploadChange"
                    ></file-upload>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('shenfenzheng')?'required':''">身份证：</div>
					<el-input  v-model="ruleForm.shenfenzheng"  autocomplete="off" placeholder="身份证"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='fuzeren'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('lianxidianhua')?'required':''">联系电话：</div>
					<el-input  v-model="ruleForm.lianxidianhua"  autocomplete="off" placeholder="联系电话"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('yonghuming')?'required':''">用户名：</div>
					<el-input  v-model="ruleForm.yonghuming"  autocomplete="off" placeholder="用户名"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('xingming')?'required':''">姓名：</div>
					<el-input  v-model="ruleForm.xingming"  autocomplete="off" placeholder="姓名"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('mima')?'required':''">密码：</div>
					<el-input  v-model="ruleForm.mima"  autocomplete="off" placeholder="密码"  type="password"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('mima')?'required':''">确认密码：</div>
					<el-input  v-model="ruleForm.mima2" autocomplete="off" placeholder="确认密码" type="password" />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('xingbie')?'required':''">性别：</div>
                    <el-select v-model="ruleForm.xingbie" placeholder="请选择性别" >
                        <el-option
                            v-for="(item,index) in chengyuanxingbieOptions"
                            v-bind:key="index"
                            :label="item"
                            :value="item">
                        </el-option>
                    </el-select>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('nianling')?'required':''">年龄：</div>
					<el-input  v-model.number="ruleForm.nianling"  autocomplete="off" placeholder="年龄"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('shoujihao')?'required':''">手机号：</div>
					<el-input  v-model="ruleForm.shoujihao"  autocomplete="off" placeholder="手机号"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('touxiang')?'required':''">头像：</div>
                    <file-upload
                        tip="点击上传头像"
                        action="file/upload"
                        :limit="3"
                        :multiple="true"
                        :fileUrls="ruleForm.touxiang?ruleForm.touxiang:''"
                        @change="chengyuantouxiangUploadChange"
                    ></file-upload>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('shenfenzheng')?'required':''">身份证：</div>
					<el-input  v-model="ruleForm.shenfenzheng"  autocomplete="off" placeholder="身份证"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('tuanduimingcheng')?'required':''">团队名称：</div>
					<el-input  v-model="ruleForm.tuanduimingcheng"  autocomplete="off" placeholder="团队名称"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 0","height":"auto"}' class="list-item" v-if="tableName=='chengyuan'">
					<div v-if="true" :style='{"width":"100%","lineHeight":"44px","fontSize":"14px","position":"relative","color":" #374254"}' class="lable" :class="changeRules('tuanzhangxingming')?'required':''">团长姓名：</div>
					<el-input  v-model="ruleForm.tuanzhangxingming"  autocomplete="off" placeholder="团长姓名"  type="text"  />
				</el-form-item>
				<button :style='{"border":"0","cursor":"pointer","padding":"0 10px","margin":"20px auto 5px","outline":"none","color":"#fff","borderRadius":"4px","background":"#dc4e41","display":"block","width":"80%","fontSize":"16px","height":"44px"}' type="button" class="r-btn" @click="login()">注册</button>
				<div :style='{"cursor":"pointer","padding":"0 10%","color":"rgba(159, 159, 159, 1)","display":"inline-block","lineHeight":"1","fontSize":"12px","textDecoration":"underline"}' class="r-login" @click="close()">已有账号，直接登录</div>
			</el-form>
			
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			ruleForm: {
			},
			forgetForm: {},
            pageFlag : '',
			tableName:"",
			rules: {},
            fuzerenxingbieOptions: [],
            chengyuanxingbieOptions: [],
		};
	},
	mounted(){
		this.pageFlag = this.$route.query.pageFlag
		if(this.$route.query.pageFlag=='register'){
			
			let table = this.$storage.get("loginTable");
			this.tableName = table;
			if(this.tableName=='fuzeren'){
				this.ruleForm = {
					tuanduimingcheng: '',
					tuanzhangxingming: '',
					mima: '',
					xingbie: '',
					nianling: '',
					touxiang: '',
					shenfenzheng: '',
					lianxidianhua: '',
				}
			}
			if(this.tableName=='chengyuan'){
				this.ruleForm = {
					yonghuming: '',
					xingming: '',
					mima: '',
					xingbie: '',
					nianling: '',
					shoujihao: '',
					touxiang: '',
					shenfenzheng: '',
					tuanduimingcheng: '',
					tuanzhangxingming: '',
				}
			}
			if ('fuzeren' == this.tableName) {
				this.rules.tuanduimingcheng = [{ required: true, message: '请输入团队名称', trigger: 'blur' }]
			}
			if ('fuzeren' == this.tableName) {
				this.rules.tuanzhangxingming = [{ required: true, message: '请输入团长姓名', trigger: 'blur' }]
			}
			if ('fuzeren' == this.tableName) {
				this.rules.mima = [{ required: true, message: '请输入密码', trigger: 'blur' }]
			}
			if ('chengyuan' == this.tableName) {
				this.rules.yonghuming = [{ required: true, message: '请输入用户名', trigger: 'blur' }]
			}
			if ('chengyuan' == this.tableName) {
				this.rules.xingming = [{ required: true, message: '请输入姓名', trigger: 'blur' }]
			}
			if ('chengyuan' == this.tableName) {
				this.rules.mima = [{ required: true, message: '请输入密码', trigger: 'blur' }]
			}
			this.fuzerenxingbieOptions = "男,女".split(',')
			this.chengyuanxingbieOptions = "男,女".split(',')
		}
	},
	created() {
	},
	destroyed() {
		  	},
	methods: {
		changeRules(name){
			if(this.rules[name]){
				return true
			}
			return false
		},
		// 获取uuid
		getUUID () {
			return new Date().getTime();
		},
		close(){
			this.$router.push({ path: "/login" });
		},
        fuzerentouxiangUploadChange(fileUrls) {
            this.ruleForm.touxiang = fileUrls;
        },
        chengyuantouxiangUploadChange(fileUrls) {
            this.ruleForm.touxiang = fileUrls;
        },

        // 多级联动参数


		// 注册
		login() {
			var url=this.tableName+"/register";
					if((!this.ruleForm.tuanduimingcheng) && `fuzeren` == this.tableName){
						this.$message.error(`团队名称不能为空`);
						return
					}
					if((!this.ruleForm.tuanzhangxingming) && `fuzeren` == this.tableName){
						this.$message.error(`团长姓名不能为空`);
						return
					}
					if((!this.ruleForm.mima) && `fuzeren` == this.tableName){
						this.$message.error(`密码不能为空`);
						return
					}
					if((this.ruleForm.mima!=this.ruleForm.mima2) && `fuzeren` == this.tableName){
						this.$message.error(`两次密码输入不一致`);
						return
					}
					if(`fuzeren` == this.tableName && this.ruleForm.nianling &&(!this.$validate.isIntNumer(this.ruleForm.nianling))){
						this.$message.error(`年龄应输入整数`);
						return
					}
            if(this.ruleForm.touxiang!=null) {
                this.ruleForm.touxiang = this.ruleForm.touxiang.replace(new RegExp(this.$base.url,"g"),"");
            }
					if(`fuzeren` == this.tableName && this.ruleForm.shenfenzheng &&(!this.$validate.checkIdCard(this.ruleForm.shenfenzheng))){
						this.$message.error(`身份证应输入身份证格式`);
						return
					}
					if(`fuzeren` == this.tableName && this.ruleForm.lianxidianhua &&(!this.$validate.isMobile(this.ruleForm.lianxidianhua))){
						this.$message.error(`联系电话应输入手机格式`);
						return
					}
					if((!this.ruleForm.yonghuming) && `chengyuan` == this.tableName){
						this.$message.error(`用户名不能为空`);
						return
					}
					if((!this.ruleForm.xingming) && `chengyuan` == this.tableName){
						this.$message.error(`姓名不能为空`);
						return
					}
					if((!this.ruleForm.mima) && `chengyuan` == this.tableName){
						this.$message.error(`密码不能为空`);
						return
					}
					if((this.ruleForm.mima!=this.ruleForm.mima2) && `chengyuan` == this.tableName){
						this.$message.error(`两次密码输入不一致`);
						return
					}
					if(`chengyuan` == this.tableName && this.ruleForm.nianling &&(!this.$validate.isIntNumer(this.ruleForm.nianling))){
						this.$message.error(`年龄应输入整数`);
						return
					}
					if(`chengyuan` == this.tableName && this.ruleForm.shoujihao &&(!this.$validate.isMobile(this.ruleForm.shoujihao))){
						this.$message.error(`手机号应输入手机格式`);
						return
					}
            if(this.ruleForm.touxiang!=null) {
                this.ruleForm.touxiang = this.ruleForm.touxiang.replace(new RegExp(this.$base.url,"g"),"");
            }
					if(`chengyuan` == this.tableName && this.ruleForm.shenfenzheng &&(!this.$validate.checkIdCard(this.ruleForm.shenfenzheng))){
						this.$message.error(`身份证应输入身份证格式`);
						return
					}
			this.$http({
				url: url,
				method: "post",
				data:this.ruleForm
			}).then(({ data }) => {
				if (data && data.code === 0) {
					this.$message({
						message: "注册成功",
						type: "success",
						duration: 1500,
						onClose: () => {
							this.$router.replace({ path: "/login" });
						}
					});
				} else {
					this.$message.error(data.msg);
				}
			});
		}
	}
};
</script>

<style lang="scss" scoped>
	.container {
	  position: relative;
	  background: url(http://codegen.caihongy.cn/20240330/83e54fd0c14b48a6a366638d7e19a66d.jpg);

		.el-date-editor.el-input {
		  width: 100%;
		}
		
		.rgs-form .el-input /deep/ .el-input__inner {
						border: 1px solid rgba(167, 180, 201,.3)    ;
						border-radius: 0;
						padding: 0 10px;
						outline: none;
						color: #a7b4c9 ;
						width: 100%;
						font-size: 14px;
						height: 40px;
					}
		
		.rgs-form .el-select /deep/ .el-input__inner {
						border: 1px solid rgba(167, 180, 201,.3)    ;
						border-radius: 0;
						padding: 0 10px;
						outline: none;
						color: #a7b4c9 ;
						width: 288px;
						font-size: 14px;
						height: 40px;
					}
		
		.rgs-form .el-date-editor /deep/ .el-input__inner {
						border: 1px solid rgba(167, 180, 201,.3)    ;
						border-radius: 0;
						padding: 0 10px 0 30px;
						outline: none;
						color: #a7b4c9 ;
						width: 288px;
						font-size: 14px;
						height: 40px;
					}
		
		.rgs-form .el-date-editor /deep/ .el-input__inner {
						border: 1px solid rgba(167, 180, 201,.3)    ;
						border-radius: 0;
						padding: 0 10px 0 30px;
						outline: none;
						color: #a7b4c9 ;
						width: 288px;
						font-size: 14px;
						height: 40px;
					}
		
		.rgs-form /deep/ .el-upload--picture-card {
			background: transparent;
			border: 0;
			border-radius: 0;
			width: auto;
			height: auto;
			line-height: initial;
			vertical-align: middle;
		}
		
		.rgs-form /deep/ .upload .upload-img {
		  		  border: 1px dashed  rgba(167, 180, 201,.3)    ;
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: rgba(167, 180, 201,.3);
		  		  width: 90px;
		  		  font-size: 32px;
		  		  line-height: 60px;
		  		  text-align: center;
		  		  height: 60px;
		  		}
		
		.rgs-form /deep/ .el-upload-list .el-upload-list__item {
		  		  border: 1px dashed  rgba(167, 180, 201,.3)    ;
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: rgba(167, 180, 201,.3);
		  		  width: 90px;
		  		  font-size: 32px;
		  		  line-height: 60px;
		  		  text-align: center;
		  		  height: 60px;
		  		}
		
		.rgs-form /deep/ .el-upload .el-icon-plus {
		  		  border: 1px dashed  rgba(167, 180, 201,.3)    ;
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: rgba(167, 180, 201,.3);
		  		  width: 90px;
		  		  font-size: 32px;
		  		  line-height: 60px;
		  		  text-align: center;
		  		  height: 60px;
		  		}
	}
	.required {
		position: relative;
	}
	.required::after{
				color: red;
				left: -10px;
				position: absolute;
				content: "*";
			}
	.editor>.avatar-uploader {
		line-height: 0;
		height: 0;
	}
</style>
