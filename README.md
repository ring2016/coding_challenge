# API Guide Line

## Introduction

The coding challenge will use log services of  Aliyun Cloud solution. The Alicloud log service provides with  API and  SDK or WebUI flavor to operate log service and analyzie logs to meet the business requirement. To  simply show the API results, we take the (Ali command line interface) to show API Results.

## Architecture

![image-20190109181352111](/Users/ring.chen/Library/Application Support/typora-user-images/image-20190109181352111.png)



### Brief

The cloud solution is deployed in shenzhen of china region , the Architecture include ECS, log Hub, Log server(Log project , log store)

* ECS: Alibaba cloud elastic cloud service that provide the cloud iaas services
* Log Hub: Alibaba cloud PaaS services.  It provide log pipeline and stream processing capability.  You can use the Alicloud agent (installed on ecs ) transfer log files to the log project  via log hub.
* Log Project:  Include the log search, analyze, count data, logShipper. We can persistent Stores log via log  store.

### Major Features

* Support almost all 50+ REST API of log service.
* Log query incomplete check and automatically query cross pagination.
* Support JMES filter to do further process on results, e.g. select specific fields from json
* Cross platforms support (Windows, Linux and Mac), Python based and friendly to Py2 and Py3 even Pypy. Support Pip installation.

## Installation

> We get the log .json via Alicloud CLI(command Line interface) , It can take the simply call the API from Aliyun. So we need to install alicloud cli  to get the log .json.

### Operation System

The CLI supports below operation system:

- Windows
- Mac
- Linux

### Supported Version

Python 2.6, 2.7, 3.3, 3.4, 3.5, 3.6, PyPy, PyPy3

### Installation Method

Run below command to install the CLI:

```python
> pip install -U aliyun-log-cli
```

**Note**

On mac it's recommended to use pip3 to install the CLI.

```python
> brew install python3
> pip3 install -U aliyun-log-cli
```

## Configure CLI

1. Input via file: You could store the content of one parameter into a file and pass it via the command line with prefix `file://`:

```shell
> aliyunlog log get_logs --request="file://./get-logs.json"
```

the content in file `get-logs.json` as below. Note: the `\` is unnecessary to escape the ".

```json
{
  "topic": "",
  "logstore": "web",
  "project": "chilingchan",
  "toTime": "2019-01-04 23:58:11",
  "offset": "0",
  "query": "*|select count(*) as count, url group by url order by count(*) desc",
  "line": "2",
  "fromTime": "2019-01-04 11:59:10",
  "reverse": "true"
}
```

According to business requirement, use log services to get the log as json format. Please refer to following.

```json
[
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "4",
    "url": "/foo/bar"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "4",
    "url": "/shop/iphone"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "3",
    "url": "/foo/bar-1"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "2",
    "url": "/shop/tv"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "/shop/pc"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "/foo/bar-2"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "null"
  }
]
```

## Test Environment 

If you need to quickly verify the environment and results,  we are ready for the environment to verify.

### ECS Infomation

```shell
Host IP: 47.107.84.200
UserNmae: root
Password: <refer to email>
```

### Command reference

Verify that get-log.json command Line

```shell
aliyunlog log get_logs --request="file://get-log.json" --format-output=json
```

It will works as following

```json
[
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "4",
    "url": "/foo/bar"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "4",
    "url": "/shop/iphone"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "3",
    "url": "/foo/bar-1"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "2",
    "url": "/shop/tv"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "/shop/pc"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "/foo/bar-2"
  },
  {
    "__source__": "",
    "__time__": "1546603150",
    "count": "1",
    "url": "null"
  }
]
```





















































