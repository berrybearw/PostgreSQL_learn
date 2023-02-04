連線

https://www.cisco.com/c/zh_tw/support/docs/cloud-systems-management/cloudcenter/212585-resolve-fatal-no-pg-hba-conf-entry-for.pdf

![image](https://user-images.githubusercontent.com/96226780/216754067-6543a348-8b56-4ac9-a751-2ed0f1f43696.png)

確認 pg_hba.conf 有設定 ip 可認證

https://www.modb.pro/db/569507

FATAL: Forbid remote connection with trust method

檢查 pg_hba.conf 認證方式 ( 密碼加密方式 trust , sha256 )

http://www.knockatdatabase.com/2021/06/04/how-to-install-config-opengauss-on-centos7/

##### Invalid or unsupported by client SCRAM mechanisms

查看密碼認證方式 ( 預設 sha256 )

可改用 md5 , 1. 調整認證方式 2. 重新設定用戶密碼

範例 MD5

![image](https://user-images.githubusercontent.com/96226780/216754081-787244b1-5b49-4fa4-9bcd-f364688f9780.png)
