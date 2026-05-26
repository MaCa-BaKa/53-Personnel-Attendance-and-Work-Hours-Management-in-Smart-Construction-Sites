# 53-智慧工地人员考勤与工时管理系统

[文档地址](http://wechat.zjrcsy.cn/)

**技术栈：** Spring Boot + Vue 3

**访问说明：** 本项目采用前后端分离部署。后端服务默认运行在 `http://localhost:8088/api`，管理端默认运行在 `http://localhost:3000`，员工端默认运行在 `http://localhost:3001`。接口文档可通过 `http://localhost:8088/api/doc.html` 访问。

**演示账号：** 管理员账号 `admin / 123456`；员工账号 `user01 / 123456`。


## 补充说明

- 后端技术要点：Spring Boot、Spring Security + JWT、MyBatis-Plus、MySQL、Redis 配置、本地文件上传、Knife4j 接口文档、统一返回结果、全局异常处理、操作日志记录等。
- 前端技术要点：Vue 3、Vite、Element Plus、Pinia、Vue Router、Axios、ECharts、高德地图定位与围栏展示等。
- 项目代码目录：`site-backend/` 为后端服务，`site-admin/` 为管理后台，`site-web/` 为员工端，数据库初始化脚本位于 `site-backend/src/main/resources/db/`。
- 系统围绕工地人员考勤、定位打卡、班组管理、请假加班申诉、工时工资核算与公告消息等业务场景设计，适合工地现场人员日常考勤和后台综合管理。


## 员工端

1. **首页：** 展示个人问候、本月出勤、本月工时、加班时长、异常考勤、快捷功能入口和最新公告。
2. **账户登录与注册：** 支持员工账号登录、注册与 JWT 鉴权，登录后进入个人工作台。
3. **定位打卡：** 员工可进行上班、下班打卡；系统展示当前时间、打卡范围、工地围栏地图，并记录 GPS 定位信息。
4. **打卡记录：** 支持按日期查询个人考勤记录，展示上班打卡、下班打卡、状态、工时、加班时长和打卡位置。
5. **考勤日历：** 以日历形式查看个人月度考勤状态，便于快速识别正常、迟到、旷工等情况。
6. **我的排班：** 查看个人班次安排、排班日期、计划时间和排班类型。
7. **请假申请：** 在线提交请假类型、起止时间、请假原因和证明材料，提交后进入后台审核流程。
8. **加班申请：** 支持填写加班日期、加班时间、加班类型和加班原因，便于后续工时工资核算。
9. **考勤申诉：** 对异常打卡、漏打卡等情况提交申诉，上传证明并等待管理员审核。
10. **申请记录：** 汇总查看请假、加班、申诉等申请的提交时间、审核状态和处理结果。
11. **工时工资：** 查看个人工时统计、工资条和相关核算信息。
12. **公告消息：** 查看全工地公告、班组公告和个人消息提醒。
13. **个人中心：** 维护个人资料、联系方式、紧急联系人、银行卡等基础信息。


## 管理员端

1. **数据看板：** 汇总在职人数、今日出勤、出勤率、异常考勤、待审核数量、班组数、近 7 天出勤趋势和班组考勤统计。
2. **用户管理：** 管理工地人员账号、真实姓名、手机号、所属班组、岗位、角色和启用状态。
3. **角色与权限：** 维护系统角色、权限菜单和访问控制关系，支撑管理员、班组长、普通员工等权限划分。
4. **系统日志：** 查看登录、新增、审核、工资生成等关键操作日志，便于追踪后台操作。
5. **工地打卡范围：** 配置工地名称、中心经纬度、半径范围，并通过地图展示定位围栏。
6. **班组管理：** 维护钢筋、木工、混凝土等班组信息，关联班组长和成员数量。
7. **考勤记录：** 查询员工每日打卡时间、打卡地点、考勤状态、工时和加班时长。
8. **考勤规则：** 配置上班时间、下班时间、迟到阈值、早退阈值、旷工阈值和加班最小时长。
9. **异常考勤：** 汇总迟到、早退、旷工、缺卡等异常记录，辅助管理员快速处理。
10. **排班管理：** 新增个人排班和班组批量排班，管理班次日期、计划时间和排班类型。
11. **申请审核：** 统一审核请假申请、加班申请和考勤申诉，支持查看原因、证明材料和审核意见。
12. **工时工资：** 统计班组与个人工时，生成工资记录，配置计薪标准、加班倍率、补贴和扣款规则。
13. **公告消息：** 发布全工地公告或班组公告，管理消息通知和阅读状态。
14. **个人账号：** 管理员可查看个人资料、编辑基础信息并修改登录密码。


## 员工端界面示意

![员工端登录](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-login.png)

![员工端首页](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-home.png)

![定位打卡](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-clock-in.png)

![打卡记录](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-attendance-record.png)

![考勤日历](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-calendar.png)

![请假申请](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-leave-apply.png)

![工时统计](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-worktime.png)

![个人中心](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/web-profile.png)


## 管理员端界面示意

![用户管理](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-users.png)

![工地打卡范围](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-site-fence.png)

![考勤记录管理](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-attendance-records.png)

![排班管理](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-shift-schedule.png)

![请假审核](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-leave-review.png)

![工资管理](https://yunzhuceshi.oss-cn-beijing.aliyuncs.com/typoraImg/admin-salary.png)

