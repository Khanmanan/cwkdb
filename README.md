🚀 Advanced Database System

An advanced and easy-to-use database system for Node.js with multi-database support, caching, encryption, and schema validation.


---

🌟 Features

✅ Multi-Database Support: SQLite and Redis
⚡ Advanced Querying: Filtering, sorting, and pagination
🧩 Schema Validation: Ensure structured data
🚀 Caching System: Faster reads with configurable cache
🔒 Encryption: Secure sensitive data
🧹 Simple API: Minimal and user-friendly design
💾 Transactions: Atomic operations
🔗 Plugin System: Extend functionality


---

📦 Installation

npm install advanced-db


---

💡 Usage

🔗 Connecting to a Database

const db = require('advanced-db');

// Connect to SQLite
await db.connect('sqlite://database.sqlite');

// Connect to Redis
await db.connect('redis://localhost:6379');

✨ CRUD Operations

// Create or update data
await db.set('user:123', { name: 'John', age: 30 });

// Get data
const user = await db.get('user:123');
console.log(user);

// Delete data
await db.delete('user:123');

📋 Advanced Querying

// Filtering
const users = await db.query('users').filter({ age: { $gt: 25 } }).get();

// Sorting
const sortedUsers = await db.query('users').sort('age', 'desc').get();

// Pagination
const page1 = await db.query('users').paginate(1, 10).get();

⚡ Caching

// Enable caching
await db.enableCache({ duration: 60 }); // Cache duration in seconds

// Clear cache
await db.clearCache();

🔒 Encryption

// Enable encryption
await db.enableEncryption('my_secret_key');

// Data will be encrypted automatically
await db.set('sensitiveData', 'This is confidential');


---

🛠️ Configuration

You can configure the database using environment variables or programmatically.


---

🔗 Plugins

Extend the functionality using plugins:

const myPlugin = (db) => {
  db.customMethod = () => console.log('Custom method');
};

db.use(myPlugin);
db.customMethod();


---

⚠️ Error Handling

try {
  await db.set('user:123', { name: 'John' });
} catch (error) {
  console.error('Database error:', error.message);
}


---

🤝 Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue.


---

📜 License

This project is licensed under the MIT License.

