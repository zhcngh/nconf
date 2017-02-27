# nconf
使用nconf配置或读取config.json

## 安装nconf模块
  ```
  npm install --save nconf
  ```

## 新建config.js 编写save\read方法
  ```
const nconf = require('nconf');
nconf.file({ file: getUserHome() + 'config.json' });

function saveSetting(settingKey, settingValue) {
    nconf.set(settingKey, settingValue);
    nconf.save();
}

function readSetting(settingKey) {
    nconf.load();
    return nconf.get(settingKey);
}

function getUserHome() {
    return process.env[(process.platform == 'win32') ? 'USERPROFILE' : 'HOME'];
}
module.exports = {
    saveSetting: saveSetting,
    readSetting: readSetting
}
```

##新建config.json配置文件
```
 
```
##main.js和其它文件中使用
```
const config = require('config');
var size = config.readSetting('Size');
if(!size){  //如果读取不到，设置一个
config.saveSetting('color',['500','500']);
}
```
