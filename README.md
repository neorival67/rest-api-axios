# 📦 rest-api-axios

A simple Node.js project using **Express.js** to create a REST API, **Axios** to consume external APIs, and **EJS** as a templating engine for rendering HTML views.

---

## 🚀 Getting Started

### 🔧 Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/neorival67/rest-api-axios.git
   cd rest-api-axios
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Run the server:**

   ```bash
   node index.js
   ```

4. Open your browser and visit:  
   [http://localhost:3000](http://localhost:3000)

---

## 📁 Project Structure

```
rest-api-axios/
├── index.js               # Main application entry
├── solution.js            # Axios logic to fetch data from external API
├── package.json           # Project metadata and dependencies
├── views/
│   └── index.ejs          # EJS template for rendering frontend
```

---

## 🛠 Technologies Used

- **Node.js** – JavaScript runtime
- **Express.js** – Web framework
- **Axios** – HTTP client for API requests
- **EJS** – Templating engine for server-side rendering

---

## 📄 Usage Example

### 1. Axios Logic (`solution.js`)

```js
const axios = require('axios');

async function getData() {
  try {
    const response = await axios.get('https://api.example.com/data');
    return response.data;
  } catch (error) {
    console.error('API error:', error);
    return null;
  }
}

module.exports = { getData };
```

### 2. Express Server (`index.js`)

```js
const express = require('express');
const { getData } = require('./solution');

const app = express();
app.set('view engine', 'ejs');

app.get('/', async (req, res) => {
  const data = await getData();
  res.render('index', { data });
});

app.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});
```

### 3. View Template (`views/index.ejs`)

```html
<!DOCTYPE html>
<html>
<head>
  <title>Data Viewer</title>
</head>
<body>
  <h1>Fetched Data</h1>
  <pre><%= JSON.stringify(data, null, 2) %></pre>
</body>
</html>
```

---

## ✅ How It Works

- When visiting `/`, the server fetches data from an external API using Axios.
- The fetched data is passed to the `index.ejs` template.
- The browser renders the data in a readable format.

---

## 🧪 Testing

1. Start the app with `node index.js`.
2. Open `http://localhost:3000`.
3. Confirm that the API data appears on the webpage.

---

## 📚 References

- [Express.js Docs](https://expressjs.com/)
- [Axios Docs](https://axios-http.com/)
- [EJS Docs](https://ejs.co/)

---

## 📬 Contributing

Feel free to fork the repository and submit pull requests for improvements or bug fixes. For any questions or issues, open a GitHub Issue.
