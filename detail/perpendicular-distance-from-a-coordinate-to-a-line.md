## Perpendicular distance from a coordinate to a line

This is an HTTP API that calculates the perpendicular surface distance from a given coordinate to a straight line extended through two geographic points.

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

![perpendicular-distance-from-a-coordinate-to-a-line](./img/perpendicular-distance-from-a-coordinate-to-a-line.png)

This image provides a visual explanation of how the API calculates the perpendicular surface distance from a coordinate to a line extended through two geographic points.
Here, point A and point B are specific geographic locations defined by latitude and longitude. The line C represents a straight line segment defined by two coordinates, which may be extended beyond its endpoints.

- For point A, the perpendicular distance is calculated to point D, which lies on the extension of the input line.
- For point B, the perpendicular intersects the line directly at point E, which lies on the original segment.

This API takes a single coordinate and a line defined by two coordinates as input, and returns the shortest perpendicular surface distance from the point to the infinite line that passes through the given two points.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/distance/from-point-to-line/perpendicular?unit=m
Content-Type: application/json

{
  "coordinate": {
    "lat": 37.618630,
    "lng": 126.920004
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

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                                         |
|:---------------------:|:------:|------------------------------------------------------|:---------------------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/distance/from-point-to-line/perpendicular` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Query Parameters**

| Parameter | Type   | Required   | Description                                                                                |
|-----------|--------|------------|--------------------------------------------------------------------------------------------|
| `unit`    | string | ❌ Optional | Unit for the response value (`mm`, `cm`, `m`, `km`, `in`, `ft`, `yd`, `mi`). Default: `m`. |

**2.2.4. Request Body**

| Field        | Type   | Required | Description                                                   |
|--------------|--------|----------|---------------------------------------------------------------|
| `coordinate` | object | ✅ Yes    | The point from which the shortest distance will be calculated |
| └ `lat`      | number | ✅ Yes    | Latitude of the input point                                   |
| └ `lng`      | number | ✅ Yes    | Longitude of the input point                                  |
| `line`       | array  | ✅ Yes    | Line segment represented by two coordinates                   |
| └ `lat`      | number | ✅ Yes    | Latitude of the starting point                                |
| └ `lng`      | number | ✅ Yes    | Longitude of the starting point                               |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "distance": 10.6699,
    "unit": "m"
  }
}
```

### 3.2. Response Specifications

| Field       | Type    | Nullable | Description                                                                                         |
|-------------|---------|----------|-----------------------------------------------------------------------------------------------------|
| `success`   | boolean | ❌ No     | Indicates whether the operation succeeded                                                           |
| `data`      | object  | ❌ No     | Included only when `success` is `true`                                                              |
| └`distance` | number  | ❌ No     | Shortest perpendicular surface distance from the input coordinate to the line (4 decimal precision) |
| └`unit`     | string  | ❌ No     | Unit of measurement (`mm`, `m`, `km`, `ft`, `yd`, `mi`)                                             |

---

## 💥 4. Error Response Details

### 4.1. Error Response Example

```http request
400 Bad Request
Content-Type: application/json

{
  "success": false,
  "code": "REQUIRED_PARAMETER_MISSING",
  "message": "Required parameter is missing.",
  "detailMessage": "Required parameter is missing. (fromCoordinate)"
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