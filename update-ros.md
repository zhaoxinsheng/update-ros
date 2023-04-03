# rosdep

#### 介绍
用于更新rosdep，通过代理方式，解决rosdep update失败问题
问题出现在于rosdep需要访问`http://raw.githubusercontent.com`,此地址对于国内用户不友好，时常不能正确访问
本方法通过增加代理方式，使得能正确访问上述地址，达到最小改动原则
更详细说明，参考https://www.ncnynl.com/archives/202109/4549.html

#### 软件架构
1. rosdep_update.sh脚本，运行脚本之后，通过替代命令把rosdep相关的脚本文件里面的url地址，都增加ghproxy.com代理能快速访问github.com相应地址
同时备份相应的脚本文件，以便自动恢复。

2. rosdep_recover.sh脚本，运行脚本之后，把之前备份的文件恢复到原来的脚本文件状态，即去掉增加的ghproxy.com代理地址

3. 上述脚本都支持python2.7或python3的，只需要修改脚本中的默认的python_version变量即可。


#### 使用清华源方式，推荐使用

 1.不使用代理，使用国内的清华源替代

`rm update_rosdep_tsinghua.sh ; wget https://gitee.com/ncnynl/rosdep/raw/master/update_rosdep_tsinghua.sh ; chmod +x ./update_rosdep_tsinghua.sh; ./update_rosdep_tsinghua.sh`


 2.执行之后，以后直接使用rosdep update，跟官方使用一致 




#### 使用代理方式，丢弃

1.更新rosdep相关文件，增加代理地址

`rm rosdep_update.sh ; wget https://gitee.com/ncnynl/rosdep/raw/master/rosdep_update.sh ; sudo chmod +x ./rosdep_update.sh; sudo ./rosdep_update.sh`

完成之后，运行rosdep update即不会出现错误提示
脚本只能运行一次，多次运行，会提示重复运行信息

.恢复rosdep相关文件，去掉代理地址

`rm rosdep_recover.sh ; wget https://gitee.com/ncnynl/rosdep/raw/master/rosdep_recover.sh ;  sudo chmod +x ./rosdep_recover.sh; sudo ./rosdep_recover.sh`


####问题提交

1. 可以联系1043931@qq.com (ncnynl)
2. gitee的issue

