# easytestapi - 文档即测试 

## 介绍
一个高度接口自动化测试工具，虽然目前还不完善，但是想法值得分享。
更多介绍请访问链接：
https://easytestapi.notion.site/easytestapi-fa8fafba18c849d2bdb3eaeafb2f6020

## 简单体验
```shell
python ./bin/easytestapi.py -d ./tests/apis/test_create_tester_api.json
```
```shell
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_随机正向值测试用例.json》已生成至本地路径: 创建tester接口\创建tester接口_随机正向值测试用例.json
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_test_str_字段不填.json》已生成至本地路径: 创建tester接口\创建tester接口_test_str_字段不填.json
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_test_str_字段填null.json》已生成至本地路径: 创建tester接口\创建tester接口_test_str_字段填null.json
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_test_phone_验证错误手机号.json》已生成至本地路径: 创建tester接口\创建tester接口_test_phone_验证错误手机号.json
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_test_dt_验证错误日期格式.json》已生成至本地路径: 创建tester接口\创建tester接口_test_dt_验证错误日期格式.json
2022-08-09 19:00:40 models.py [line:615] INFO 用例《创建tester接口_test_enum_验证不存在的枚举值.json》已生成至本地路径: 创建tester接口\创建tester接口_test_enum_验证不存在的枚举值.json
```

## 接口JSON
[test_create_tester_api.json](https://github.com/nigelaji/easytestapi/blob/main/tests/apis/test_create_tester_api.json)
```JSON
{
    "name": "创建tester接口",
    "code": "test_create_tester",
    "versions": ["v1.0"],
    "route": "/tp/testers",
    "method": "POST",
    "setup": [

    ],
    "headers": {
        "Content-Type": "application/json"
    },
    "fields": [
      // 内容比较长，查看tests/apis/test_create_tester_api.json
    ],
    "teardown": [],
    "additional": [],
    "response": {
        "code": 200,
        "data": {
            "id": 1
        },
        "msg": "ok"
    },
    "response_assert": {
        "$.code": "200",
        "$.data.id": "\\d+"
    }
}
```

## 用例JSON
用例生成之后，会创建一个文件夹。里面存放着用例的json
```JSON
{
    "flag": true,
    "name": "创建tester接口_随机正向值测试用例",
    "versions": [
        "v1.0"
    ],
    "route": "/tp/testers",
    "route_params": {},
    "params": {},
    "method": "POST",
    "setup": [],
    "headers": {
        "Content-Type": "application/json"
    },
    "body": {
        "test_str": "AWmbuGKzhOSsMbjlKePdiAilBJVtzQ",
        "test_int": 9612115852,
        "test_float": 3083983981.08,
        "test_phone": "18924681674",
        "test_dt": "2022-08-09 19:00:40",
        "test_enum": "B"
    },
    "teardown": [],
    "response_assert": {
        "$.code": "200",
        "$.data.id": "\\d+"
    }
}
```

## 直接执行用例
可以使用`-r`参数直接执行用例，须web服务 https://github.com/nigelaji/easytestapi-flask 配合使用。
启动`easytestapi-flask`项目后，执行下面命令行。
```shell
python ./bin/easytestapi.py -r ./tests/apis/test_create_tester_api.json
```
