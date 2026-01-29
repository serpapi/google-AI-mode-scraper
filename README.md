![<img width="950" height="300" alt="Google AI Mode scraper" src="https://github.com/user-attachments/assets/ea592cbd-7aca-4f5b-a0be-8d5076807022" />](https://serpapi.com/?utm_source=github_google_ai_mode_scraper)

Google AI Mode Scraper - A tool to scrape Google's AI Mode search results with a simple API. Get AI-generated answers, text blocks, references, shopping results, local results, and support for multi-turn conversations.

We provide the results in a structured JSON format, eliminating the need for parsing, coding, proxies, or any other web scraping headaches for developers.

## How to scrape Google AI Mode?

Using a simple GET request, you can retrieve Google AI Mode results:

```
https://serpapi.com/search.json?engine=google_ai_mode&q=What+is+machine+learning&api_key=YOUR_API_KEY
```

- Register for free at [SerpApi to get your API Key](https://serpapi.com/google-ai-mode-api?utm_source=github_google_ai_mode_scraper)
- `q` parameter: defines the search query (same as regular Google search).
- `subsequent_request_token` parameter (optional): continues a multi-turn conversation.

## Code examples
Here are some code examples based on your favorite programming languages.

### cURL Integration

``` bash
curl --get https://serpapi.com/search \
 -d engine="google_ai_mode" \
 -d q="What is machine learning" \
 -d api_key="secret_api_key"
```

### Python Integration

Step 1:
Create a new `main.py` file.

Step 2:
Install [requests package](https://pypi.org/project/requests/) with:
```
pip install requests
```

Step 3:
Add this code to your file:
``` py
import requests
SERPAPI_API_KEY = "YOUR_SERPAPI_API_KEY"

params = {
    "api_key": SERPAPI_API_KEY,
    "engine": "google_ai_mode",
    "q": "What is machine learning"
}

search = requests.get("https://serpapi.com/search", params=params)
response = search.json()
print(response)
```

If you're interested in the `text_blocks`, you can print them from the response directly:

``` py
print(response["text_blocks"])
```

For multi-turn conversations, use the `subsequent_request_token`:

``` py
# Continue the conversation
if "subsequent_request_token" in response:
    params["subsequent_request_token"] = response["subsequent_request_token"]
    params["q"] = "Can you give me an example?"

    follow_up = requests.get("https://serpapi.com/search", params=params)
    print(follow_up.json())
```

### JavaScript Integration

Step 1:
Install the [SerpApi JavaScript package](https://github.com/serpapi/serpapi-javascript):
```
npm install serpapi
```

Step 2:
Create a new `index.js` file.

Step 3:
Add this to your file:
``` js
const { getJson } = require("serpapi");
getJson({
  api_key: API_KEY,
  engine: "google_ai_mode",
  q: "What is machine learning"
}, (json) => {
  console.log(json["text_blocks"]);

  // For follow-up questions, use subsequent_request_token
  if (json.subsequent_request_token) {
    console.log("Token for follow-up:", json.subsequent_request_token);
  }
});
```

### Other Programming Languages
While you can use our APIs using a simple GET request with any programming language, you can also see our ready-to-use libraries here: [SerpApi Integrations](https://serpapi.com/integrations?utm_source=github_google_ai_mode_scraper).

## Google AI Mode Scraper Parameters
Please find the parameters for the Google AI Mode API below:

| Name           | Description                                                                                                                                      | Requirement |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| q              | Parameter defines the search query                                                                                                               | Required    |
| **Localization**   |                                                                                                                                              |             |
| location       | Parameter defines search origin point (city-level recommended)                                                                                   | Optional    |
| gl             | Parameter defines the two-letter country code (e.g., `us`, `uk`, `fr`)                                                                           | Optional    |
| hl             | Parameter defines the two-letter language code (e.g., `en`, `es`, `fr`)                                                                          | Optional    |
| **Conversation**   |                                                                                                                                              |             |
| subsequent_request_token | Parameter to continue a multi-turn conversation with prior context                                                                     | Optional    |
| **Advanced**       |                                                                                                                                              |             |
| device         | Parameter defines the device: `desktop` (default), `tablet`, or `mobile`                                                                         | Optional    |
| no_cache       | Parameter to force fresh results                                                                                                                 | Optional    |

Visit [our documentation](https://serpapi.com/google-ai-mode-api) for more information on all available parameters.


## Available data on Google AI Mode (JSON Response)
Google AI Mode returns AI-generated responses with various content types:

``` json
{
  "text_blocks": [
    {
      "type": "String - Block type (paragraph, heading, list, table, code_block)",
      "snippet": "String - Text content",
      "reference_indexes": "Array - Indexes linking to references"
    }
  ],
  "references": [
    {
      "index": "Integer - Reference number",
      "title": "String - Source page title",
      "link": "String - URL to the source",
      "snippet": "String - Brief excerpt",
      "source": "String - Source website name"
    }
  ],
  "quick_results": "Object - Featured snippets and quick answers",
  "shopping_results": "Array - Product listings with prices",
  "local_results": "Array - Location-based businesses",
  "inline_images": "Array - Embedded images",
  "inline_videos": "Array - Embedded videos",
  "subsequent_request_token": "String - Token for continuing conversations"
}
```

Text block types include: `paragraph`, `heading`, `list`, `table`, `code_block`

## Use cases
Here are some use cases for the Google AI Mode API:

- Build AI-powered search interfaces with conversational capabilities.
- Monitor how Google's AI responds to queries about your brand or products.
- Create research tools that leverage AI-generated summaries.
- Build chatbots that use Google's AI Mode for information retrieval.
- Track which sources Google's AI cites for SEO research.
- Create competitive intelligence tools analyzing AI responses.

## Blog tutorial
- [Scrape Google AI Mode - Scraping AI Answers for Generative Engine Optimization (GEO), SEO and More](https://serpapi.com/blog/scrape-google-ai-mode-introducing-the-new-google-ai-mode-api/)
- [Find and Track Google's AI Mode Cited Sources](https://serpapi.com/blog/find-and-track-googles-ai-mode-cited-sources/)

## Contacts
Feel free to reach out via `contact@serpapi.com`.

Check other [Google Scrapers](https://serpapi.com/google-ai-mode-api) from SerpApi.
