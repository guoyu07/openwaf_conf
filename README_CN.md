Synopsis
========
```lua
    #openwaf_init.lua
    
    -- construct a new object - twaf_config
    local twaf_config_m = require "lib.twaf.twaf_conf"
    twaf_config = twaf_config_m:new()
    
    twaf_config:load_default_config("/secone/webapng/lualib/twaf/conf")
    twaf_config:load_access_rule("/secone/webapng/lualib/twaf/conf")
    twaf_config:load_policy_config("/secone/webapng/lualib/twaf/conf",
                                   {twaf_global_conf = 1, twaf_policy_conf = 1})
    twaf_config:load_rules()
    twaf_config:set_main_policy("twaf_global_conf")
    
    -- json geoIP
    twaf_config:load_geoip("/path/to/geo.json")
```

Configuration Directives
================================
* [new](#new)
* [set_main_policy](#set_main_policy)
* [load_default_config](#load_default_config)
* [load_access_rule](#load_access_rule)
* [load_policy_config](#load_policy_config)
* [load_rules](#load_rules)
* [load_geoip](#load_geoip)

new
---
**syntax:** *conf = new()*

set_main_policy
---------------
**syntax:** *set_main_policy(conf, policy_uuid)*

load_default_config
-------------------
**syntax:** *load_default_config(conf, path)*

load_access_rule
----------------
**syntax:** *load_access_rule(conf, path)*

load_policy_config
------------------
**syntax:** *load_policy_config(conf, path, policy_uuids)*

load_rules
----------
**syntax:** *load_rules()*

load_geoip
----------
**syntax:** *conf = load_geoip(conf, path)*

