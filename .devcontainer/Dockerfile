# ベースイメージとして公式のFlutterイメージを使用
FROM cirrusci/flutter:stable

# パッケージリストを更新し、必要なツールをインストール
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    git \
    curl \
    unzip \
    wget \
    xz-utils

# 作業ディレクトリを設定
WORKDIR /workspace

# プロジェクトの依存関係をコピーしてインストール
COPY pubspec.yaml pubspec.lock ./
RUN flutter pub get

# アプリケーションソースをコピー
COPY . .

# Flutterの依存関係をインストール
RUN flutter pub get

# 初期化コマンドを実行
CMD ["flutter", "doctor"]
