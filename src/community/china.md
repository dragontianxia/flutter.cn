---
title: Using Flutter in China
title: 在中国网络环境下使用 Flutter
description: Where to find a version of the Flutter site that is localized to Simplified Chinese.
description: 如果你需要在中国网络环境下使用 Flutter，请查阅此页面。
toc: true
---

{% assign path = 'flutter_infra/releases/stable/windows/flutter_windows_v1.0.0-stable.zip' -%}

The Flutter community has made a Simplified Chinese version of the
Flutter website available at
[https://flutter-io.cn](https://flutter-io.cn).

欢迎你来到由中国 Flutter 社区维护的中文 Flutter 资源网站：[https://flutter.cn](https://flutter.cn)

If you’d like to install Flutter using an [installation
bundle](/docs/development/tools/sdk/archive),
you can replace the domain of the original URL with a trusted mirror
to speed it up. For example:

如果你需要下载 [Flutter SDK 的独立打包文件](/docs/development/tools/sdk/archive)，你可以将下载链接前缀替换为你信任的镜像链接。

* 原始链接:<br>
  [`https://storage.googleapis.com/{{path}}`](https://storage.googleapis.com/{{path}})

* 镜像之后的链接:<br>
  [`https://storage.flutter-io.cn/{{path}}`](https://storage.flutter-io.cn/{{path}})

You must also set two environment variables to upgrade Flutter and use the pub
package repository in China. Instructions are below.

同时为了正常升级 Flutter 和通过 pub package 命令获取 packages，你需要设置如下两个环境变量，
设置方式如下：

{{site.alert.important}}

  Use mirror sites only if you _trust_ the provider.
  The Flutter team cannot verify their reliability or security.
  
  使用任意镜像网站的时候，你必须确保你 **信任** 你的镜像提供者。
  Flutter 团队无法确保他们的安全性。
  
{{site.alert.end}}

## Configuring Flutter to use a mirror site

## 为 Flutter 设定镜像配置

If you’re installing or using Flutter in China, it may be helpful to use
a trustworthy local mirror site that hosts Flutter’s dependencies.
To instruct the Flutter tool to use an alternate storage location,
you need to set two environment variables, `PUB_HOSTED_URL` and
`FLUTTER_STORAGE_BASE_URL`, before running the `flutter` command.

如果你在国内使用 Flutter，那么你可能需要找一个与官方同步的可信的镜像站点，
帮助你的 Flutter 命令行工具到该镜像站点下载其所需的资源。
你需要为此设置两个环境变量：“PUB_HOSTED_URL”和“FLUTTER_STORAGE_BASE_URL”，
然后再运行 Flutter 命令行工具。

Taking MacOS or Linux as an example, here are the first few steps in
the setup process for using a mirror site. Run the following in a Bash
shell from the directory where you wish to store your local Flutter clone:

以 macOS 或者与 Linux 相近的系统为例，这里有以下步骤帮助你设定镜像。
在系统终端里执行如下命令设定环境变量，并通过 GitHub 检出 Flutter SDK：


```terminal
$ export PUB_HOSTED_URL=https://pub.flutter-io.cn
$ export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
$ git clone -b dev {{site.github}}/flutter/flutter.git
$ export PATH="$PWD/flutter/bin:$PATH"
$ cd ./flutter
$ flutter doctor
```

After these steps, you should be able to continue
[setting up Flutter](/docs/get-started/editor) normally.
From here on, packages fetched by `flutter pub get` are
downloaded from `flutter-io.cn` in any shell where `PUB_HOSTED_URL`
and `FLUTTER_STORAGE_BASE_URL` are set.

如上步骤设定之后，你可以继续进行 Flutter 安装的下一步：[编辑工具设定](/docs/get-started/editor)，
在这两个环境变量（`PUB_HOSTED_URL` 和 `FLUTTER_STORAGE_BASE_URL`）设定过后，
未来通过命令 `flutter pub get` 获取 packages 的时候，网络请求将会通过
`flutter-io.cn` 提供的镜像进行。

The `flutter-io.cn` server is a provisional mirror for Flutter
dependencies and packages maintained by [GDG China]().
The Flutter team cannot guarantee long-term availability of this service.
You’re free to use other mirrors if they become available. If you’re
interested in setting up your own mirror in China, contact
[flutter-dev@googlegroups.com](mailto:flutter-dev@googlegroups.com)
for assistance.

`flutter-io.cn` 所提供的镜像由中国的 Flutter 开发者社区提供和维护，
Flutter 团队无法保证其的长期稳定运作，你也可以自由使用其他可信的机构提供的镜像服务。

## Community-run mirror sites

## 社区运行的镜像站点

如下列表为目前在国内提供镜像的社区，
由于镜像的实现方式有所不同，可能回导致数据的滞后等问题。
我们制作了一个 [镜像可用性监控页面](https://stats.uptimerobot.com/JZK3ZTql79) 供参考。

### Flutter 社区

社区主镜像，采用多种方式同步 Flutter 开发者资源（推荐）。

```terminal
$ export PUB_HOSTED_URL=https://pub.flutter-io.cn
$ export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

### 上海交大 Linux 用户组

使用反向代理方式建立的 Flutter 镜像，数据与站源实时同步。
Pub API 返回值未做处理，可能造成无法访问的情况。

```terminal
$ export PUB_HOSTED_URL=https://dart-pub.mirrors.sjtug.sjtu.edu.cn
$ export FLUTTER_STORAGE_BASE_URL=https://mirrors.sjtug.sjtu.edu.cn
```

### 清华大学 TUNA 协会

定时与 Flutter 社区 Storage 镜像同步，Pub API 采取定时主动抓取策略，
镜像配置了完善的失败回源策略（推荐）。
查看帮助文档：
[Flutter 镜像安装帮助](https://mirrors.tuna.tsinghua.edu.cn/help/flutter/)，
[Pub 镜像安装帮助](https://mirrors.tuna.tsinghua.edu.cn/help/dart-pub/)。

```terminal
$ export PUB_HOSTED_URL=https://mirrors.tuna.tsinghua.edu.cn/dart-pub
$ export FLUTTER_STORAGE_BASE_URL=https://mirrors.tuna.tsinghua.edu.cn/flutter
```

### CNNIC

基于 TUNA 协会的镜像服务，数据策略与 TUNA 一致，通过非教育网的域名访问。

```terminal
$ export PUB_HOSTED_URL=http://mirrors.cnnic.cn/dart-pub
$ export FLUTTER_STORAGE_BASE_URL=http://mirrors.cnnic.cn/flutter
```

### 腾讯云开源镜像站

定时（每天凌晨）与 TUNA 协会镜像同步，数据有延迟，访问速度有待反馈。

```terminal
$ export PUB_HOSTED_URL=https://mirrors.cloud.tencent.com/dart-pub
$ export FLUTTER_STORAGE_BASE_URL=https://mirrors.cloud.tencent.com/flutter
```

### 已知问题

- 上海交大 Linux 用户组镜像的 Pub API 返回值未做处理，会导致用户获取 package 下载地址时从 Google 服务器获取资源，可能造成 Packages 无法下载的情况。（暂未修复）
- 上海大学的镜像暂时只允许校内访问，故暂未展示。
- 已知的 Flutter 中国镜像目前均不支持上传 packages / plugins 到 Pub site。这个过程通常需要登陆谷歌账号，而这将是一个无法绕开且复杂的挑战，故暂无修复计划。

## 致谢

本页面列出的镜像由提供者分别维护，我们确保上述列出的镜像提供方不会对数据进行恶意修改，
因为国内网络情况的复杂性和特殊性，我们无法保证镜像长期稳定性和访问速度，请谅解。

如果在镜像使用中有任何问题，欢迎通过邮件与我们联系：cfug-dev@googlegroups.com。
非常感谢所有帮助 Flutter 在国内维护社区基础设施建设资源的社区和公司，查看
[详细致谢名单](/about/docs-cn)。
