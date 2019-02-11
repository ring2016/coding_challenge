```shell
# 打印URL，并计算出现次数，按降序排列
*|select count(*) as count, url group by url order by count(*) desc

```

