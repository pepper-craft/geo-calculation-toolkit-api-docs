## Perpendicular foot of a coordinate on a line

This is an HTTP API that returns the foot of the perpendicular dropped from a given coordinate onto a line defined by two geographic points.

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

![perpendicular-foot-of-a-coordinate-on-a-line](./img/perpendicular-foot-of-a-coordinate-on-a-line.png)

This image shows how the API calculates the perpendicular foot of a coordinate on a line defined by two geographic points.
The segment labeled C represents the input line.
Points A and B are input coordinates, and the API computes the point on the line where a perpendicular from each input coordinate would intersect.
These intersection points—known as the perpendicular feet—are marked as D and E.
Note that the input line is treated as extending infinitely in both directions, even beyond its endpoints, to allow for perpendicular projection from any input coordinate.

The API returns the geographic coordinate of the perpendicular foot from the given point.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/coordinate/perpendicular-foot
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

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                             |
|:---------------------:|:------:|------------------------------------------------------|:---------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/coordinate/perpendicular-foot` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Request Body**

| Field        | Type   | Required | Description                                                                       |
|--------------|--------|----------|-----------------------------------------------------------------------------------|
| `coordinate` | object | ✅ Yes    | The input coordinate used to calculate its perpendicular projection onto the line |
| └ `lat`      | number | ✅ Yes    | Latitude of the input point                                                       |
| └ `lng`      | number | ✅ Yes    | Longitude of the input point                                                      |
| `line`       | array  | ✅ Yes    | Line segment represented by two coordinates                                       |
| └ `lat`      | number | ✅ Yes    | Latitude of the starting point                                                    |
| └ `lng`      | number | ✅ Yes    | Longitude of the starting point                                                   |                                                  |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "coordinate": {
      "lat": 37.618453,
      "lng": 126.920180
    }
  }
}
```

### 3.2. Response Specifications

| Field          | Type    | Nullable | Description                                                              |
|----------------|---------|----------|--------------------------------------------------------------------------|
| `success`      | boolean | ❌ No     | Indicates whether the operation succeeded                                |
| `data`         | object  | ❌ No     | Included only when `success` is `true`                                   |
| └ `coordinate` | object  | ❌ No     | The geographic coordinate of the perpendicular foot on the extended line |
| └─ `lat`       | number  | ❌ No     | Latitude of the perpendicular foot                                       |
| └─ `lng`       | number  | ❌ No     | Longitude of the perpendicular foot                                      |

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