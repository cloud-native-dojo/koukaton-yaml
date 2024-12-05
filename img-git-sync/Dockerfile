# ベースイメージとして git-sync を使用
FROM k8s.gcr.io/git-sync/git-sync:v3.6.1

# 必要なパッケージのインストール
USER root
RUN apt-get update && apt-get install -y \
    rsync \
    sshpass \
    bash \
    curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# ローカルから `kubectl` と `config` をコンテナにコピー
COPY kubectl /usr/local/bin/kubectl
COPY config /root/.kube/config

# `kubectl` を実行可能にする
RUN chmod +x /usr/local/bin/kubectl

# `git-sync` の既存機能を維持
USER 65533:65533

# デフォルトのエントリポイントを維持
ENTRYPOINT ["/git-sync"]
