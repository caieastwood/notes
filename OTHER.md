EHM ehealthmedicare 主要是US维护，XM主要维护mcws castro mose，US主要维护muse  
EHMP ehealthmedicareplans 主要XM维护  
EHIM ehealthinsurance 主要US维护  

## 项目配置
需要改content的地方  
castro:resource-loader.properties  
mcws:dev.properties 

muse-v2配置  
在`medicare-quick-start/pc/apache-2.4.9/conf.d`下添加muse-v2.conf  
```muse-v2.conf
Alias "/v2" "D:/git/mc-eclipse/muse-v2/dist"
<Directory "D:/git/mc-eclipse/muse-v2/dist">
    Options Indexes FollowSymLinks Includes
	AllowOverride None
	Require all granted

	<FilesMatch "manifest.json$">
	<IfModule mod_headers.c>
		Header set Access-Control-Allow-Origin "*"
	</IfModule>
	</FilesMatch>
</Directory>
```

 

