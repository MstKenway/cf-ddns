# cf-ddns
A shell script for cloudflare ddns


代码修改自[出处](https://gist.githubusercontent.com/benkulbertis/fff10759c2391b6618dd/raw )


使用方法：

1.先下载
```
mkdir /etc/cf-ddns
wget https://github.com/MstKenway/cf-ddns/raw/master/cf-ddns.sh -O /etc/cf-ddns/cf-ddns.sh && chmod +x /etc/cf-ddns/cf-ddns.sh
```

2.修改参数，包括cf的账号、api令牌、域名和CNAME。如下：

```
auth_email="user@example.com"
auth_key="c2547eb745079dac9320b638f5e225cf483cc5cfdda41" # found in cloudflare account settings
zone_name="example.com"
record_name="www.example.com"
```

可使用vi或者nano编辑
```
vi /etc/cf-ddns/cf-ddns.sh
```

或

```
nano /etc/cf-ddns/cf-ddns.sh
```

3.运行
```
bash /etc/cf-ddns/cf-ddns.sh
```

4.编辑定时任务crontab，这里设定每2分钟检查一次ip变化，可根据实际需求改变频率，最小单位是1分钟。具体查看crontab使用方法。
```
crontab -e

*/2 * * * * bash /etc/cf-ddns/cf-ddns.sh > /dev/null 2>&1
```
