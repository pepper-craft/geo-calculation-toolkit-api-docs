## Destination coordinate after moving a certain distance toward another coordinate

This is an HTTP API that calculates the coordinate reached after moving a certain distance from one point toward another point.

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

![destination-coordinate-after-moving-a-certain-distance-toward-another-coordinate](./img/destination-coordinate-after-moving-a-certain-distance-toward-another-coordinate.png)

This image illustrates how the API determines a new coordinate by moving a specific distance in the direction of another coordinate.

- A starting coordinate (point A) serves as the origin
- A target coordinate (point B) defines the direction
- A fixed distance is applied along the straight path between A and B
- The resulting coordinate (point C) lies on the line from A to B at the given distance

The API returns the coordinate (point C) that results from moving the specified distance from the starting point toward the destination point.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/coordinate/move-toward-coordinate
Content-Type: application/json

{
  "fromCoordinate": {
    "lat": 37.618492,
    "lng": 126.920078
  },
  "toCoordinate": {
    "lat": 37.629410,
    "lng": 126.933330
  },
  "distance": 2.5,
  "distanceUnit": "m"
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                                 |
|:---------------------:|:------:|------------------------------------------------------|:-------------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/coordinate/move-toward-coordinate` |

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
| `toCoordinate`   | object | ✅ Yes      | The coordinate indicating the direction of movement                             |
| └ `lat`          | number | ✅ Yes      | Latitude of the target coordinate                                               |
| └ `lng`          | number | ✅ Yes      | Longitude of the target coordinate                                              |
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
      "lat": 37.6185082,
      "lng": 126.9200977
    }
  }
}
```

### 3.2. Response Specifications

| Field          | Type    | Nullable | Description                                                  |
|----------------|---------|----------|--------------------------------------------------------------|
| `success`      | boolean | ❌ No     | Indicates whether the operation succeeded                    |
| `data`         | object  | ❌ No     | Included only when `success` is `true`                       |
| └ `coordinate` | object  | ❌ No     | The resulting coordinate after moving the specified distance |
| └─ `lat`       | number  | ❌ No     | Latitude of the resulting coordinate                         |
| └─ `lng`       | number  | ❌ No     | Longitude of the resulting coordinate                        |

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


- [🐞 Open a GitHub Issue](https://github.com/pepper-craft/geo-calculation-toolkit-api-docs/issues)  
  Use this for technical support, API usage questions, feature requests, or bug reports.  
  We respond publicly so others can benefit from the same information.


- [📬 Email Us](mailto:peppercraft40@gmail.com)  
  For private or sensitive inquiries that should not be shared publicly.

---

[Go to API List](../README)