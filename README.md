-----

# Daily Quotes API

This repository contains the source code for a simple Google Apps Script that serves a daily quote via a web-based API. This API is designed to be lightweight and easy to integrate into any web project, application, or script.

### API Endpoint

The core functionality of this project is a simple `GET` request to the following API endpoint.

```
https://script.google.com/macros/s/AKfycbyU2tuTOsLmynjo7oKCUwT4UAXrvfWZSHgnLDqrtK_e1aY_1HyL2LeyBqn5VscEHL-kVg/exec?action=getQuote
```

The API returns a JSON object with the following structure:

```json
{
  "quote": "The only way to do great work is to love what you do.",
  "author": "Steve Jobs",
  "date": "2023-10-27"
}
```

-----

### Code Examples

Here are some examples of how you can use this API in your own projects.

#### JavaScript

```javascript
const getDailyQuote = async () => {
  try {
    const res = await fetch(
      'https://script.google.com/macros/s/AKfycbyU2tuTOsLmynjo7oKCUwT4UAXrvfWZSHgnLDqrtK_e1aY_1HyL2LeyBqn5VscEHL-kVg/exec?action=getQuote'
    );
    if (!res.ok) throw new Error(res.status);
    return await res.json();
  } catch (err) {
    console.error('Error fetching daily quote:', err);
    return null;
  }
};

// Example usage:
getDailyQuote().then(q => {
  if (q) {
    console.log(`${q.quote} — ${q.author} (${q.date})`);
  }
});
```

#### Python

```python
import requests

def get_daily_quote():
    """Fetches the daily quote from the API."""
    url = "https://script.google.com/macros/s/AKfycbyU2tuTOsLmynjo7oKCUwT4UAXrvfWZSHgnLDqrtK_e1aY_1HyL2LeyBqn5VscEHL-kVg/exec"
    params = {
        "action": "getQuote"
    }
    
    try:
        response = requests.get(url, params=params)
        response.raise_for_status()  # Raise an exception for bad status codes
        
        quote_data = response.json()
        return quote_data
    except requests.exceptions.RequestException as e:
        print(f"Error fetching daily quote: {e}")
        return None

# Example usage:
quote = get_daily_quote()
if quote:
    print(f"{quote['quote']} — {quote['author']} ({quote['date']})")
```

-----

### About the Project

The API is built using **Google Apps Script**, which allows it to function as a simple web service without the need for a dedicated server. You can view and fork the source code for the API itself in the script editor.
