# Post

### Docs on Byte posts and the post API

## Post structure

```json
{
	"id": "POST_ID",
	"type": 0,
	"authorID": "ACCOUNT_ID",
	"caption": "",
	"allowCuration": true,
	"allowRemix": false,
	"mentions": [
		<List of mention structures>
	],
	"date": 1580069942,
	"videoSrc": "https://e6k9t9a9.stackpathcdn.com/videos/3TIV4MY44BF5BDDDZ7HUQLTKVU-h264.mp4",
	"thumbSrc": "https://e6k9t9a9.stackpathcdn.com/videos/3TIV4MY44BF5BDDDZ7HUQLTKVU.jpg",
	"commentCount": 4,
	"comments": [
		<List of comment structures>
	],
	"likeCount": 11,
	"likedByMe": false,
	"loopCount": 48,
	"rebytedByMe": false
}
```

## Comment structure

```json
{
	"id": "POST_ID-RANDM_ID",
	"postID": "POST_ID",
	"authorID": "ACCOUNT_ID",
	"body": "Hi @username",
	"mentions": [
		<List of mention structures>
	],
	"date": 1580069946
}
```

## Mention structure

```json
{
	"accountID": "ACCOUNT_ID", // Account ID of person mentioned
	"username": "username", // mentioned users username
	"text": "@username", // the text used to mention the user
	"range": { // the start and stop positions in the UTF-8 string
		"start": 0,
		"stop": 9
	},
	"byteRange": { // the start and stop positions in the data
		"start": 0,
		"stop": 12
	}
}
```

# Endpoints

## [POST] /post/id/POST_ID/loop

Increments the posts loop count. Has a rate limit

### Response

```json
{
	"data": {
		"loopCount": 111111,
		"postID": "POST_ID"
	},
	"success": 1
}
```


## [PUT] /post/id/POST_ID/feedback/like

Likes/dislikes the post

### Body

```json
{
	"postID": "POST_ID"
}
```


## [POST] /post/id/POST_ID/feedback/comment

Creates a comment on a post

### Body

```json
{
	"postID": "POST_ID",
	"body": "Comment body"
}
```

### Response

```json
{
	"data": {
		"id": "POST_ID-RANDOM_ID",
		"postID": "POST_ID",
		"authorID": "ACCOUNT_ID",
		"body": "Comment body",
		"mentions": [
			<List of mention structures>
		],
		"date": 1580071916,
		"accounts": {
			"ACCOUNT_ID": <Account structure>
		}
	},
	"success": 1
}
```