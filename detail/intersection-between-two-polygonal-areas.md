## Intersection between two polygonal areas

This is an HTTP API that determines whether two polygonal areas intersect.

---

## 📚 Table of Contents

1. [🧭 Overview](#-1-overview) — *For first-time users*
2. [📤 Request Details](#-2-request-details) — *For developers integrating the API*
    1. [Request Example](#21-request-example)
    2. [Request Specifications](#22-request-specifications)
3. [📥 Response Details](#-3-response-details)
    1. [Response Example](#31-response-example)
    2. [Response Specifications](#32-response-specifications)
4. [💥 Error Response Details](#-4-error-response-details)
    1. [Error Response Example](#41-error-response-example)
    2. [Error Response Specifications](#42-error-response-specifications)
    3. [Error Codes](#43-error-codes)
5. [🔗 Reference Links](#-5-reference-links) — *For testing the API and retrieving your API key*

---

## 🧭 1. Overview

![intersection-between-two-polygonal-areas](./img/intersection-between-two-polygonal-areas.png)

This image illustrates how the API checks for spatial intersection between two polygonal areas.

- Two polygonal shapes are shown, each defined by a list of connected coordinates
- Labels A and B represent each polygonal area, not individual points
- The API determines if any part of polygon A overlaps with polygon B

The API returns a boolean result indicating whether the two polygonal areas intersect.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/intersection/polygon-pair
Content-Type: application/json

{
  "polygon1": [
    { "lat": 37.618000, "lng": 126.920000 },
    { "lat": 37.618000, "lng": 126.921000 },
    { "lat": 37.617000, "lng": 126.921000 },
    { "lat": 37.617000, "lng": 126.920000 }
  ],
  "polygon2": [
    { "lat": 37.617500, "lng": 126.920500 },
    { "lat": 37.617500, "lng": 126.921500 },
    { "lat": 37.616500, "lng": 126.921500 },
    { "lat": 37.616500, "lng": 126.920500 }
  ]
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                         |
|:---------------------:|:------:|------------------------------------------------------|:-----------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/intersection/polygon-pair` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Request Body**

| Field      | Type   | Required | Description                                            |
|------------|--------|----------|--------------------------------------------------------|
| `polygon1` | array  | ✅ Yes    | List of coordinates defining the first polygonal area  |
| └ `lat`    | number | ✅ Yes    | Latitude of a vertex                                   |
| └ `lng`    | number | ✅ Yes    | Longitude of a vertex                                  |
| `polygon2` | array  | ✅ Yes    | List of coordinates defining the second polygonal area |
| └ `lat`    | number | ✅ Yes    | Latitude of a vertex                                   |
| └ `lng`    | number | ✅ Yes    | Longitude of a vertex                                  |

> If the polygon is not closed, the API will automatically add a final segment connecting the last point to the first.

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "intersected": true
  }
}
```

### 3.2. Response Specifications

| Field           | Type    | Nullable | Description                               |
|-----------------|---------|----------|-------------------------------------------|
| `success`       | boolean | ❌ No     | Indicates whether the operation succeeded |
| `data`          | object  | ❌ No     | Included only when `success` is `true`    |
| └ `intersected` | boolean | ❌ No     | Whether the two polygonal areas intersect |

---

## 💥 4. Error Response Details

### 4.1. Error Response Example

```http request
500 Internal Server Error
Content-Type: application/json

{
  "success": false,
  "code": "INTERNAL_SERVER_ERROR",
  "message": "Internal server error occurred.",
  "detailMessage": "Please try again later. (An error occurred in the internal calculation logic.)"
}
```

### 4.2. Error Response Specifications

**4.2.1. Error Response Headers**

| Header Name    | Example Value      | Description                    |
|----------------|--------------------|--------------------------------|
| `Content-Type` | `application/json` | MIME type of the response body |

**4.2.2. Error Response Body**

| Field           | Type    | Nullable | Description                                                                      |
|-----------------|---------|----------|----------------------------------------------------------------------------------|
| `success`       | boolean | ❌ No     | Indicates whether the operation was successful. Always `false` here.             |
| `code`          | string  | ❌ No     | Application-defined error code representing the type of failure.                 |
| `message`       | string  | ❌ No     | General explanation of the error.                                                |
| `detailMessage` | string  | ❌ No     | Additional information providing context about the error for debugging purposes. |

### 4.3. Error Codes

To view the full list of error codes, please visit the link below.

- [Error Codes](./common/error-codes.md)

---

## 🔗 5. Reference Links

- [🚀 Try the API on RapidAPI Console](https://rapidapi.com/your-api/test)  
  Run live requests, view sample code, pricing, and manage your API key—all in one place.


- [💬 Contact Support](mailto:support@yourapi.com)  
  If you have any questions or need help with the API, feel free to email us. We’ll get back to you as soon as possible.

---

[Go to API List](../README)