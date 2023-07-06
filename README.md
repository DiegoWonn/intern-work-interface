# 实习期间做的已上线的一些简单接口：

## 批量给产品pd授权aplus权限（vipernew)

### 背景

- Aplus是一款数据产品：数据埋点，检测。a+ SDK为阿里云提供流量&性能数据采集方案。Aplus为接入项目实现流量数据埋点等功能。

- viper控制台(WIND是前端解决方案，OneConsole是后端解决方案)是阿里云产品管理平台。云产品通过接入viper可以配置（负责人、信息、渠道、业务人员、openAPI等的管理）等信息，开发人员也可以过viper平台管控各产品的数据源接入、审批、open api管理、审批等。

### 需求

批量给产品pd授权aplus权限：一般，产品的spmb都是批量自动生成的，但是可能出现异常，或者由于是新产品，导致其没有spmb。在viper项目代码里，提供接口，通过viper的产品管理接口给产品相关管理员授予Aplus项目权限。ConsoleProductServiceImp：通过aplusSdkService提供的updateAplusSdkProjectMembers接口实现，这个接口需要提供待授权人和授权项目，待授权人通过viper的productModel获取，授权项目则通过设置pid、token等实现。

### 验证

- aplus提供的读取已授权名单的接口，打印的授权名单信息，看是否授权成功
- 授权给自己，再自己访问aplus，确实是有权限的（授权成功）。在viper平台输入产品ID，可以找到产品关联的应用，打开应用三方脚本，可以看到关联的aplus项目，如果点开有项目的流量数据之类的，说明“我”的权限已经加进去了（无权限则什么都看不到，把自己加入权限）
- 抽几个产品pd询问是否已被授权



## 添加手动添加Spmb的接口(viper new)

### 背景

Spmb:spm是一种用来跟踪页面模块位置的编码，b位是spm的组成部分。

<img width="1141" alt="image" src="https://github.com/DiegoWonn/intern-work-interface/assets/135291488/9dcfdfcd-b920-4e6c-8463-2f4549a070f5">


### 需求

手动生成spmb:一般，产品的spmb都是批量自动生成的（viper中存在给产品批量生成spmb的接口），但是可能出现异常，或者是新产品，导致有的产品没有spmb。需求是提供一个接口，可以手动的为没有spmb的产品生成spmb.

<img width="1049" alt="image" src="https://github.com/DiegoWonn/intern-work-interface/assets/135291488/0d4fb30a-9e82-4c83-a33c-a06084d8eeb1">


### 验证

- 能返回正确格式的Spmb
- 前端完成工作后，能在页面显示正确的生成Spmb入口，刷新页面能持久化保存生成的Spmb



## 根据产品ID精确查询产品详情(vco-console)

### 需求

根据输入的产品ID能精确查询产品详情（非模糊查询），比较简单，不过多赘述。

### 验证

- 查询功结果正确



## 封装工号和花名（vipernew)

## 需求

之前在数据资源检索页只会显示负责人的工号，希望改成一个返回给前端同学一个封装有工号和花名的object（应该调取已有的hsf服务根据工号查花名再封装在一起就行）的接口。

### 验证

- 返回结果封装有花名，且花名与工号是同一人的

### 注意

这个接口需要根据工号查找花名，vipernew项目本身是没有相关方法和服务的，需要消费外界提供的hsf服务。涉及到的技术就是hsf依赖的引入，hsf消费端对于hsfBean的引入(pom方式、HSFConfig方式)、消费。



## 数据源接入详情页的显示(vipernew)

## 需求

<img width="1092" alt="image" src="https://github.com/DiegoWonn/intern-work-interface/assets/135291488/c9236587-6dc7-48c8-9ab0-7b7eac84c7bd">


显示类似如图所示的数据源详情

<img width="916" alt="image" src="https://github.com/DiegoWonn/intern-work-interface/assets/135291488/eb9debe1-c57f-4a30-ace3-f9873d8501f2">


### 验证

- 返回正确，一个封装了数据源详情页的list

