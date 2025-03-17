# DAX Query View URL Generator

A simple, elegant tool that generates shareable URLs for Power BI DAX Query View.

![DAX Query View URL Generator](https://user-images.githubusercontent.com/your-username/your-repo/main/screenshot.png)

Overview by Zoe Douglas on DAX Query View URL : https://www.youtube.com/live/FKMXG0Oga0Q?si=kslHvC1775JXo4eu

## 🚀 Features

- **Simple Interface**: Clean, intuitive design that's easy to use
- **Instant URL Generation**: Convert DAX queries to shareable URLs with one click
- **GZIP Compression**: Efficiently compresses queries to fit within URL length restrictions
- **Base64 Encoding**: Creates URL-safe query strings
- **Copy & Open Functionality**: Easily copy or directly open generated URLs

## 🔍 What is DAX Query View?

DAX Query View is a Power BI feature that allows analysts to run and share DAX queries directly in the Power BI service. This tool makes it easy to generate shareable URLs containing your DAX queries.

## 📊 How It Works

1. Enter your **Power BI Workspace ID** (GUID)
2. Enter your **Semantic Model ID** (GUID)
3. Write or paste your **DAX query**
4. Click **Generate URL**
5. Copy the URL or click to open it directly in Power BI

The tool handles all the required processing:
- Compresses the query using GZIP
- Encodes the compressed data in Base64
- Makes the data URL-safe
- Constructs the final URL with your workspace and dataset IDs

## 🛠️ Technical Details

The URL generation follows Microsoft's specifications for DAX Query View URLs. Under the hood, the tool:

```javascript
// Convert string to Uint8Array
const uint8Array = new TextEncoder().encode(daxQuery);

// Compress with pako (GZIP)
const compressedData = pako.gzip(uint8Array);

// Convert to base64
let base64Data = arrayBufferToBase64(compressedData);

// Make URL-safe
const urlSafeData = encodeURIComponent(base64Data);

// Construct the final URL
const url = `https://app.powerbi.com/groups/${workspaceId}/modeling/${datasetId}/daxQueryView?query=${urlSafeData}`;
```

## 🔗 Useful Links

- [Learn more about DAX Query View in Power BI](https://learn.microsoft.com/en-us/power-bi/transform-model/dax-query-view#dax-query-view-in-web)
- [Generate URL using Semantic Link Labs](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.generate_dax_query_view_url)
- [Visit Fabric.guru](https://www.fabric.guru) for more Power BI resources

## 🚀 Getting Started

### Using the Live Version

Simply visit: https://pawarbi.github.io/DAXQueryViewURLGenerator/

### Running Locally

1. Clone this repository
2. Open `index.html` in any modern web browser

## 👨‍💻 Development

This is a pure HTML/CSS/JavaScript application with no build steps. To modify:

1. Edit `index.html` to change the UI or functionality
2. Test by opening the file locally in your browser
3. Deploy by pushing changes to the `main` branch

## 📝 Credits

Created by Sandeep Pawar with assistance from Claude 3.7 Sonnet.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Made with ❤️ for the Power BI community
