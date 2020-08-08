# 通知事件

## 群文件上传

**注意：仅群文件上传表现为事件，好友发送文件在 酷Q 中没有独立的事件，而是直接表现为好友消息，请注意在编写业务逻辑时进行判断。**

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | ------- | ---- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `group_upload` | 通知类型 |
| `group_id` | number (int64) | - | 群号 |
| `user_id` | number (int64) | - | 发送者 QQ 号 |
| `file` | object | - | 文件信息 |

其中 `file` 字段的内容如下：

| 字段名 | 数据类型 | 说明 |
| ----- | ------ | ---- |
| `id` | string | 文件 ID |
| `name` | string | 文件名 |
| `size` | number (int64) | 文件大小（字节数） |
| `busid` | number (int64) | busid（目前不清楚有什么作用） |

## 群管理员变动

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | -------- | --- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `group_admin` | 通知类型 |
| `sub_type` | string | `set`、`unset` | 事件子类型，分别表示设置和取消管理员 |
| `group_id` | number (int64) | - | 群号 |
| `user_id` | number (int64) | - | 管理员 QQ 号 |

## 群成员减少

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | -------- | --- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `group_decrease` | 通知类型 |
| `sub_type` | string | `leave`、`kick`、`kick_me` | 事件子类型，分别表示主动退群、成员被踢、登录号被踢 |
| `group_id` | number (int64) | - | 群号 |
| `operator_id` | number (int64) | - | 操作者 QQ 号（如果是主动退群，则和 `user_id` 相同） |
| `user_id` | number (int64) | - | 离开者 QQ 号 |

## 群成员增加

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | -------- | --- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `group_increase` | 通知类型 |
| `sub_type` | string | `approve`、`invite` | 事件子类型，分别表示管理员已同意入群、管理员邀请入群 |
| `group_id` | number (int64) | - | 群号 |
| `operator_id` | number (int64) | - | 操作者 QQ 号 |
| `user_id` | number (int64) | - | 加入者 QQ 号 |

## 群禁言

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | -------- | --- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `group_ban` | 通知类型 |
| `sub_type` | string | `ban`、`lift_ban` | 事件子类型，分别表示禁言、解除禁言 |
| `group_id` | number (int64) | - | 群号 |
| `operator_id` | number (int64) | - | 操作者 QQ 号 |
| `user_id` | number (int64) | - | 被禁言 QQ 号 |
| `duration` | number (int64) | - | 禁言时长，单位秒 |

## 好友添加

### 上报数据

| 字段名 | 数据类型 | 可能的值 | 说明 |
| ----- | ------ | -------- | --- |
| `post_type` | string | `notice` | 上报类型 |
| `notice_type` | string | `friend_add` | 通知类型 |
| `user_id` | number (int64) | - | 新添加好友 QQ 号 |