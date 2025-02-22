# 🚀 **Advanced Database System**  
An advanced and easy-to-use database system for Node.js with multi-database support, caching, encryption, and schema validation.

---

## 🌟 **Features**  
- ✅ **Multi-Database Support:** SQLite and Redis  
- ⚡ **Advanced Querying:** Filtering, sorting, and pagination  
- 🧩 **Schema Validation:** Ensure structured data  
- 🚀 **Caching System:** Faster reads with configurable cache  
- 🔒 **Encryption:** Secure sensitive data  
- 🧹 **Simple API:** Minimal and user-friendly design  
- 💾 **Transactions:** Atomic operations  
- 🔗 **Plugin System:** Extend functionality  

---

## 📦 **Installation**  
```bash
npm install advanced-db
```

---

## 💡 **Usage**  

### 🔗 **Connecting to a Database**  
```javascript
const db = require('advanced-db');

// Connect to SQLite
await db.connect('sqlite://database.sqlite');

// Connect to Redis
await db.connect('redis://localhost:6379');

// Check database connection
await db.ping();
```

### ✨ **CRUD Operations**  
```javascript
// Create or update data
await db.set('user:123', { name: 'John', age: 30 });

// Get data
const user = await db.get('user:123');
console.log(user);

// Delete data
await db.delete('user:123');

// Check if a key exists
const exists = await db.has('user:123');
console.log(exists);
```

### 📋 **Advanced Querying**  
```javascript
// Filtering
const users = await db.query('users').filter({ age: { $gt: 25 } }).get();

// Sorting
const sortedUsers = await db.query('users').sort('age', 'desc').get();

// Pagination
const page1 = await db.query('users').paginate(1, 10).get();

// Complex queries with multiple conditions
const advancedQuery = await db.query('users').filter({
  age: { $gt: 25 },
  name: { $regex: '^J' }
}).sort('name', 'asc').paginate(1, 5).get();
```

### ⚡ **Caching**  
```javascript
// Enable caching
await db.enableCache({ duration: 60, maxSize: 100 }); // Cache duration in seconds, max cache size

// Clear cache
await db.clearCache();

// Check cache status
console.log(db.cacheStatus());
```

### 🔒 **Encryption**  
```javascript
// Enable encryption
await db.enableEncryption('my_secret_key', { algorithm: 'aes-256-cbc' });

// Data will be encrypted automatically
await db.set('sensitiveData', 'This is confidential');

// Retrieve and decrypt data
const sensitiveData = await db.get('sensitiveData');
console.log(sensitiveData);
```

---

## 🛠️ **Configuration**  
You can configure the database using environment variables or programmatically.

| 📝 **Option**        | 📋 **Description**                                 |
|--------------------|--------------------------------------------------|
| `DB_URL`           | Database connection URL                          |
| `CACHE_DURATION`   | Cache duration in seconds                        |
| `CACHE_MAX_SIZE`   | Maximum number of items in the cache             |
| `ENCRYPTION_KEY`   | Secret key for encryption                        |
| `ENCRYPTION_ALGO`  | Encryption algorithm (default: aes-256-cbc)      |

---

## 🔗 **Plugins**  
Extend the functionality using plugins:
```javascript
const myPlugin = (db) => {
  db.customMethod = () => console.log('Custom method');
};

db.use(myPlugin);
db.customMethod();

// List all registered plugins
console.log(db.listPlugins());
```

---

## ⚠️ **Error Handling**  
```javascript
try {
  await db.set('user:123', { name: 'John' });
} catch (error) {
  console.error('Database error:', error.message);
}

// Custom error handling
await db.onError((error) => {
  console.error('Custom error handler:', error);
});
```

---

## 🧪 **Testing**  
```bash
npm test

// Run tests with coverage
npm run coverage
```

---

## 📄 **Documentation**  
- [API Reference](docs/API.md)  
- [Advanced Usage](docs/AdvancedUsage.md)  
- [Plugins](docs/Plugins.md)  

---

## 🤝 **Contributing**  
Contributions are welcome! Feel free to submit a pull request or open an issue.

1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Submit a Pull Request

---

## 📜 **License**  
This project is licensed under the [MIT License](LICENSE).


I've updated the README to use javascript instead of js so the code blocks are easily copyable. Let me know if you need more adjustments!

