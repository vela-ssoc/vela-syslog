# syslog
> 创建一个syslog日志服务器

## 内置方法
- [vela.syslog{}](#创建服务) &创建syslog服务器

## 创建服务
> syslog = vela.syslog{cfg} <br />

- name
- protocol &emsp;监听协议
- listen
- format &emsp;[日志格式](#日志格式)
- encode
- output

```lua
    local kafka = kafka.producer{}
    local file = rock.file{}
    local syslog = syslog.server{
        protocol  = "udp", -- udp , tcp , udp/tcp
        listen    = "0.0.0.0:514",
        
        -- RFC3178,RFC5424,RFC6587,Auto
        format    = syslog.Auto ,
        
        -- json , raw  数据保存格式
        encode    = "raw", 
        
        output = {kafka , file } -- lua.Writer 接口的方法 
    }

    start(kafka , file , syslog)-- 启动
```

## 日志格式


- vela.syslog.RFC3164
- vela.syslog.RFC5424
- vela.syslog.RFC6587
- vela.syslog.AUTO
