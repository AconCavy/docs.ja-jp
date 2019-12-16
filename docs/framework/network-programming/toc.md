# [.NET Framework のネットワーク プログラミング](index.md)
## [ネットワーク プログラミング方法のトピック](network-programming-how-to-topics.md)
## [プラグ可能なプロトコルの概要](introducing-pluggable-protocols.md)
## [データの要求](requesting-data.md)
### [インターネット要求の作成](creating-internet-requests.md)
### [方法: Web ページを要求し、ストリームとして結果を取得する](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
### [方法: WebRequest クラスを使用してデータを要求する](how-to-request-data-using-the-webrequest-class.md)
### [方法: WebRequest クラスを使用してデータを送信する](how-to-send-data-using-the-webrequest-class.md)
### [方法: WebRequest に一致するプロトコル固有の WebResponse を取得する](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
### [ネットワーク上のストリームの使用](using-streams-on-the-network.md)
### [非同期要求を行う](making-asynchronous-requests.md)
### [エラーの処理](handling-errors.md)
## [プラグ可能なプロトコルのプログラミング](programming-pluggable-protocols.md)
### [方法: WebRequest を使用してカスタム プロトコルを登録する](how-to-register-a-custom-protocol-using-webrequest.md)
### [方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
### [WebRequest からの派生](deriving-from-webrequest.md)
### [WebResponse からの派生](deriving-from-webresponse.md)
## [アプリケーション プロトコルの使用](using-application-protocols.md)
### [HTTP](http.md)
#### [HttpListener](httplistener.md)
### [方法: HTTP 固有のプロパティにアクセスする](how-to-access-http-specific-properties.md)
### [接続の管理](managing-connections.md)
#### [接続のグループ化](connection-grouping.md)
#### [方法: グループの接続にユーザー情報を割り当てる](how-to-assign-user-information-to-group-connections.md)
### [TCP、UDP](tcp-udp.md)
#### [TCP サービスの使用](using-tcp-services.md)
#### [UDP サービスの使用](using-udp-services.md)
### [ソケット](sockets.md)
#### [方法: ソケットを作成する](how-to-create-a-socket.md)
#### [クライアント ソケットの使用](using-client-sockets.md)
##### [同期クライアント ソケットの使用](using-a-synchronous-client-socket.md)
##### [非同期クライアント ソケットの使用](using-an-asynchronous-client-socket.md)
#### [リッスン (ソケットで)](listening-with-sockets.md)
##### [同期サーバー ソケットの使用](using-a-synchronous-server-socket.md)
##### [非同期サーバー ソケットの使用](using-an-asynchronous-server-socket.md)
#### [ソケットのコード例](socket-code-examples.md)
##### [同期クライアント ソケットの例](synchronous-client-socket-example.md)
##### [同期サーバー ソケットの例](synchronous-server-socket-example.md)
##### [非同期クライアント ソケットの例](asynchronous-client-socket-example.md)
##### [非同期サーバー ソケットの例](asynchronous-server-socket-example.md)
### [FTP](ftp.md)
#### [方法: FTP を使用してファイルをダウンロードする](how-to-download-files-with-ftp.md)
#### [方法: FTP を使用してファイルをアップロードする](how-to-upload-files-with-ftp.md)
#### [方法: FTP でディレクトリの内容を一覧表示する](how-to-list-directory-contents-with-ftp.md)
### [Understanding WebRequest の問題と例外](understanding-webrequest-problems-and-exceptions.md)
## [インターネット プロトコル バージョン 6](internet-protocol-version-6.md)
### [IPv6 のアドレス指定](ipv6-addressing.md)
### [IPv6 ルーティング](ipv6-routing.md)
### [IPv6 の自動構成](ipv6-auto-configuration.md)
### [有効にして、IPv6 を無効化](enabling-and-disabling-ipv6.md)
### [方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)
## [インターネット アプリケーションの構成](configuring-internet-applications.md)
## [.NET Framework のネットワークのトレース](network-tracing.md)
### [ネットワークのトレースの解釈](interpreting-network-tracing.md)
### [ネットワークのトレースを有効にします。](enabling-network-tracing.md)
### [方法: ネットワークのトレースを構成する](how-to-configure-network-tracing.md)
## [ネットワーク アプリケーションのキャッシュ管理](cache-management-for-network-applications.md)
### [キャッシュ ポリシー](cache-policy.md)
### [場所ベースのキャッシュ ポリシー](location-based-cache-policies.md)
### [時間ベースのキャッシュ ポリシー](time-based-cache-policies.md)
#### [キャッシュ ポリシーの相互作用 - 最大有効期間と最大期限延長](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
#### [キャッシュ ポリシーの相互作用 - 最大有効期間と最小鮮度](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
### [ネットワーク アプリケーションでのキャッシュの構成](configuring-caching-in-network-applications.md)
#### [方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する](how-to-set-a-location-based-cache-policy-for-an-application.md)
#### [方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する](how-to-set-the-default-time-based-cache-policy-for-an-application.md)
#### [方法: 時間ベースのキャッシュ ポリシーをカスタマイズする](how-to-customize-a-time-based-cache-policy.md)
#### [方法: 要求のキャッシュ ポリシーを設定する](how-to-set-cache-policy-for-a-request.md)
## [ネットワーク プログラミングにおけるセキュリティ](security-in-network-programming.md)
### [Secure Sockets Layer の使用](using-secure-sockets-layer.md)
#### [証明書の選択と検証](certificate-selection-and-validation.md)
### [インターネット認証](internet-authentication.md)
#### [基本認証とダイジェスト認証](basic-and-digest-authentication.md)
#### [NTLM と Kerberos 認証](ntlm-and-kerberos-authentication.md)
### [Web およびソケットのアクセス許可](web-and-socket-permissions.md)
## [System.Net クラスのベスト プラクティス](best-practices-for-system-net-classes.md)
## [プロキシを介したインターネットへのアクセス](accessing-the-internet-through-a-proxy.md)
### [プロキシ構成](proxy-configuration.md)
### [自動プロキシ検出](automatic-proxy-detection.md)
### [方法: WebRequest でインターネットとの通信にプロキシを使用できるようにする](how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet.md)
### [方法: グローバル プロキシの選択をオーバーライドする](how-to-override-a-global-proxy-selection.md)
## [ネットワーク情報](networkinformation.md)
### [方法: ネットワークの可用性とアドレスの変更を検出する](how-to-detect-network-availability-and-address-changes.md)
### [方法: インターフェイス情報とプロトコル情報を取得する](how-to-get-interface-and-protocol-information.md)
### [方法: ホストに対して ping を実行](how-to-ping-a-host.md)
## [バージョン 2.0 での System.Uri 名前空間の変更](changes-to-the-system-uri-namespace-in-version-2-0.md)
## [System.Uri での International Resource Identifier のサポート](international-resource-identifier-support-in-system-uri.md)
## [バージョン 3.5 のソケット パフォーマンスの強化](socket-performance-enhancements-in-version-3-5.md)
## [ピア名解決プロトコル](peer-name-resolution-protocol.md)
### [ピア名と PNRP Id](peer-names-and-pnrp-ids.md)
### [ピア名前公開と解決](peer-name-publication-and-resolution.md)
### [PNRP クラウド](pnrp-clouds.md)
### [PNRP キャッシュ](pnrp-caches.md)
### [アプリケーションの開発での PNRP](pnrp-in-application-development.md)
## [ピアツーピア コラボレーション](peer-to-peer-collaboration.md)
### [System.Net.PeerToPeer.Collaboration 名前空間について](about-the-system-net-peertopeer-collaboration-namespace.md)
### [ピア ツー ピア ネットワー キング シナリオ](peer-to-peer-networking-scenarios.md)
## [バージョン 3.5 SP1 における HttpWebRequest の NTLM 認証への変更](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)
## [統合 Windows 認証と拡張保護](integrated-windows-authentication-with-extended-protection.md)
## [IPv6 および Teredo を使用した NAT トラバーサル](nat-traversal-using-ipv6-and-teredo.md)
## [Windows ストア アプリのネットワーク分離](network-isolation-for-windows-store-apps.md)
## [ネットワーク プログラミングのサンプル](network-programming-samples.md)