# iOS Recruitment Test

The task is to create an app that includes two separate screens: **Currency Converter** and **Online Quotes**.

### **Navigation Requirements**
- The app should use a **TabBar-based navigation** with two tabs:
  1. **Currency Converter**
  2. **Online Quotes**
- The **TabBar** should provide a clear visual indication of the currently selected screen.
- Users should be able to easily switch between the two sections.

---

## **Currency Converter**
The **Currency Converter screen** should provide a simple and efficient way to convert currencies. Users should be able to:
- Select a **primary currency** and input an amount.
- Choose a **secondary currency** from a dropdown menu.
- See the **converted value** dynamically.

#### **API Endpoints**
##### **Get Currency List**
**Request:**
```http
GET https://valyuta.com/api/get_currency_list_for_app
```
**Response Example:**
```json
[
    {
        "code": "AED",
        "az": "BƏƏ dirhəmi",
        "en": "UAE Dirham",
        "tr": "BAE Dirhemi",
        "ru": "Дирхам ОАЭ"
    },
    {
        "code": "TRY",
        "az": "Türk lirəsi",
        "en": "Turkish Lira",
        "tr": "Türk Lirası",
        "ru": "Турецкая лира"
    }
]
```

##### **Get Currency Rates**
**Request:**
```http
GET https://valyuta.com/api/get_currency_rate_for_app/{CURRENCY}/{DATE}
```
- `{CURRENCY}` – The base currency code (e.g., `"USD"`, `"EUR"`, `"GBP"`).
- `{DATE}` – The date in `YYYY-MM-DD` format (e.g., `"2025-02-18"`).

**Response Example:**
```json
[
    {
        "from": "AED",
        "to": "EUR",
        "result": 0.2603217,
        "date": "2025-02-18",
        "menbe": "cbar"
    },
    {
        "from": "AUD",
        "to": "EUR",
        "result": 0.607984,
        "date": "2025-02-18",
        "menbe": "afor"
    }
]
```

---

## **Online Quotes**
The **Online Quotes screen** should display real-time financial data received via WebSocket from the **InvestAZ** platform.

#### **WebSocket Connection**
**WebSocket URL:**
  ```
  wss://investaz.az/quotes
  ```

**Response Example:**
```json
[
    {
        "0": "down", 
        "1": "USDDKK", 
        "2": "7.12933", 
        "3": "7.13342", 
        "4": "7.11132", 
        "5": "7.13435", 
        "6": "409", 
        "7": "2025-02-18T09:53:11"
    },
    {
        "0": "up", 
        "1": "XAUEUR", 
        "2": "2784.06", 
        "3": "2784.61", 
        "4": "2763.19", 
        "5": "2788.79", 
        "6": "55", 
        "7": "2025-02-18T09:53:11"
    }
]
```

#### **Field Mapping:**
| Index | Field Name      | Description                        |
|-------|---------------|------------------------------------|
| `0`   | `trend`       | Price movement (`up`/`down`) |
| `1`   | `symbol`      | Asset or currency pair (e.g., `"USDDKK"`) |
| `2`   | `bid_price`   | Bid price |
| `3`   | `ask_price`   | Ask price |
| `4`   | `low_price`   | Lowest price of the day |
| `5`   | `high_price`  | Highest price of the day |
| `6`   | `spread`      | Difference between bid and ask price |
| `7`   | `lasttime`    | Last update time (ISO 8601) |

Online quotes screen should show the quotes and indicators that are received from InvestAZ site via WebSocket. Connect to WebSocket at `wss://investaz.az/quotes` using the standard WebSocket API.

### **Requirements**
- Display real-time quotes in a **table format**.
- Allow users to **hide/show specific quotes**.
- Provide a **visual indicator** for WebSocket connection status.

### **Optional Features**
- **Cache WebSocket data**, ensuring users see the latest quotes even if disconnected.
- Implement a **reconnection strategy** if WebSocket connection drops.

---

## **Submission**
1. **Push your completed project** to a GitHub repository.
2. **Send the repository link** to `hr@investaz.az`.
3. **Attach your resume** with your submission.
4. **Wait for our feedback.**

Good luck! 🎉
