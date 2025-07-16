## Destination coordinate after moving a certain distance in a given bearing

This is an HTTP API that calculates the destination coordinate after moving a certain distance from a starting point in a specified bearing.

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

![destination-coordinate-after-moving-a-certain-distance-in-a-given-bearing](./img/destination-coordinate-after-moving-a-certain-distance-in-a-given-bearing.png)

This image illustrates how the API computes a new coordinate by moving a set distance from a point in a given directional bearing.

- A starting coordinate (point A) defines the origin
- A bearing (angle from true north) specifies the movement direction
- A distance value indicates how far to move from the origin
- The resulting destination (point C) lies along the specified bearing and distance

The API returns the coordinate (point C) obtained by moving from the starting point in the provided bearing by the given distance.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/coordinate/move-in-bearing
Content-Type: application/json

{
  "fromCoordinate": {
    "lat": 37.618492,
    "lng": 126.920078
  },
  "bearing": 45,
  "distance": 200,
  "distanceUnit": "m"
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

| Field            | Type   | Required   | Description                                                                     |
|------------------|--------|------------|---------------------------------------------------------------------------------|
| `fromCoordinate` | object | ✅ Yes      | The starting coordinate                                                         |
| └ `lat`          | number | ✅ Yes      | Latitude of the starting coordinate                                             |
| └ `lng`          | number | ✅ Yes      | Longitude of the starting coordinate                                            |
| `bearing`        | number | ✅ Yes      | Direction of movement in degrees (0° = true north, clockwise)                   |
| `distance`       | number | ✅ Yes      | Distance to move from the starting point                                        |
| `distanceUnit`   | string | ❌ Optional | Unit of distance (`mm`, `cm`, `m`, `km`, `in`, `ft`, `yd`, `mi`) (default: `m`) |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "coordinate": {
      "lat": 37.6194374,
      "lng": 126.9220114
    }
  }
}
```

### 3.2. Response Specifications

| Field          | Type    | Nullable | Description                               |
|----------------|---------|----------|-------------------------------------------|
| `success`      | boolean | ❌ No     | Indicates whether the operation succeeded |
| `data`         | object  | ❌ No     | Included only when `success` is `true`    |
| └ `coordinate` | object  | ❌ No     | The resulting coordinate after movement   |
| └─ `lat`       | number  | ❌ No     | Latitude of the destination coordinate    |
| └─ `lng`       | number  | ❌ No     | Longitude of the destination coordinate   |

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


- [📬 Email Us](mailto:peppercraft40@gmail.com)  
  For private or sensitive inquiries that should not be shared publicly.

---

[Go to API List](../README)