## Closest point on a line from a coordinate

This is an HTTP API that finds the closest point on a given line segment from an input coordinate.

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

![closest-point-on-a-line-from-a-coordinate](./img/closest-point-on-a-line-from-a-coordinate.png)

This image illustrates how the API calculates the closest point on a single line segment from a given coordinate.

- Coordinates (e.g., points A, B) are input locations
- A single line segment (labeled C) connects two endpoints
- The API identifies the point on the segment that is closest to the input coordinate
- That closest point (e.g., D or E) is marked on the segment

The API returns the geographic coordinate (such as point D or E) that lies on the line segment (C) and is closest to the input coordinate.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/coordinate/closest-on-line
Content-Type: application/json

{
  "coordinate": {
    "lat": 37.618492,
    "lng": 126.920078
  },
  "line": [
    {
      "lat": 37.618515,
      "lng": 126.920021
    },
    {
      "lat": 37.618385,
      "lng": 126.920339
    }
  ]
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                          |
|:---------------------:|:------:|------------------------------------------------------|:------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/coordinate/closest-on-line` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Request Body**

| Field        | Type   | Required | Description                                                |
|--------------|--------|----------|------------------------------------------------------------|
| `coordinate` | object | ✅ Yes    | The input point from which the closest point is calculated |
| └ `lat`      | number | ✅ Yes    | Latitude of the input coordinate                           |
| └ `lng`      | number | ✅ Yes    | Longitude of the input coordinate                          |
| `line`       | array  | ✅ Yes    | A single line segment defined by exactly two coordinates   |
| └ `lat`      | number | ✅ Yes    | Latitude of an endpoint of the line segment                |
| └ `lng`      | number | ✅ Yes    | Longitude of an endpoint of the line segment               |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "coordinate": {
      "lat": 37.6184918,
      "lng": 126.9200778
    }
  }
}
```

### 3.2. Response Specifications

| Field          | Type    | Nullable | Description                                                           |
|----------------|---------|----------|-----------------------------------------------------------------------|
| `success`      | boolean | ❌ No     | Indicates whether the operation succeeded                             |
| `data`         | object  | ❌ No     | Included only when `success` is `true`                                |
| └ `coordinate` | object  | ❌ No     | The point on the line segment that is closest to the input coordinate |
| └─ `lat`       | number  | ❌ No     | Latitude of the closest point on the line segment                     |
| └─ `lng`       | number  | ❌ No     | Longitude of the closest point on the line segment                    |

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

- [🚀 Try the API on RapidAPI Console](https://rapidapi.com/pepper-craft1-pepper-craft-default/api/geo-calculation-toolkit-api)  
  Run live requests, view sample code, pricing, and manage your API key—all in one place.

---

[Go to API List](../README)