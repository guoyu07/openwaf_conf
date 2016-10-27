Table of Contents
=================
* [Synopsis](#synopsis)
* [Description](#description)
* [API](#api)

Synopsis
========
```lua
    #openwaf_init.lua
    
    -- construct a new object - twaf_config
    local twaf_config_m = require "lib.twaf.twaf_conf"
    twaf_config = twaf_config_m:new()
    
    twaf_config:load_default_config("/opt/OpenWAF/conf/twaf_default_conf.json")
    twaf_config:load_policy_config("/opt/OpenWAF/conf", {twaf_policy_conf = 1})
    twaf_config:load_access_rule("/opt/OpenWAF/conf")
    twaf_config:load_rules()
    twaf_config:set_main_policy("twaf_policy_conf")
    
    -- GeoIP 
    twaf_config:load_geoip_country_ipv4("/opt/OpenWAF/lib/twaf/inc/knowledge_db/geo_country/GeoIP.dat")
    twaf_config:load_geoip_country_ipv6("/opt/OpenWAF/lib/twaf/inc/knowledge_db/geo_country/GeoIPv6.dat")
```

Description
===========
twaf_conf是OpenWAF的静态配置管理模块，主要负责加载缺省配置文件，加载接入规则文件，加载策略配置文件，加载规则库，以及GeoIP库

API
=============
* [new](#new)
* [load_default_config](#load_default_config)
* [load_policy_config](#load_policy_config)
* [set_main_policy](#set_main_policy)
* [load_access_rule](#load_access_rule)
* [load_rules](#load_rules)
* [load_geoip_country_ipv4](#load_geoip_country_ipv4)
* [load_geoip_country_ipv6](#load_geoip_country_ipv6)

new
---
**syntax:** *twaf_config = require "lib.twaf.twaf_conf":new()*

创建配置管理对象

load_default_config
-------------------
**syntax:** *twaf_config:load_default_config(path)*

加载缺省配置文件

load_policy_config
------------------
**syntax:** *twaf_config:load_policy_config(path, policy_uuids)*

加载策略配置文件

```
若文件目录结构为
/
|--- opt
      |--- OpenWAF
              |---conf
                   |---policy_1.json
                   |---policy_2.lua

则加载策略配置文件可为 twaf_config:load_policy_config("/opt/OpenWAF/conf", {policy_1 = 1, policy_2 = 1})
```

set_main_policy
---------------
**syntax:** *twaf_config:set_main_policy(policy_uuid)*

指定缺省策略，未指定则缺省策略为“twaf_default_conf”

接入规则中未指定使用的策略，则走缺省策略

load_access_rule
----------------
**syntax:** *twaf_config:load_access_rule(path)*

加载接入规则文件

load_rules
----------
**syntax:** *twaf_config:load_rules()*

加载规则库

load_geoip_country_ipv4
-----------------------
**syntax:** *twaf_config:load_geoip_country_ipv4(path)*

加载国家级别ipv4的GEOIP库

load_geoip_country_ipv6
-----------------------
**syntax:** *twaf_config:load_geoip_country_ipv6(path)*

加载国家级别ipv6的GEOIP库
