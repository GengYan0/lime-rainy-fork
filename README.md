# rainy-lime

Lime 8.3.2 的构建基线。源码与 8.3.2 发行版逐字节一致，没有任何修改。

存在的目的是给 `rainy-openfl` 与 `rainy-flixel` 钉一个固定的底层版本，让三层的编译结果
可复现，也方便回滚到具体某一天的底层。

## 安装

```bash
haxelib dev lime "D:/libs/rainy-lime"
```

或者：

```bash
haxelib git lime https://github.com/GengYan0/lime-rainy-fork
```

## 钉版本的原因

`lime display <target>` 会把 lime 与 hxcpp 的全局安装路径写进 classpath 第一位，
`haxelib dev` 的路径排在后面，Haxe 按顺序解析、先者胜。所以即使 dev 链接了这个仓库，
**真正参与编译的仍是全局那份**。

实测：有 dev 链接时 lime 与 hxcpp 各出现两次（全局 + 本仓），全局胜出；解除 dev 链接后
只走全局。两者编译结果相同，因为本仓没有改动。

真要 patch lime 本身，需要先把全局路径从 classpath 里挤掉，例如临时改名
`<haxelib>/lime/8,3,2`。光做 `haxelib dev` 不够。

## 边界

- 不含任何补丁。渲染层的改动在 `rainy-openfl`，游戏层的在 `rainy-flixel`。
- 升级到新版 lime 时，`rainy-openfl` 需要同步核对 `Context3D` 与 `OpenGLRenderer` 两处
  内部 API：`__flushGLTextures`、`__bindGLTexture2D`、`__bindGLTextureCubeMap`。
