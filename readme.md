# 👉 [subosito/flutter-action](https://github.com/subosito/flutter-action) Flutter environment for use in GitHub Actions. It works on Linux, Windows, and macOS.

---

# DockerFlutterBuilder

DockerFlutterBuilder 是一个基于 Docker 的工具，用于自动化构建 Flutter 项目的多平台版本。它简化了 Android、iOS、Web 和桌面平台的构建过程，通过使用一致的 Docker 容器，减少了环境相关的问题，提升了跨平台开发的效率。

## 功能

- 多平台构建：支持 Android、iOS、Web 和桌面(Windows、Linux、MacOS)平台，通过统一的构建环境实现。
- 环境一致性：Docker 容器确保所有机器上的构建环境完全一致。
- 易于使用：通过最小化配置，简化了构建过程。
- 可扩展：非常适合用于 CI/CD 流水线以及跨平台开发团队。

## TODO

- [ ] Windows
- [ ] MacOS
- [ ] IOS

## 使用示例

### Android

```yaml
name: Flutter Build for Android Apk with Docker

on: [ workflow_dispatch ]

jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: ppbymrtk/flutter:0.1.0.android
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Dependencies
        run: flutter pub get
      - name: Analyze
        run: flutter analyze
      - name: Build
        run: flutter build apk --release
      # run: flutter build apk --release --split-per-abi
      - name: Artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build
          path: build/
```

### Linux

```yaml
name: Flutter Build for Linux with Docker

on: [ workflow_dispatch ]

jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: ppbymrtk/flutter:0.1.0.linux
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Dependencies
        run: flutter pub get
      - name: Analyze
        run: flutter analyze
      - name: Build
        run: flutter build linux --release
      - name: Artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build
          path: build/
```

### Web

```yaml
name: Flutter Build for Web with Docker

on: [ workflow_dispatch ]

jobs:
  build:
    runs-on: ubuntu-latest
    container:
      image: ppbymrtk/flutter:0.1.0.web
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Dependencies
        run: flutter pub get
      - name: Analyze
        run: flutter analyze
      - name: Build
        run: flutter build web --release
      - name: Artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build
          path: build/
```

## 构建

```bash
docker build -t ppbymrtk/flutter:version.web --progress=plain web
docker build -t ppbymrtk/flutter:version.linux --progress=plain linux
docker build -t ppbymrtk/flutter:version.android --progress=plain android
docker build -t ppbymrtk/flutter:version.windows --progress=plain windows
docker build -t ppbymrtk/flutter:version.macos --progress=plain macos
docker build -t ppbymrtk/flutter:version.ios --progress=plain ios
```

## 发布

```bash
docker push ppbymrtk/flutter:version.web
docker push ppbymrtk/flutter:version.linux
docker push ppbymrtk/flutter:version.android
docker push ppbymrtk/flutter:version.windows
docker push ppbymrtk/flutter:version.macos
docker push ppbymrtk/flutter:version.io
```

## 资源

- [instrumentisto/flutter-docker-image](https://github.com/instrumentisto/flutter-docker-image)
- [cirruslabs/docker-images-android](https://github.com/cirruslabs/docker-images-android)


