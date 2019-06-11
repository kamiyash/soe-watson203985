# これはどういうプログラムですか？

* Service Orchestrate Engineと申しまして、VoiceGateWayとWatson Asisstantの間に置くアプリです。
* 通常、VoiceGateWayからWatson Assistantにテキストデータを流すのですが、Watoson Assistantでは外部システム連携処理等を実装することができません。Watson Assistantの代わりに色々やる、それがSOEです。

# どこに配置するプログラムですか？

* IBM Cloud(Public)のCloud FoundryのSDK for Node.jsに配置するアプリケーションです。
* また、本プログラムは IBM Cloud(Public) > ToolChane > Cloud Foundryアプリ開発から作成されたGitLabに置くことを想定しています。
* 新規ToolChaneの作成時にソース・リポジトリーのURLの指定があります。その時にこのGithubのソースをコピーしてください。」

# IBM Cloudにてデプロイする際の注意点
* リポジトリ名は無駄に長くしてください。
  * IBM Cloud内で名前が被ってエラーになる可能性も。
* Watson Assistantのusername/passowrd/workspace等の情報は、app/.envファイルを参照するように設計されています。
  * ですが、もちろん.envは.gitignoreに含まれています。
  * また、Derivery Pipelineからデプロイされるので、コンテナのBuild時に.envファイルを作成し、秘密情報を保存する必要があります。
  * Delivery PipelineのBuildステージにて、ビルダータイプをシェルスクリプトにして、echo '<秘密情報>' >> .envということを繰り返して、コンテナに.envファイルを作成させて下さい。
  * 何回やってもコンテナに環境情報を覚えさせることはできませんでした。ビルダータイプをシェルスクリプトにして、export AAA=BBBとしても実際のアプリには環境変数がなかった。

# soe
# soe-watson203985
