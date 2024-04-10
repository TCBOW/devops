# shellをexecuterにgitlab-runnerをインストールする

### gitlab-runner_<arch>.deb　をダウンロード
https://gitlab-docs.creationline.com/runner/install/bleeding-edge.html#download-any-other-tagged-release

### gitlab-runner 16.6.2 の場合
https://s3.amazonaws.com/gitlab-runner-downloads/v16.6.2/deb/gitlab-runner_amd64.deb

### ランナーのインストール
sudo dpkg -i ~/Downloads/gitlab-runner_amd64.deb

### トークンの取得
リポジトリ選択＞左のメニュー＞設定＞CI/CD＞Runner＞新規プロジェクトRunnerの点点をクリックしてコピーする。
取得したトークンを下記に登録すれば良い。

### 登録トークンの場合

sudo gitlab-runner register  --non-interactive --executor "shell" --url "http://192.168.1.14:8080/"  --registration-token "GR13489413jGTgBZFQD87xQTa3Cgf"

sudo gitlab-runner register  --non-interactive --executor "shell" --url "http://192.168.1.14" --registration-token "GR1348941yx3P_ggyFx3morJmb4v3"

### 認証トークンの場合
sudo gitlab-runner register     --non-interactive     --executor "shell"     --url "http://192.168.1.14:8080/"     --token "gtrb-GR13489413jGTgBZFQD87xQTa3Cgf"

以上 // shellでの実行ができるようになる

# その他

### docker-compose.ymlの変更を反映させる手順(バージョン変更した場合などに実施する)
docker ps   # container IDを確認する
docker stop <ID>
docker-compose up -d

### gitlabが起動しない場合のログの確認
docker logs --tail 50 --follow --timestamps gitlab_gitlab_1

### dockerのgitlabバージョンで所望のものがあるか確認する場合下記で探す
https://hub.docker.com/r/gitlab/gitlab-ee/tags?page=2
