## 💥 Error Codes

| HTTP Status | Error Code                        | Message                                               | Description                                                                         |
|-------------|-----------------------------------|-------------------------------------------------------|-------------------------------------------------------------------------------------|
| 400         | `REQUIRED_PARAMETER_MISSING`      | Required parameter is missing.                        | A required parameter was not provided in the request payload or query string.       |
| 400         | `INVALID_FORMAT`                  | Invalid format.                                       | One or more values in the request do not match the expected data type or structure. |
| 400         | `LATITUDE_OUT_OF_RANGE`           | Latitude (lat) must be between -90 and 90 degrees.    | The specified latitude is outside the valid geographic range.                       |
| 400         | `LONGITUDE_OUT_OF_RANGE`          | Longitude (lng) must be between -180 and 180 degrees. | The specified longitude is outside the valid geographic range.                      |
| 400         | `GEO_LINE_MINIMUM_COORDINATES`    | Geo Line must have at least 2 coordinates.            | A polyline must consist of at least two coordinate points to form a valid line.     |
| 400         | `GEO_POLYGON_MINIMUM_COORDINATES` | Geo Polygon must have at least 3 coordinates.         | A polygon must include at least three coordinate points to form a closed shape.     |