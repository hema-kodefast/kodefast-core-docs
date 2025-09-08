# KV Service Integration Documentation

## Overview

The KV (Key-Value) Service provides a fast, efficient way to store and retrieve data using simple key-value pairs. This documentation covers how to integrate and use the KV service in your API applications.

## Table of Contents

- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
- [Authentication](#authentication)
- [Integration Examples](#integration-examples)
- [Error Handling](#error-handling)
- [Best Practices](#best-practices)
- [Icon Processing Workflow](#icon-processing-workflow)

## Getting Started

### Base URL

```
https://kv.kodefast.net
```

### Prerequisites

- Valid API key/token for authentication
- HTTP client (fetch, axios, etc.)
- Understanding of REST API principles

## API Endpoints

### 1. Store Key-Value Pair

**POST** `/api/kv/set`

Store a key-value pair in the KV store.

**Request Body:**

```json
{
  "key": "user:123:profile",
  "value": {
    "name": "John Doe",
    "email": "john@example.com",
    "preferences": {
      "theme": "dark",
      "language": "en"
    }
  },
  "ttl": 3600
}
```

**Parameters:**

- `key` (string, required): Unique identifier for the data
- `value` (any, required): Data to store (can be string, number, object, array)
- `ttl` (number, optional): Time to live in seconds

**Response:**

```json
{
  "success": true,
  "message": "Key-value pair stored successfully",
  "key": "user:123:profile"
}
```

### 2. Retrieve Value by Key

**GET** `/api/kv/get/:key`

Retrieve a value by its key.

**Parameters:**

- `key` (string, required): The key to retrieve

**Response:**

```json
{
  "success": true,
  "key": "user:123:profile",
  "value": {
    "name": "John Doe",
    "email": "john@example.com",
    "preferences": {
      "theme": "dark",
      "language": "en"
    }
  },
  "createdAt": "2024-01-15T10:30:00Z",
  "expiresAt": "2024-01-15T11:30:00Z"
}
```

### 3. Delete Key

**DELETE** `/api/kv/delete/:key`

Delete a key-value pair from the store.

**Parameters:**

- `key` (string, required): The key to delete

**Response:**

```json
{
  "success": true,
  "message": "Key deleted successfully",
  "key": "user:123:profile"
}
```
