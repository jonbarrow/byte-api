# Account

### Docs on Byte accounts and the account API

## Account structure

```json
{
	"id": "ACCOUNT_ID",
	"isChannel": Bool,
	"registrationDate": 0000000000,
	"displayName": "Display Name",
	"username": "Username",
	"avatarURL": "https://link.to.user/avatar.jpg",
	"bio": "Users Bio",
	"backgroundColor": "#00FF71",
	"foregroundColor": "#203154",
	"followerCount": 0,
	"followingCount": 0,
	"loopCount": 0,
	"loopsConsumedCount": 0,
	"isFollowing": Bool,
	"isFollowed": Bool,
	"isBlocked": Bool
}
```

# Endpoints

## [GET] /account/prefix/{username}

Runs a username search

### Response

```json
{
	"data": {
		"accounts": [
			<List of account structures>
		]
	},
	"success": 1
}
```


## [GET] /account/me

Gets account information for currently logged in user

### Response

```json
{
	"data": <Account structure>,
	"success": 1
}
```


## [PUT] /account/me

Updates account information for currently logged in user (does not handle profile pictures, see upload API)

### Body

```json
{
	"displayName": "Display Name",
	"colorScheme": 0,
	"bio": "Bio",
	"avatarUploadID": "XXXXXXXXXXXXXXXXXXXXXXXXXX",
	"username": "username"
}
```


## [GET] /account/me/posts

Gets users posts

### Body

```json
{
	{
	"data": {
		"posts": [
			<List of post structures>
		],
		"accounts": {
			"ACCOUNT_ID": {
				<Account structure>
			},
			"ACCOUNT_ID": {
				<Account structure>
			}
			...
		}
	},
	"success": 1
}
}
```



## [GET] /account/me/colors

Returns a list of colors

### Response

```json
{
	"data": {
		"colors": [
			{
				"id": 1,
				"foreground": "#E2E9FF",
				"background": "#E2E9FF"
			},
			...
		]
	},
	"success": 1
}
```


## [GET] /account/me/following

Gets list of accounts the current user is following

### Response

```json
{
	"data": {
		"accounts": [
			<List of account structures>
		]
	},
	"success": 1
}
```


## [GET] /account/me/followers

Gets list of accounts following the current user

### Response

```json
{
	"data": {
		"accounts": [
			<List of account structures>
		]
	},
	"success": 1
}
```


## [GET] /account/me/blocking

Gets list of accounts blocked by the current user

### Response

```json
{
	"data": {
		"accounts": [
			<List of account structures>
		]
	},
	"success": 1
}
```


## [PUT] /account/id/ACCOUNT_ID/block

Blocks the given user


## [DELETE] /account/id/ACCOUNT_ID/block

Unblocks the given user


## [PUT] /account/me/device

Updates the current device information?

## Body

```json
{
	"deviceToken": "token",
	"deviceType": "type",
	"applicationID": "co.byte.video",
}
```


## [GET] /account/me/feedback/like

Gets users likes

### Body

```json
{
	{
	"data": {
		"posts": [
			<List of post structures>
		],
		"accounts": {
			"ACCOUNT_ID": {
				<Account structure>
			},
			"ACCOUNT_ID": {
				<Account structure>
			}
			...
		}
	},
	"success": 1
}
}
```



## [GET] /account/id/ACCOUNT_ID

Returns account information by ID

### Response

Same format as `/account/me`


## [GET] /account/id/ACCOUNT_ID/following

Gets list of accounts the given user is following

### Response

Same format as `/account/me/following`


## [GET] /account/id/ACCOUNT_ID/followers

Gets list of accounts following the given user

### Response

Same format as `/account/me/followers`


## [GET] /account/id/ACCOUNT_ID/posts

Returns account posts

### Response

Same format as `/account/me/posts`