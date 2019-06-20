# financial
金融理财系统  
项目利用gradle 分模块进行构建

## 项目知识点
![思维导图](https://github.com/o0Y0o/financial/blob/master/manager/src/main/resources/static/pic/01.png)  

## 数据库表
```
CREATE TABLE `order_t` (
  `order_id` varchar(64) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_520_ci NOT NULL COMMENT '订单编号',
  `chan_id` varchar(64) NOT NULL COMMENT '渠道编号',
  `product_id` varchar(64) NOT NULL COMMENT '产品编号',
  `chan_user_id` varchar(64) NOT NULL COMMENT '渠道用户编号',
  `order_type` varchar(64) NOT NULL COMMENT '类型，APPLY:申购,REDEEM:赎回',
  `order_status` varchar(64) NOT NULL COMMENT '状态,INIT：初始化,PROCESS：处理中,SUCCESS:成功,FAIL:失败',
  `outer_order_id` varchar(64) NOT NULL COMMENT '外部订单编号',
  `amount` decimal(15,3) NOT NULL COMMENT '金额',
  `remark` varchar(255) DEFAULT NULL COMMENT '备注',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`order_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC;

-- ----------------------------
-- Records of order_t
-- ----------------------------

-- ----------------------------
-- Table structure for product
-- ----------------------------
DROP TABLE IF EXISTS `product`;
CREATE TABLE `product` (
  `id` varchar(64) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_520_ci NOT NULL COMMENT '产品编号',
  `name` varchar(64) NOT NULL COMMENT '产品名称',
  `threshold_amount` decimal(15,3) NOT NULL COMMENT '起投资金',
  `step_amount` decimal(15,3) NOT NULL COMMENT '投资步长',
  `lock_term` smallint(6) NOT NULL COMMENT '锁定期',
  `reward_rate` decimal(5,3) NOT NULL COMMENT '收益率',
  `status` varchar(32) NOT NULL COMMENT '状态,audinting:审核中,in_sell:销售中,locked:暂停销售,finished:已结束',
  `remark` varchar(255) DEFAULT NULL COMMENT '备注',
  `create_user` varchar(32) DEFAULT NULL COMMENT '创建者',
  `update_user` varchar(32) DEFAULT NULL COMMENT '更新者',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC COMMENT='产品表';

-- ----------------------------
-- Records of product
-- ----------------------------
INSERT INTO `product` VALUES ('aaa', 'user', '12.000', '0.000', '0', '20.000', '0', '是是是', 'user', 'user', '2019-06-19 10:01:11', '2019-06-19 10:01:11');

```