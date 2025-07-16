## Shortest distance from a coordinate to a line

This is an HTTP API that calculates the shortest distance from a coordinate to a line segment, considering only the finite bounds of the segment.


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

![shortest-distance-from-a-coordinate-to-a-line](./img/shortest-distance-from-a-coordinate-to-a-line.png)

This image illustrates how the shortest distance is determined from a coordinate to a limited line segment.

- Coordinates A and B are input points from which the distance is measured.
- Line segment C represents the defined reference line between two endpoints.
- Unlike perpendicular distance, the shortest distance may connect to either the perpendicular foot (if it falls within the segment) or to an endpoint (e.g., D or E) if the perpendicular foot lies outside the segment bounds.

The API returns the minimum distance between the input coordinate and the finite line segment, along with the unit of measurement.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/distance/from-point-to-line/shortest?unit=m
Content-Type: application/json

{
  "coordinate": {
    "lat": 37.618500,
    "lng": 126.920300
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

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                                    |
|:---------------------:|:------:|------------------------------------------------------|:----------------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/distance/from-point-to-line/shortest` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Query Parameters**

| Parameter | Type   | Required   | Description                                                                                 |
|-----------|--------|------------|---------------------------------------------------------------------------------------------|
| `unit`    | string | ❌ Optional | Unit for the response value (`mm`, `cm`, `m`, `km`, `in`, `ft`, `yd`, `mi`) (default: `m`). |

**2.2.4. Request Body**

| Field        | Type   | Required | Description                                              |
|--------------|--------|----------|----------------------------------------------------------|
| `coordinate` | object | ✅ Yes    | The point from which the shortest distance is calculated |
| └ `lat`      | number | ✅ Yes    | Latitude of the input coordinate                         |
| └ `lng`      | number | ✅ Yes    | Longitude of the input coordinate                        |
| `line`       | array  | ✅ Yes    | The finite line segment represented by two coordinates   |
| └ `lat`      | number | ✅ Yes    | Latitude of a point on the line                          |
| └ `lng`      | number | ✅ Yes    | Longitude of a point on the line                         |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "distance": 9.7817,
    "unit": "m"
  }
}
```

### 3.2. Response Specifications

| Field        | Type    | Nullable | Description                                                                 |
|--------------|---------|----------|-----------------------------------------------------------------------------|
| `success`    | boolean | ❌ No     | Indicates whether the operation succeeded                                   |
| `data`       | object  | ❌ No     | Included only when `success` is `true`                                      |
| └ `distance` | number  | ❌ No     | Shortest surface distance from the input coordinate to the line             |
| └ `unit`     | string  | ❌ No     | Unit for the response value (`mm`, `cm`, `m`, `km`, `in`, `ft`, `yd`, `mi`) |

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