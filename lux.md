## ��װnodejs

```sh
# �޷������ /var/lib/dpkg/lock-frontend - open

rm /var/lib/dpkg/lock-frontend
rm /var/lib/dpkg/lock
dpkg --configure -a
# sudo systemctl restart accounts-daemon


apt-get install nodejs
apt-get install nodejs-legacy
apt-get install npm

npm config set registry https://registry.npm.taobao.org
npm config list

npm install -g pm2

ls

pm2 start index.js --name "etwatcher"
#pm2 restart api
#pm2 delete api
#pm2 kill

// �鿴dac����ʵ����ռ���ڴ���õ�ʵ���ڴ�
ps aux | grep dac | sort -nr -k4 | head -n1 | awk '{print $6}'
```





## netstat

-a all
-t tcp
-u udp
-l listen
-p pid list

## ps

-A �����еĽ��̾���ʾ�������� -e ����ͬ����Ч�ã�
-a �� ��ʾ�����ն˻��µ����н��̣����������û��Ľ��̣�
-u �����û�Ϊ���Ľ���״̬ ��
x ��ͨ���� a �������һ��ʹ�ã����г���������Ϣ��
�����ʽ�滮��
l ���ϳ�������ϸ�Ľ��� PID �ĵ���Ϣ�г���
j �������ĸ�ʽ (jobs format)
-f ����һ����Ϊ�����������



�����ڴ��أ�





## nc �������

```shell
test tcp
# nc -z -v [hostname/IP address] [port number]
test udp
# nc -z -v -u [hostname/IP address] [port number]

```

## step by step ��װubuntu

1. rufus-2.15.exe ���� ubuntu-16.04
2. sudo apt-get install openssh-server
3. sudo apt-get install openjdk-8-jdk

�����������(Samba����)
mkdir -p localdir
apt install cifs-utils
mount -t cifs //10.8.30.163/versions /var/jenkins-version -o rw

>> tail:
tail -f ѭ����ȡ
tail -n ����

>> �г����а汾��Ϣ
[root@localhost ~]# lsb_release -a

>> Systemctl  (https://linux.cn/article-5926-1.html)
Systemctl��һ��systemd���ߣ���Ҫ�������systemdϵͳ�ͷ����������
����������ʱ
systemd-analyze [blame]/������  [critical-chain]/�ؼ���
systemctl list-unit-files �г����п��õ�Ԫ
systemctl list-units �г����������е�Ԫ
systemctl --failed  �г�����ʧ�ܵ�Ԫ
systemctl is-enabled crond.service ���ĳ����Ԫ���� cron.service���Ƿ�����
systemctl status firewalld.service ���ĳ����Ԫ������Ƿ����� 
systemctl start httpd.service

systemctl restart httpd.service

systemctl stop httpd.service

systemctl reload httpd.service

systemctl status httpd.service


>> hdfs
�鿴hdfs�洢�ռ䣺
hdfs dfs -du -h / 
hdfs dfs -rmr  hdfs://node35:9000/user/anxin/check-point
docker logs xxx container_id

>> hadoop ��Ⱥ����ʱȷ�����л������û�����һ��
	��
	useradd hadoop
	passwords hadoop
	// ����sudoers
	su
	chmod 777 /etc/sudoers
	vi /etc/sudoers
		-- hadoop    ALL=(ALL)       ALL
	chmod 440 /etc/sudoers

	su hadoop
	sudo mkdir /home/hadoop
	sudo chown /home/hadoop

## �ڴ������Ų�

	free [-m -g...]
	 total        used        free      shared  buff/cache   available
Mem:       12219288     7485148      271236       27104     4462904     4311184
Swap:             0           0           0
	mem:�����ڴ� swapӲ���Ͻ���������ʹ�������ֻ��mem����ǰ����ʵ��ռ����,��û����buffers��cacheʱ���Ż�ʹ�õ�swap
	MEM -- total: �������ڴ��С  used: �ܼƷ��������ʹ�õ�����(����buff/cache)  free: δ��������ڴ�  shared: �����ڴ�(һ��ϵͳ�����õ�)
			buff/cache�� ���䵫δ��ʹ�õ�cache��buffer����
	<https://blog.csdn.net/tianlesoftware/article/details/5463790>
	

	dmidecode -t processor memory [bios, system, baseboard, chassis, processor, memory, cache, connector, slot]
	
	top -d 1(1�����һ��)  -c����ʾ������·�����ƣ�  -i(����ʵ�κ�Idle��zombie����)  -m(���´�������ɺ��˳�)
	��������     �����ȼ���				  
	PID USER      PR  NI�����ȼ�����ֵ��    VIRT������ռ�õ������ڴ�ֵ��    RES������ռ�õ������ڴ�ֵ��
	SHR������ʹ�õĹ����ڴ�ֵ�� S�����̵�״̬������S��ʾ���ߣ�R��ʾ�������У�Z��ʾ����״̬��N��ʾ�ý�������ֵ�Ǹ�����
	%CPU %MEM     TIME+ COMMAND                                                                                                                       
 3581 root      20   0  415048 266628  21956 S   6.3  2.2 512:58.32 kube-apiserver                                                                                                                
  730 root      20   0  708712  61548  16404 S   4.7  0.5 333:30.48 kubelet                                                                                                                       
 3241 root      20   0  139472  57008  15800 S   4.0  0.5 353:34.31 kube-controller  
	

	top��֧�ֵĲ�����
	 ���ո񡷣�����ˢ�¡�
	
	P������CPUʹ�ô�С��������
	
	T������ʱ�䡢�ۼ�ʱ������
	
	q���˳�top���
	
	m���л���ʾ�ڴ���Ϣ��
	
	t���л���ʾ���̺�CPU״̬��Ϣ��
	
	c���л���ʾ�������ƺ����������С�
	
	M������ʹ���ڴ��С��������
	
	W������ǰ����д��~/.toprc�ļ���
	
	SHIFT+M �̶����ڴ�����


?	
	uptime ��ʾϵͳ����ʱ�� ���1����/5����/15���ӵ�ϵͳ����
	17:38:07 up 6 days,  1:13,  4 users,  load average: 0.32, 0.36, 0.45
	
	vmstat��ʾ
	procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
	 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
	 0  0      0 251324 477184 3994764    0    0     8    48   10   12  3  2 94  1  0
	 ���У�
	 io:
		bi - �Ӵ���ÿ���ȡ�Ŀ�����blocks/s��
		bo - ÿ��д�����̵Ŀ�����blocks/s��
	 cpu:
		us - �û�����ռcpu����
		sy - ϵͳռ�ñ���
		id - ����ʱ�����
		wa - cpu�ȴ�δ���Ĵ���IOʱ�����
		
	iostat ����ͳ��CPU��ʹ�������tty�豸��Ӳ�̺�CD-ROM��I/0��

## GREP��ѯ�������

kubectl logs spark-et-driver-savoir | grep 'a\|b'
kubectl logs -n savoir savoir-recv2-d55c84956-lwt47 --tail 100000 | egrep 'savoir_data.*d931eb76-7703-4d8c-a240-8158a02ceeae.*"result":{"code":3002'
netstat -an | grep -E "ESTABLISHED|WAIT"

ʹ�÷�ʽ��egrep [OPTIONS] PATTERN [FILE...] 

����grep -E [OPTIONS] PATTERN [FILE...]

����-i�������ַ��Ĵ�Сд
����-o������ʾƥ�䵽���ַ�������
����-v����ʾ����ģʽƥ�䵽����
����-q����Ĭģʽ����������κ���Ϣ
����-A #����ʾ��ģʽƥ����м����#��
����-B #����ʾ��ģʽƥ����м���ǰ#��
����-C #����ʾ��ģʽƥ����м���ǰ���#��
����-G:֧�ֻ���������ʽ


## chmod �÷�
	u -- User �ļ���Ŀ¼��ӵ����
	g -- Group ����Ⱥ��
	o -- Other
	a -- ȫ���û�
	r -- ��ȡȨ�ޣ����ִ���4
	w -- д��Ȩ�ޣ����ִ���2
	x -- ִ�л��л�Ȩ�ޣ����ִ���1
	- -- �����κ�Ȩ�ޣ����ִ���0
	s -- ���⹦��˵��������ļ���Ŀ¼��Ȩ��
	-R �ݹ鴦��
	chmod u+x f01 // ����ӵ���ߵĿ�ִ������
	chmod u=rwx,g=rw f01
	chmod 764 f01
	
	- rw- r-- r-- 
	��һ���ַ�"-"��ʾ��ͨ�ļ� "d"��ʾĿ¼
	��������ֱ�Ϊ u/g/o �û���Ȩ��


## ����/ɾ�� ָ�����ڵ��ļ�
	find .  -type f  -name *.*  -mtime +10  -exec rm {} \;
	. ��ǰĿ¼
	-type f �����ļ�
	-name *.log �������ƺ�׺log���ļ�
	-mtime +180  ��ѯ180����ǰ���ļ�
	find . -type f -mtime -180 -exec ls -l {} \; | more
	find . -newermt '2016-11-03' ! -newermt '2016-11-04' -exec ls -l {} \;
	
	find . -type d -ctime +10 | xargs rm -rf;
	ɾ���޸�ʱ�䳬��10��������ļ��� ���ȼ��� find /path/to/base/dir/* -type d -ctime +10 -exec rm -rf {} \;��
	
	// ��versionĿ¼ִ��
	find . -type d -mindepth 1 -maxdepth 2  -ctime +10 | xargs rm -rf
	...TO LERN MORE
	
	>>
	-amin <����> ������ָ��ʱ��������ȡ�����ļ���Ŀ¼
	-anewer <�ο��ļ���Ŀ¼> �������ȡʱ�佻ָ���ļ���Ŀ¼�Ĵ�ȡʱ����µ�
	-atime<24Сʱ��>��������ָ��ʱ��������ȡ�����ļ���Ŀ¼����λ��24Сʱ���㣻
	-depth Ŀ¼���
	-daystart �ӱ��տ�ʼ����ʱ��
	-empty Ѱ�ҿ��ļ����ļ���
	-name "*.txt" �����ļ���
	-iname "*.txt" ͬ�ϣ����Դ�Сд
	find . -type f -size +10k ��������10KB���ļ�
	find . -maxdepth 3 -type f ��������������Ϊ3
	find . -mindepth 2 -type f ��������Ⱦ��뵱ǰĿ¼����2����Ŀ¼�������ļ�
	find /usr/ -path "*local*" ·��ƥ��
	find . -regex ".*\(\.txt\|\.pdf\)$" ����������ʽƥ���ļ�·��

## ���̿ռ� �� ���Ҵ��ļ�
```bash
find / -type f -size +200M 2>/dev/null|xargs du -shm|sort -nr|awk '{print $2}'|ls -l

ls -ll
du -h �Cmax-depth=1 *  ���Բ鿴��ǰĿ¼�¸��ļ����ļ��еĴ�С
du -sh ��ѯ��ǰĿ¼�ܴ�С

```


?	
## ��̨��������
  *nohup �������ssh���̹رգ���̨nohup����Ҳ�ᱻ�ر�
  ����ʹ�� screen
  apt-get install screen
  > screen ��Enter�������µ�screen
	> ���µ�screen����ʹ��nohup������ֱ���������������ǵĽ���
	> Ctrl A + D �˳�
	> ��ʾ [detached from 8377.pts-12.node35]
  > �г���ǰ�û�����screen -ls
  > ��������screen -r 8377.pts-12.node35

## �رս�������
https://serverfault.com/questions/684771/best-way-to-disable-swap-in-linux
	1. Identify configured swap devices and files with cat /proc/swaps.
	2. Turn off all swap devices and files with swapoff -a.
	3. Remove any matching reference found in /etc/fstab.
	4. Optional: Destroy any swap devices or files found in step 1 to prevent their reuse. Due to your concerns about leaking sensitive information, you may wish to consider performing some sort of secure wipe.
	
	1. run swapoff -a: this will immediately disable swap
	2. remove any swap entry from /etc/fstab
	3. reboot the system. If the swap is gone, good. If, for some reason, it is still here, you had to remove the swap partition. Repeat steps 1 and 2 and, after that, use fdisk or parted to remove the (now unused) swap partition. Use great care here: removing the wrong partition will have disastrous effects!
	4. reboot

## xshellʹ��
	���������������Ĭ������ΪUTF-8
	������������������ɫ(��ʶ����Ҫ������)
	sudo apt install lrzsz��װ�����ʵ���ļ����䣨��ק�ϴ�/rz �ϴ�/sz ���أ�

## git Permission denied (github)
	ssh-keygen
	copy C:\Users\yww08/.ssh/id_rsa.pub ����
	github.com >personal settings>SSH > New SSH Key
	[ref](https://stackoverflow.com/questions/2643502/how-to-solve-permission-denied-publickey-error-when-using-git)


?	
## ���� alias

	alias ka='kubectl get pods -n anxinyun'
	alias
	
	��~/.bashrc�ļ������
	alias ka='kubectl get pods -n anxinyun -o wide'
	alias kla='kubectl logs -n anxinyun '
	alias ksa='kubectl get services -n anxinyun -o wide'
	alias klat='kubectl logs -n anxinyun --tail 1000'
	alias kda='kubectl delete pod -n anxinyun'
	alias ks='kubectl get pods -n savoir -o wide'
	alias kss='kubectl get services -n savoir -o wide'
	alias kls='kubectl logs -n savoir '
	alias klst='kubectl logs -n savoir --tail 1000'

## Linux <> Windows �ļ�����
	rz 
	sz file

## ElasticSearch���ݵ���
	https://www.npmjs.com/package/elasticdump
	
	npm install elasticdump -g
	
	elasticdump \
  --input=http://iota-m2:9200/aqi_division_hour \
  --output=/home/anxin/tools/aqi_division_hour_mapping.json \
  --type=mapping

  elasticdump \
  --input=http://production.es.com:9200/my_index \
  --output=http://staging.es.com:9200/my_index \
  --type=analyzer
elasticdump \
  --input=http://production.es.com:9200/my_index \
  --output=http://staging.es.com:9200/my_index \
  --type=mapping

  curl -X PUT 'http://172.16.3.5:9200/shining_index' -d@/data/shining_index_mapping.json

  

 ## Ubuntu 16.04 ��װjenkins
 https://www.jianshu.com/p/845f267aec52

������������
systemctl status jenkins.service
����
Failed to start LSB: Start Jenkins at boot time

>> �鿴�Ƿ�װjdk
>> �Ƿ�˿ں��ض����޸�jenkins�˿� https://blog.csdn.net/csfreebird/article/details/9033443

jenkins�ϳ�������go��Ŀ��
https://blog.csdn.net/aixiaoyang168/article/details/82965854

## HDFS
Missing Blocks
1 hdfs fsck -list-corruptfileblocks
1 hdfs fsck / | egrep -v '^\.+$' | grep -v eplica
�鿴����ĳһ���ļ������
1 hdfs fsck /path/to/corrupt/file -locations -blocks -files

�������
����ļ�����Ҫ������ֱ��ɾ�����ļ�(hdfs fsck -delete)����ɾ�������¸���һ�ݵ���Ⱥ��
�������ɾ������Ҫ�������������ҵ���������̨�����ϣ�Ȼ�󵽴˻����ϲ鿴��־��


hadoop fs  -stat %r /anxinyun


163DORCKER
sudo nsenter --target `sudo docker inspect -f {{.State.Pid}} a699a640d325` --mount --uts --ipc --net --pid 
chown 1000:1000 /var/run/docker.sock

## k8s����ɾ��pod
kubectl get pods -n savoir| grep savoir-jupyter | awk '{print $1}' | xargs kubectl delete pod -n savoir

## mosquitto����
	ps -ef | grep mosq
	
	/etc/mosquitto/mosquitto.conf

## ambari �ڵ��ϵķ��� ��ʾ������ʧ

����ambari����
��������� service ambari-agent restart



## journalctl

```shell
journalctl -eu kubelet

# �ں���־
journalctl  -k 

--no-full, --full, -l
����ֶ����ݳ��� ����ʡ�Ժ�(��)�ض�����Ӧ�п� Ĭ����ʾ�������ֶ����� (�����Ĳ��ֻ�����ʾ���߱���ҳ���߽ض�)��

�Ͼɵ� -l/--full ѡ�� �����ڳ������е� --no-full ѡ�����֮��û�������ô���

-a, --all
������ʾ�����ֶ����ݣ���ʹ���а����Ǵ�ӡ�ַ������ֶ����ݳ����� Ĭ������£������Ǵ�ӡ�ַ����ֶν�����дΪ"blob data"(����������)�� ע�⣬��ҳ������ܻ��ٴ�ת��Ǵ�ӡ�ַ�

-f, --follow
ֻ��ʾ���µ���־� ���Ҳ�����ʾ�����ɵ���־� ��ѡ�������� -n ѡ�

-e, --pager-end
�ڷ�ҳ������ ������ת����־��β���� ��ѡ�������� -n1000 ��ȷ����ҳ���߲��ػ���̫�����־�С� ��������������������Ա���ȷ���õ� -n ѡ��ǡ� ע�⣬��ѡ��������� less(1) ��ҳ����

-n, --lines=
������ʾ���µ���־������ --pager-end �� --follow �����˴�ѡ� ��ѡ��Ĳ�������Ϊ���������ʾ��������� ��Ϊ "all" ���ʾ������������ ������������ʾĬ��ֵ10�С�

--no-tail
��ʾ������־�У� Ҳ�������ڳ������е� --lines= ѡ��(��ʹ�� -f ����)��

-r, --reverse
��ת��־�е����˳�� Ҳ����������ʾ���µ���־��

-o, --output=
������־�� �����ʽ�� ����ʹ������ѡ�

short 
����Ĭ��ֵ�� �������ʽ�봫ͳ�� syslog �ļ��ĸ�ʽ���ƣ� ÿ����־һ�С�

short-full 
�� short ���ƣ�ֻ�ǽ�ʱ����ֶ� ���� --since= �� --until= ���ܵĸ�ʽ��ʾ�� �� short �Ĳ�֮ͬ�����ڣ� �����ʱ����л��������ڡ���ݡ�ʱ����Ϣ��������ϵͳ�ı��ػ������޹ء�

short-iso 
�� short ���ƣ�ֻ�ǽ�ʱ����ֶ��� ISO 8601 ��ʽ ��ʾ��

short-iso-precise 
�� short-iso ���ƣ�ֻ�ǽ�ʱ����ֶε����� ��ȷ����΢�뼶��(�����֮һ��)��

short-precise 
�� short ���ƣ�ֻ�ǽ�ʱ����ֶε����� ��ȷ����΢�뼶��(�����֮һ��)��

short-monotonic 
�� short ���ƣ�ֻ�ǽ�ʱ����ֶε���ֵ ���ں�����ʱ��ʼ���㡣

short-unix 
�� short ���ƣ�ֻ�ǽ�ʱ����ֶ���ʾΪ��"UNIXʱ��ԭ��"(1970-1-1 00:00:00 UTC)������������ ��ȷ��΢�뼶��

verbose 
�Խṹ���ĸ�ʽ��ʾ ÿ����־�������ֶΡ�

export 
����־���л�Ϊ�������ֽ��� (�󲿷���Ȼ���ı�)�� �������ڱ��������紫��(��� Journal Export Format �ĵ�)�����ʹ�� systemd-journal-remote.service(8) ���߽��������ֽ���ת��Ϊ���� journald ��ʽ��

json 
����־���ʽ��Ϊ JSON ���󣬲��û��з��ָ�(Ҳ����ÿ����־һ�У���� Journal JSON Format �ĵ�)�� �ֶ�ֵͨ������ JSON �ַ����淶���б��룬������������������⣺

����4096�ֽڵ��ֶν�������Ϊ null ֵ(����ʹ�� --all ѡ��رմ����ԣ������������ᵼ�������ִ��ֳ��� JSON ����)��

��־���������ͬ���ֶΣ������� JSON �����в����� ��ˣ�ͬ���ֶεĶ��ֵ�� JSON �����н��ᱻ ����Ϊһ�����顣

�����Ǵ�ӡ�ַ����UTF8�ַ����ֶΣ� ��������Ϊ����ԭʼ�������ֽڵ�����(���е�ÿ���ֽڶ���Ϊһ���޷�������)��

ע�⣬���ֱ��뷽ʽ�ǿ����(���ڿռ��С������)��

json-pretty 
����־���JSON���ݽṹ��ʽ���� ����ÿ���ֶ�һ�У� �Ա��������Ķ���

json-sse 
����־���JSON�ṹ��ʽ����ÿ����־һ�У������ô����Ű�Χ�� �Է��� Server-Sent Events ��Ҫ��

json-seq 
����־���JSON�ṹ��ʽ���� ͬʱΪÿ����־����һ��ASCII��¼�ָ���(0x1E)ǰ׺�Լ�һ��ASCII���з�(0x0A)��׺���Է��� JavaScript Object Notation (JSON) Text Sequences ("application/json-seq") ��Ҫ��

cat 
����ʾ��־��ʵ�����ݣ� ������ʾ�����־��ص� �κ�Ԫ����(����ʱ���)��

with-unit 
�� short-full ���ƣ� ��������־��ǰ׺��ʹ�õ�Ԫ���ƴ��洫ͳ�� syslog ��ʶ�� ����ڴ�ģ��ʵ���������ĵ�Ԫ�Ƚ������壬 ��Ϊ���ڵ�Ԫ�����а���ʵ����������

--output-fields=
һ�����ŷָ����ֶ������б���ʾ������б��е��ֶΡ� ��Ӱ��Ĭ�����ȫ���ֶε������ʽ(verbose, export, json, json-pretty, json-sse, json-seq)��ע�⣬ "__CURSOR", "__REALTIME_TIMESTAMP", "__MONOTONIC_TIMESTAMP", "_BOOT_ID" �ֶ���Զ����� ���ܱ��ų���

--utc
������ͳһʱ��(UTC) ��ʾʱ��

--no-hostname
����ʾ��Դ�ڱ�������־��Ϣ���������ֶΡ� ��ѡ����� short ϵ�������ʽ(������)��Ч��

-x, --catalog
����־������� ����һЩ�����ԵĶ��ı��� �԰�����һ��˵�� ��־�ĺ��塢 ����Ľ��������֧����̳�� �����ĵ����Լ������κ����ݡ� ����������־���� ��Щ����İ����ı��� ��� Message Catalog Developer Documentation �ĵ���

ע�⣬���Ҫ����־�������bug���棬 �벻Ҫʹ�� ��ѡ�

-q, --quiet
����ģʽ�� Ҳ���ǵ�����ͨ�û��������ʱ�� ����ʾ�κξ�����Ϣ����ʾ��Ϣ�� ���磺 "-- Logs begin at ��", "-- Reboot --"

-m, --merge
�����ʾ ��������������Զ����������־���ڵ����пɼ���־��

-b [ID][��offset], --boot=[ID][��offset]
��ʾ�ض���ĳ����������־�� ���൱�������һ�� "_BOOT_ID=" ƥ��������

���δָ�� ID �� ��offset ������ ���ʾ����ʾ������������־��

���ʡ���� ID �� ��ô�� ��offset ��������ʱ�� ������־ͷ��ʼ������ң� ����(Ҳ����Ϊ��������)������־β��ʼ������ҡ� ������˵�� "-b 1"��ʾ��ʱ��˳������������Ǵ������� "-b 2"���ʾ��ʱ���ϵڶ�����Ǵ������� "-b -0"��ʾ���һ�������� "-b -1"��ʾ��ʱ���ϵڶ������Ǵ������� �Դ����ơ� ��� ��offset Ҳʡ���ˣ� ��ô�൱��"-b -0"�� ���Ǳ��������������һ������(������ --directory ָ���� ����һ̨�����ϵ���־Ŀ¼)��

���ָ����32�ַ��� ID �� ��ô��ʾ�Դ� ID ��������Ǵ�����Ϊ��׼ ����ƫ����(��offset)�� ���㷽��ͬ�ϡ� ���仰˵�� ʡ�� ID ��ʾ�Ա�������Ϊ��׼ ����ƫ����(��offset)��

--list-boots
�г�ÿ�������� ���(Ҳ��������ڱ���������ƫ����)��32�ַ���ID�� ��һ����־��ʱ��������һ����־��ʱ�����

-k, --dmesg
����ʾ�ں���־�������� -b ѡ���Լ� "_TRANSPORT=kernel" ƥ���

-t, --identifier=SYSLOG_IDENTIFIER
����ʾ syslog ʶ���Ϊ SYSLOG_IDENTIFIER ����־�

���Զ��ʹ�ø�ѡ���� ָ�����ʶ�����

-u, --unit=UNIT|PATTERN
����ʾ �����ض���Ԫ����־�� Ҳ���ǵ�Ԫ�������õ��� UNIT ���߷��� PATTERN ģʽ�ĵ�Ԫ�� ���൱�������һ�� "_SYSTEMD_UNIT=UNIT" ƥ����(���� UNIT ��˵)�� ��һ��ƥ����(���� PATTERN ��˵)��

���Զ��ʹ�ô�ѡ������Ӷ�����е�ƥ������(�൱����"OR"�߼�����)��

--user-unit=
����ʾ �����ض��û��Ự��Ԫ����־�� �൱��ͬʱ����� "_SYSTEMD_USER_UNIT=" �� "_UID=" ����ƥ��������

���Զ��ʹ�ô�ѡ������Ӷ�����е�ƥ������(�൱����"OR"�߼�����)��

-p, --priority=
���� ��־�ȼ�(�����ȼ���Χ) ������������ ��־�ȼ�������������֮��� ��Ӧ��ϵ���� (�μ� syslog(3))�� "emerg" (0), "alert" (1), "crit" (2), "err" (3), "warning" (4), "notice" (5), "info" (6), "debug" (7) �� ����Ϊһ�����������ֻ���־�ȼ����ƣ� ���ʾ����ʾС�ڻ���ڴ˵ȼ�����־(Ҳ������Ҫ�̶ȵ��ڻ���ڴ˵ȼ�����־)�� ��ʹ�� FROM..TO.. ����һ����Χ�� ���ʾ����ʾָ���ĵȼ���Χ��(������)����־�� ��ѡ���൱������� "PRIORITY=" ƥ��������

-g, --grep=
ʹ��ָ����������ʽ�� MESSAGE= �ֶν��й��ˣ������ƥ�����־� ����ʹ�� PERL ���ݵ�������ʽ����ϸ�﷨�μ� pcre2pattern(3) �ֲᡣ

���������ʽ�н���Сд��ĸ����ô���Զ����д�Сд�޹ص�ƥ�䣬 ����ʹ�ô�Сд���е�ƥ�䡣�Ƿ��Сд���п���ʹ������� --case-sensitive ѡ��ǿ��ָ����

--case-sensitive[=BOOLEAN]
�Ƿ��������ʽ���д�Сд���е�ƥ�䡣

-c, --cursor=
��ָ�����α�(cursor)��ʼ��ʾ��־�� [��ʾ]ÿ����־����һ��"__CURSOR"�ֶΣ������ڸ�����־��ָ�ơ�

--after-cursor=
��ָ�����α�(cursor) ֮��ʼ��ʾ��־�� ���ʹ���� --show-cursor ѡ� ��Ҳ����ʾ�α걾��

--show-cursor
�����һ����־֮����ʾ�α꣬ ����������������"--"��ͷ��

-- cursor: s=0639��
�α�ľ����ʽ��˽�е�(Ҳ����û�й����Ĺ淶)�� ���һ�仯��

-S, --since=, -U, --until=
��ʾ����ָ��ʱ��(--since=)����־����ʾ����ָ��ʱ��(--until=)����־�� �����ĸ�ʽ���� "2012-10-30 18:17:16" ������ ���ʡ����"ʱ:��:��"���֣����൱����Ϊ "00:00:00" �� �����ʡ����"��"�Ĳ������൱����Ϊ ":00" �� ���ʡ����"��-��-��"���֣����൱����Ϊ��ǰ���ڡ� ����"��-��-�� ʱ:��:��"��ʽ�����������Խ����������ã� (1)��Ϊ "yesterday", "today", "tomorrow" �Ա�ʾ��һ������(00:00:00)�� (2)��Ϊ "now" �Ա�ʾ��ǰʱ�䡣 (3)������"��-��-�� ʱ:��:��"ǰ���� "-"(ǰ��) �� "+"(����) ǰ׺�Ա�ʾ����ڵ�ǰʱ���ƫ�ơ� ����ʱ�������ڵ���ϸ�淶���μ� systemd.time(7) ע�⣬ --output=short-full ����һ˿�������ϸ���������ʽ���ʱ�����

-F, --field=
��ʾ������־��ָ���ֶε����п���ֵ�� [����ע]������SQL��䣺"SELECT DISTINCT ָ���ֶ� FROM ȫ����־"

-N, --fields
���������־�ֶε�����

--system, --user
����ʾ ϵͳ�������ں˵���־(--system)�� ����ʾ��ǰ�û�����־(--user)�� �������ѡ�δָ��������ʾ��ǰ�û������пɼ���־��

-M, --machine=
��ʾ�������������еġ��ض����Ƶı�����������־�� ����������һ���������������ơ�

-D DIR, --directory=DIR
����ʾ �ض�Ŀ¼�е���־�� ������ Ĭ�ϵ�����ʱ��ϵͳ��־Ŀ¼�е���־��

--file=GLOB
GLOB ��һ�� ���԰���"?"��"*"���ļ�·��ƥ��ģʽ�� ��ʾ����ʾ������ָ���� GLOB ģʽƥ����ļ��е���־�� ������Ĭ�ϵ�����ʱ��ϵͳ��־Ŀ¼�е���־�� ���Զ��ʹ�ô�ѡ�� ��ָ�����ƥ��ģʽ(���ģʽ֮����"OR"�߼�����)��

--root=ROOT
�ڶ���־���в���ʱ�� �� ROOT ��Ϊϵͳ�ĸ�Ŀ¼�� ���� --update-catalog ���ᴴ�� ROOT/var/lib/systemd/catalog/database �ļ��� ���ҽ�����ʾ ROOT/run/journal �� ROOT/var/log/journal Ŀ¼�е���־��

--header
��ѡ���������ʾ��־���ݣ� ����������ʾ ��־�ļ��ڲ���ͷ��Ϣ(������Ԫ����)��

--disk-usage
��ѡ���������ʾ��־���ݣ� ����������ʾ ������־�ļ�(�鵵�ļ����ļ�)�Ĵ���ռ��������

--vacuum-size=, --vacuum-time=, --vacuum-files=
��Щѡ���������ʾ��־���ݣ���������������ڵ���־�鵵�ļ�(������������־�ļ�)�����ͷŴ��̿ռ䡣 --vacuum-size= ���������ƹ鵵�ļ���������ʹ����(����ʹ�� "K", "M", "G", "T" ��׺)�� --vacuum-time= ���������ָ��ʱ��֮ǰ�Ĺ鵵(����ʹ�� "s", "m", "h", "days", "weeks", "months", "years" ��׺)�� --vacuum-files= ������������־�鵵�ļ������������ ע�⣬--vacuum-size= �� --disk-usage ��������м��Ч���� ��Ϊ --disk-usage ������ǹ鵵��־����־�������� ͬ����--vacuum-files= Ҳδ��һ���������־�ļ��������� ��Ϊ��ͬ���������ڹ鵵�ļ�������ɾ�������־�ļ���

������ѡ�����ͬʱʹ�ã� ��ͬʱ������ά��ȥ���ƹ鵵�ļ��� ����ĳѡ����Ϊ�㣬 ���ʾȡ����ѡ������ơ�

������ѡ����Ժ� --rotate һ��ʹ�ã� ��ʾ���ȹ���������־�鵵�� Ȼ����ִ����������� ��������ȷ������������л��־�Ĺ鵵�� ����ʹ�����������÷ǳ���Ч��

--list-catalog [128-bit-ID��] 
��Ҫ�г���־������Ϣ�� ���а����Է�����Ϣ�ļ�Ҫ������

�����ȷָ���˷���ID(128-bit-ID)�� ��ô����ʾָ���ķ��ࡣ

--dump-catalog [128-bit-ID��] 
��ϸ�г� ��־������Ϣ (��ʽ�� .catalog �ļ���ͬ)��

�����ȷָ���˷���ID(128-bit-ID)�� ��ô����ʾָ���ķ��ࡣ

--update-catalog
���� ��־���������������ļ��� ÿ����װ��ɾ���������˷����ļ��� ����Ҫִ��һ�δ˶�����

--setup-keys
��ѡ���������ʾ��־���ݣ� ������������һ���µ�FSS(Forward Secure Sealing)��Կ�ԡ� ����Կ�԰���һ��"sealing key" ��һ��"verification key"�� "sealing key"�����ڱ�����־Ŀ¼�У� ��"verification key"����뱣���������ط������ journald.conf(5) �е� Seal= ѡ�

--force
�� --setup-keys ���ã� ��ʾ��ʹ�Ѿ�������FSS(Forward Secure Sealing)��Կ�ԣ� ҲҪǿ���������ɡ�

--interval=
�� --setup-keys ���ã� ָ��"sealing key"�ı仯����� �϶̵�ʱ�����ᵼ��ռ�ø����CPU��Դ�� �����ܹ�����δ������־�仯ʱ�䡣 Ĭ��ֵ�� 15min

--verify
�����־�ļ�������һ���ԡ� �����־�ļ�������ʱ������FSS���ԣ� ����ʹ�� --verify-key= ָ����FSS��"verification key"�� ��ô��ͬʱ������֤��־�ļ�����ʵ�ԡ�

--verify-key=
�� --verify ѡ�����ã� ָ��FSS��"verification key"

--sync
Ҫ����־�ػ����� ������δд����̵���־����ˢд�������ϣ� ����һֱ������ˢд����ʵ�����֮��ŷ��ء� ��˸�������Ա�֤�������ص�ʱ�� �����ڵ��ô������ʱ���֮ǰ����־�� �Ѿ�ȫ����ȫ��ˢд���˴����С�

--flush
Ҫ����־�ػ����� �� /run/log/journal �е���־���� ˢд�� /var/log/journal �� (����־ô洢�豸��ǰ���õĻ�)�� �˲�����һֱ�������������֮��Ż᷵�أ� ��˿���ȷ���ڸ������ʱ�� ����ת��ȷʵ�Ѿ���ɡ� ע�⣬�������ִ��һ�������ġ�һ���Ե�ת�ƶ����� ��û��������Ҫת�ƣ� �������ʲôҲ������ ����Ҳ�᷵��һ�� ��ʾ��������ȷ��ɵķ���ֵ��

--rotate
Ҫ����־�ػ����̹�����־�ļ����������һֱ�����������������֮��Ż᷵�ء� ��־��������ȷ�����л����־�ļ������رա���������������ɹ鵵�� ͬʱ���µĿհ���־�ļ���������������Ϊ�µĻ��־�ļ��� ��ѡ������� --vacuum-size=, --vacuum-time=, --vacuum-file= һ��ʹ�ã� �������־�����Ч�ʡ�

-h, --help
��ʾ��̵İ�����Ϣ���˳���

--version
��ʾ��̵İ汾��Ϣ���˳���

--no-pager
���������������ݹܵ�(pipe)����ҳ����
```

