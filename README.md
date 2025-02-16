# SearchDataTransporter
一个中间层服务,主要为了支持让本地部署的Ollama框架中运行的大模型实现联网搜索能力

## 使用说明 
运行主文件，将搜索到的数据导入kafka，用于让Ollama的订阅者进行订阅

## 业务原理
Ollama增加SearchData订阅者插件，打开联网功能的情况下，用户询问的内容，首先先由SearchData订阅者向  SearchDataTransporter中间服务 发出咨询；SearchDataTransporter返回的数据进入kafka中后，再有SearchData的消息订阅器消费推送给大模型进行统一处理，最后整合以后返回给用户
