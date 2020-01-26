# Other

### Docs on other misc endpoints

# Endpoints

## [POST] /client/event

Updates the server on user-made events. Probably to detect bots or API abuse

### Body

```json5
{
	"eventType": "appOpen",
	"eventData": {
		"os": "ios"
	}
}