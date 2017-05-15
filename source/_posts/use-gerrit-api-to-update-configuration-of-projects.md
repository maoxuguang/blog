---
title: use gerrit api to update configuration of projects
date: 2017-03-17 20:43:27
tags: gerrit
---
遇到的问题:
1. unauthenticated
Gerrit用的是LDAP， 所以用http密码authentication要加上参数--digest参数，在gerrit端设置httppassword
2. not found
这个是因为我们的project名字里有反斜线，要用%2f转义
3. Invalid application/json in request
json格式不正确

脚本：
```
#!/bin/bash

#escape the slash in project name and get the project list
sed -i "s#/#%2f#g" projects.txt
projectList=$(cat projects.txt)

for name in $projectList;do
    cmd="curl -X PUT --digest --user username:password --data-binary @subConf.txt --header 'Content-Type: application/json; charset=UTF-8' http://gerrit.nsn-net.net/a/projects/$name/config"
    echo $cmd >> setConf.log 
	eval $cmd >> setConf.log
done
```

