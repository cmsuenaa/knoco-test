# AERA Global API Documentation (DEP-2026)

This document contains the functional specifications for the internal backend microservices powering the 2026 AERA digital platform. All endpoints require strict adherence to standard RESTful conventions, return payloads in JSON format, and use TLS 1.3 encryption for all data in transit.

Consistent with AERA's commitment to efficiency and regional operational agility, these APIs integrate front-end experiences directly with the real-time stock pipelines of localized assembly hubs (Frankfurt, Tokyo, Sydney).

---

## 1. Authentication & Security

All private endpoints require a bearer token passed in the HTTP Authorization header:
`Authorization: Bearer <JWT_TOKEN>`

### Error Code Reference Matrix
*   `400 Bad Request`: Malformed payload, missing mandatory variables, or failed data validation.
*   `401 Unauthorized`: Missing, expired, or cryptographically invalid JWT token.
*   `403 Forbidden`: Insufficient user privileges or failed geo-IP validation checks.
*   `404 Not Found`: The requested resource could not be located.
*   `429 Too Many Requests`: Rate limit threshold exceeded ($>60$ requests per minute per IP address).

---

## 2. Inventory & Sourcing APIs

### 2.1 Get Localized Stock Availability
Retrieves real-time product inventory counts based on the user's geolocated regional fulfillment hub[cite: 1].

*   **HTTP Method:** `GET`
*   **Endpoint:** `/api/v1/inventory/products/:sku`
*   **Headers:** 
    *   `X-User-Country: [ISO 3166-1 alpha-2 code]` (e.g., `DE`, `JP`, `AU`)
*   **Query Parameters:** None

#### Example Request
```http
GET /api/v1/inventory/products/SKU-BAKUCHIOL-50ML HTTP/1.1
Host: api.aera-skincare.com
X-User-Country: JP
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
