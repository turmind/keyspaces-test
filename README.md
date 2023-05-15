# Keyspaces-test

## 测试观察的情况

- 与keyspaces的链接在大约12900秒后断开链接，大概为35.84小时左右
- keyspaces在断开后即刻重连，不影响业务运行

## 测试准备

- cpp-diver tag v2.16.0 编译并安装 https://github.com/datastax/cpp-driver/tree/2.16.0
- simple中编译可执行文件

## 测试案例分别为以下

- key-active-break 有效凭证不运行select
- key-active-normal 有效凭证每30秒运行一次select
- key-inactive-break 无效凭证不运行select
- key-inactive-normal 无效凭证每30秒运行一次select

## 相关测试文件

- netstat.txt 为观察到的与keyspaces的socket对的情况
- nohup.out为运行日志，重点查看内容：
  - key-active-break 4302行
  - key-active-normal 8602行
  - key-inactive-break 4302行
  - key-inactive-normal 8602行
