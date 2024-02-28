Certainly! Below is the documentation for the API to get all chats with pagination, including the last message for each chat, and the API to get all messages for a single chat with pagination:

---

## Get All Chats with Pagination API

### Endpoint:

- **Method**: GET
- **URL**: `/api/chats?page=<page_number>&limit=<limit_per_page>`

### Query Parameters:

| Parameter       | Type     | Description                                    |
|-----------------|----------|------------------------------------------------|
| `page`          | integer  | Page number for pagination.                    |
| `limit`         | integer  | Number of chats to fetch per page.             |

### Response Payload:

| Field          | Type     | Description                                    |
|----------------|----------|------------------------------------------------|
| `success`      | boolean  | Indicates whether the request was successful.  |
| `chats`        | array    | Array of chat objects.                         |

#### Chat Object:

| Field          | Type     | Description                                    |
|----------------|----------|------------------------------------------------|
| `id`           | integer  | Unique identifier of the chat.                 |
| `last_message` | object   | Object representing the last message in the chat.|
| `participants` | array    | Array of user objects participating in the chat.|

##### Last Message Object:

| Field          | Type     | Description                                    |
|----------------|----------|------------------------------------------------|
| `id`           | integer  | Unique identifier of the last message.         |
| `sender_id`    | integer  | Identifier of the user who sent the last message. |
| `message`      | string   | Content of the last message.                   |
| `timestamp`    | DateTime | Timestamp indicating when the last message was sent. |

```json
{
  "success": true,
  "chats": [
    {
      "id": 1,
      "last_message": {
        "id": 123,
        "sender_id": 456,
        "message": "Hello!",
        "timestamp": "2024-02-27T12:05:00Z"
      },
      "participants": [
        {
          "id": 456,
          "name": "User A"
        },
        {
          "id": 789,
          "name": "User B"
        }
      ]
    },
    {
      "id": 2,
      "last_message": {
        "id": 456,
        "sender_id": 789,
        "message": "Hi there!",
        "timestamp": "2024-02-27T12:10:00Z"
      },
      "participants": [
        {
          "id": 123,
          "name": "User C"
        },
        {
          "id": 789,
          "name": "User B"
        }
      ]
    }
  ]
}
```

---

## Get All Messages for a Single Chat with Pagination API

### Endpoint:

- **Method**: GET
- **URL**: `/api/chat/<chat_id>/messages?page=<page_number>&limit=<limit_per_page>`

### Path Parameters:

| Parameter       | Type     | Description                                    |
|-----------------|----------|------------------------------------------------|
| `chat_id`       | integer  | Identifier of the chat for which messages are fetched. |

### Query Parameters:

| Parameter       | Type     | Description                                    |
|-----------------|----------|------------------------------------------------|
| `page`          | integer  | Page number for pagination.                    |
| `limit`         | integer  | Number of messages to fetch per page.          |

### Response Payload:

| Field          | Type     | Description                                    |
|----------------|----------|------------------------------------------------|
| `success`      | boolean  | Indicates whether the request was successful.  |
| `messages`     | array    | Array of message objects.                      |

#### Message Object:

| Field          | Type     | Description                                    |
|----------------|----------|------------------------------------------------|
| `id`           | integer  | Unique identifier of the message.              |
| `sender_id`    | integer  | Identifier of the user who sent the message.   |
| `message`      | string   | Content of the message.                        |
| `timestamp`    | DateTime | Timestamp indicating when the message was sent.|

```json
{
  "success": true,
  "messages": [
    {
      "id": 1,
      "sender_id": 123,
      "message": "Hello!",
      "timestamp": "2024-02-27T12:05:00Z"
    },
    {
      "id": 2,
      "sender_id": 456,
      "message": "Hi there!",
      "timestamp": "2024-02-27T12:10:00Z"
    }
  ]
}
```

---

These APIs allow fetching all chats with pagination, including the last message for each chat, as well as fetching all messages for a single chat with pagination. They provide structured documentation for developers to understand the endpoints, request parameters, response structure, and example responses.
