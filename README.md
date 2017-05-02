# imgur command line tool

private image uploading

## setup

1. create your account on imgur: http://imgur.com/
1. create your app (API Client): https://api.imgur.com/oauth2/addclient
    - Auth type is `OAuth 2 authorization without a callback URL`
    - copy the client-id and the client-secret

the client-id and client-secret are stored on `~/.imgur/app.sh` like this

```bash
mkdir ~/.imgur
cd ~/.imgur
cat <<EOM > app.sh
CLIENT_ID={{client-id}}
CLIENT_SECRET={{client-secret}}
EOM
```

`~/imgur/app.sh` will be sourced.

3. auth your account with the client
    - run `./imgur auth`

## usage

### upload images

```bash
# upload a local image
$ imgur ./image.png
http://i.imgur.com/zzzzzzz.png

# upload via url
$ imgur --url http://example.co.jp/image.png
http://i.imgur.com/zzzzzzz.png

# title, description
$ imgur --title Houbunsha -D "2017/05/01 Morning" ./photo.jpg
http://i.imgur.com/zzzzzzz.png
```

### album creation

```bash
$ imgur album create hoge

$ imgur album ls
TITLE   ID      DELETEHASH
hoge    xxxxx   yyyyyyyyyyyyyyy
```

### upload images into an album

```bash
$ imgur -A yyyyyyyyyyyyyyy ./image.jpg
http://i.imgur.com/zzzzzzz.png
```

