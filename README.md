# 🚌 Bus Availability API

This is a simple public API to **check available bus tickets** between two cities in Iran using data from [Alibaba.ir](https://www.alibaba.ir).

---

## 🔗 API Endpoint

```
GET https://alibabacrawler.sideco.ir
```

---

## 🧾 Query Parameters

| Parameter     | Required | Description                                 |
|---------------|----------|---------------------------------------------|
| `origin`      | ✅       | Origin city name in English (e.g. `tehran`) |
| `destination` | ✅       | Destination city name in English            |
| `date`        | ✅       | Travel date in format `YYYY-MM-DD`          |

> ⚠️ City names are case-insensitive.

---

## ✅ Example Request

```http
GET https://alibabacrawler.sideco.ir/?origin=tehran&destination=shiraz&date=2025-04-20
```

---

## 🔄 Example Response

```json
{
  "availableBuses": [
    {
      "busCompany": "Iran Peyma",
      "departureTime": "10:00",
      "arrivalTime": "18:00",
      "price": 250000,
      ...
    },
    ...
  ]
}
```

> The actual format depends on [Alibaba.ir](https://www.alibaba.ir)'s internal API response and may include fields such as `busCompany`, `price`, `departureTime`, `arrivalTime`, `busType`, etc.

---

## 🚫 Error Responses

| Status | Message                          | Cause                            |
|--------|----------------------------------|----------------------------------|
| 400    | `Missing origin, destination...` | One or more required parameters are missing |
| 400    | `Invalid origin or destination`  | City name not found              |
| 500    | `Internal error`                 | Upstream service is unreachable  |

---

## 📝 Notes

- The city name lookup is powered by **SnappTrip**'s public API.
- You must provide the **English version** of city names.
- Date must be in the **Gregorian format** `YYYY-MM-DD`.

---

## 💬 Support

For help or to report an issue, contact the developer or open a GitHub issue.
