## Coordinate containment in a polygonal area

This is an HTTP API that determines whether a given coordinate is contained within a polygonal area.

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

![coordinate-containment-in-a-polygonal-area](./img/coordinate-containment-in-a-polygonal-area.png)

This image illustrates how the API checks whether a point lies inside or outside a polygon.

- A polygonal area is enclosed by a set of connected coordinates
- Input coordinates (e.g., A, B) are tested for containment within the polygon
- The label C visually indicates the entire polygon area
- The API classifies each point as either inside or outside the polygon

The API returns a boolean result indicating whether the given coordinate lies inside the polygonal area.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{BASE-URL}}/containment/polygon/coordinate
Content-Type: application/json

{
  "coordinate": {
    "lat": 37.618492,
    "lng": 126.920078
  },
  "polygon": [
    { "lat": 37.618385, "lng": 126.920021 },
    { "lat": 37.618500, "lng": 126.920150 },
    { "lat": 37.618600, "lng": 126.920300 },
    { "lat": 37.618450, "lng": 126.920400 },
    { "lat": 37.618320, "lng": 126.920250 },
    { "lat": 37.618385, "lng": 126.920021 } 
  ]
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | BASE-URL(HTTP Protocol + Host)                       | Path                              |
|:---------------------:|:------:|------------------------------------------------------|:----------------------------------|
|       Rapid API       |  POST  | `https://geo-calculation-toolkit-api.p.rapidapi.com` | `/containment/polygon/coordinate` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Request Body**

| Field        | Type   | Required | Description                                        |
|--------------|--------|----------|----------------------------------------------------|
| `coordinate` | object | ✅ Yes    | The point to check for containment                 |
| └ `lat`      | number | ✅ Yes    | Latitude of the coordinate                         |
| └ `lng`      | number | ✅ Yes    | Longitude of the coordinate                        |
| `polygon`    | array  | ✅ Yes    | An ordered list of coordinates forming the polygon |
| └ `lat`      | number | ✅ Yes    | Latitude of a vertex                               |
| └ `lng`      | number | ✅ Yes    | Longitude of a vertex                              |

> If the polygon is not closed, the API will automatically add a final segment connecting the last point to the first.

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "contained": true
  }
}
```

### 3.2. Response Specifications

| Field         | Type    | Nullable | Description                                       |
|---------------|---------|----------|---------------------------------------------------|
| `success`     | boolean | ❌ No     | Indicates whether the operation succeeded         |
| `data`        | object  | ❌ No     | Included only when `success` is `true`            |
| └ `contained` | boolean | ❌ No     | Whether the coordinate is inside the polygon area |

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


- [💬 Contact Support](mailto:peppercraft40@gmail.com)  
  If you have any questions or need help with the API, feel free to email us. We’ll get back to you as soon as possible.

---

[Go to API List](../README)