## Total length of a polyline

This is an HTTP API that calculates the total geographic length of a given polyline.

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

![total-length-of-a-polyline](./img/total-length-of-a-polyline.png)

This image illustrates how the API computes the total length of a polyline by summing the distances between consecutive points.

- A polyline is formed by multiple coordinates connected in sequence
- Each segment's length (e.g., distance 1, 2, 3) is measured individually
- The total length is the sum of all segment lengths

The API returns the total length of the polyline in the specified unit.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/length/polyline?unit=m
Content-Type: application/json

{
  "polyline": [
    { "lat": 37.618492, "lng": 126.920078 },
    { "lat": 37.618385, "lng": 126.920339 },
    { "lat": 37.618210, "lng": 126.920580 },
    { "lat": 37.618050, "lng": 126.920830 }
  ]
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path               |
|:---------------------:|:------:|------------------------------------------------------|:-------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/length/polyline` |

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

| Field      | Type   | Required | Description                                         |
|------------|--------|----------|-----------------------------------------------------|
| `polyline` | array  | ✅ Yes    | An ordered list of coordinates forming the polyline |
| └ `lat`    | number | ✅ Yes    | Latitude of a point in the polyline                 |
| └ `lng`    | number | ✅ Yes    | Longitude of a point in the polyline                |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "length": 142.9837,
    "unit": "m"
  }
}
```

### 3.2. Response Specifications

| Field      | Type    | Nullable | Description                                                                 |
|------------|---------|----------|-----------------------------------------------------------------------------|
| `success`  | boolean | ❌ No     | Indicates whether the operation succeeded                                   |
| `data`     | object  | ❌ No     | Included only when `success` is `true`                                      |
| └ `length` | number  | ❌ No     | Total length of the polyline                                                |
| └ `unit`   | string  | ❌ No     | Unit for the response value (`mm`, `cm`, `m`, `km`, `in`, `ft`, `yd`, `mi`) |

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