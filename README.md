# rime-lua-select-character
Rime / 以词定字

## 使用

以词定字可以让你在输入一个词组后，选取这个词组的开头或结尾的一个字直接上屏，比如想要打“嫉”这个字，可以先打“嫉妒”再按 `[` 键选择第一个字，这样在输入一些生僻字的时候会有所帮助。

## 安装

以词定字须附加在某一个具体的输入方案上，以朙月拼音（luna_pinyin）为例，可执行以下[东风破](https://github.com/rime/plum)口令：

``` shell
bash rime-install BlindingDark/rime-lua-select-character:customize:schema=luna_pinyin
```

若想更新到最新版，则重复执行安装命令即可。  
由于 plum 目前还不能自动引入 lua 脚本，所以在使用以词定字之前还需要手动在 rime 配置目录下的 `rime.lua` 文件中添加以下内容，`rime.lua` 文件不存在可手动创建。

``` lua
-- select_character_processor: 以词定字
-- 详见 `lua/select_character.lua`
select_character_processor = require("select_character")
```

以上步骤都做好之后重新部署 rime 即可生效。

### Rime Lua 脚本扩展的安装方式

以词定字依托于 [RIME Lua 脚本扩展](https://github.com/hchunhui/librime-lua)，Windows, Mac, Android 用户请将 rime 升级到最新发布的版本。  
Linux 用户需要安装带有 lua 扩展的 librime 版本，以下是部分发行版的安装方式

- ArchLinux
  ``` shell
  yay -S librime
  ```

  推荐使用 `fcitx5` 并配合 `fcitx5-configtool` 在 GUI 下设置开启 lua 插件。
  

Linux 用户也可以按照[这里的说明](https://github.com/hchunhui/librime-lua#instructions)进行编译安装

## 配置

默认情况下，按 `[` 键将会选中词组的第一个字，按 `]` 键将会选中词组的最后一个字。  
你可以通过修改 `key_binder/select_first_character` 以及 `key_binder/select_last_character` 的值来改变默认按键。  

如你可以这样修改 `default.yaml` 以使用逗号和点号进行选字

``` yaml
key_binder:
  select_first_character: 'comma'
  select_last_character: 'period'
```

可用的键值列表参见 [Rime Schema.yaml 详解](https://github.com/LEOYoon-Tsaw/Rime_collections/blob/master/Rime_description.md#%E4%B8%83%E5%85%B6%E5%AE%83)
