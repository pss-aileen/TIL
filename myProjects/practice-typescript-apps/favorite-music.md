# Favorite Music

## Getting Started: Spotify Web API を表示するまでの流れ

[Web API | Spotify for Developers](https://developer.spotify.com/documentation/web-api)

### 手順1 利用規約に同意

### 手順2 dashboard でアプリを作成

[アプリ | 開発者向け Spotify](https://developer.spotify.com/documentation/web-api/concepts/apps)

こちらの通りに作成

### 手順3 アクセストークンのリクエスト

```sh
curl -X POST "https://accounts.spotify.com/api/token" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "grant_type=client_credentials&client_id=your-client-id&client_secret=your-client-secret"
```

ターミナルで上記を実行、トークンがかえされる（1時間だけ有効）

```json
{"access_token":"XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
"token_type":"Bearer",
"expires_in":3600}
```

### 手順4 データをリクエスト

```sh
curl "https://api.spotify.com/v1/artists/4Z8W4fKeB5YxbusRsdQVPb" \
     -H "Authorization: Bearer XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

上記をたたくと、以下がかえってきた

```json
{
  "external_urls" : {
    "spotify" : "https://open.spotify.com/artist/4Z8W4fKeB5YxbusRsdQVPb"
  },
  "followers" : {
    "href" : null,
    "total" : 9979198
  },
  "genres" : [ "alternative rock", "art rock", "melancholia", "oxford indie", "permanent wave", "rock" ],
  "href" : "https://api.spotify.com/v1/artists/4Z8W4fKeB5YxbusRsdQVPb",
  "id" : "4Z8W4fKeB5YxbusRsdQVPb",
  "images" : [ {
    "height" : 640,
    "url" : "https://i.scdn.co/image/ab6761610000e5eba03696716c9ee605006047fd",
    "width" : 640
  }, {
    "height" : 320,
    "url" : "https://i.scdn.co/image/ab67616100005174a03696716c9ee605006047fd",
    "width" : 320
  }, {
    "height" : 160,
    "url" : "https://i.scdn.co/image/ab6761610000f178a03696716c9ee605006047fd",
    "width" : 160
  } ],
  "name" : "Radiohead",
  "popularity" : 79,
  "type" : "artist",
  "uri" : "spotify:artist:4Z8W4fKeB5YxbusRsdQVPb"
}
```

TypeScriptで取得しようとするとこうなる。

```ts
fetch("https://api.spotify.com/v1/artists/4Z8W4fKeB5YxbusRsdQVPb",
  {
    method: "GET",
    headers: {
      "Authorization": token
    }
  }
)
```

### .envの設定

- [GitHub Actions でのシークレットの使用 - GitHub Docs](https://docs.github.com/ja/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository)