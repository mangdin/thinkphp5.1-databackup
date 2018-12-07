# thinkphp5.1-databackup
thinkphp5.1 数据库备份组件

1.传入参数
$config=array(
    'path'     => './data/',//数据库备份路径
    'part'     => 20971520,//数据库备份卷大小
    'compress' => 0,//数据库备份文件是否启用压缩 0不压缩 1 压缩
    'level'    => 9 //数据库备份文件压缩级别 1普通 4 一般  9最高
);
$db = new Backup($config);

2.数据库列表
$list = $db->dataList();

3.数据库备份
（1）备份全部
 $res = $db->sql_all();
（2）备份单个表
 //$start 代表起始备份位置，全部备份填0即可
 $res = $db->backup($name,$start);
 备份成功返回值为0;

4.备份数据列表
$list = $db->fileList();

5.备份数据还原(单个表)
//$name 为sql文件名，$start 代表起始还原位置
$res = $db->setFile(['name' => $name])->import($sart);

6.删除备份文件
$res = $db->delFile($name);
