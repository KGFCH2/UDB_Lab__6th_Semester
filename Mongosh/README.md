# 🍃 Mongosh: MongoDB Shell Operations
**Unstructured Database Lab (CSE12203)** | **Babin Bid**

This folder contains the core MongoDB shell (`mongosh`) implementations, focusing on schema-less data management, JavaScript-driven data manipulation, and real-time API integrations.

---

## 👨‍💻 Author Profile
*   **Name:** Babin Bid
*   **LinkedIn:** [Babin Bid](https://www.linkedin.com/in/babinbid123/)
*   **GitHub:** [@KGFCH2](https://github.com/KGFCH2)
*   **University:** Adamas University

---

## 🗓️ Day 1: MongoDB Fundamentals

### ❓ Question 1
**Create a Database in MongoDB Shell (Mongosh) and insert an item.**

Initialize a new database and perform a document insertion to verify correct shell configuration.

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
test> use btech_b
**(Press Enter)**

btech_b> db.createCollection("C2")
**(Press Enter)**

btech_b> db.C2.insertOne({
    "name" : "Babin",
    "age" : 21,
    "phone" : 9123777679,
    "stream" : "CSE"
})
**(Press Enter)**
```

### 🔍 Verification & Expected Output
```javascript
btech_b> db.C2.find().pretty()
**(Press Enter)**

// Expected Output:
[
  {
    _id: ObjectId("6970xxxxxxxxxxxx"),
    name: 'Babin',
    age: 21,
    phone: 9123777679,
    stream: 'CSE'
  }
]
```

---

### ❓ Question 2
**Write a program in JS to display the elements of an array, which stores the first ten natural numbers using Mongosh script.**

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
btech_b> function display_numbers() {
    var arr = [1,2,3,4,5,6,7,8,9,10]
    for(var i = 0; i < arr.length; i++) {
        print(arr[i])
    }
}
**(Press Enter)**

btech_b> display_numbers()
**(Press Enter)**

// Expected Output:
1
2
3
4
5
6
7
8
9
10
```

---

### ❓ Question 3
**Write a program to store the names of 10 classmates in an array and hobbies in another array using Mongosh script.**

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
btech_b> function store_arrays() {
    var classmates = ["A","B","C","D","E","F","G","H","I","J"]
    var hobbies = ["Reading","Music","Gaming","Traveling","Photography",
                   "Cricket","Dancing","Coding","Drawing","Singing"]
    
    print("Classmates:", classmates)
    print("Hobbies:", hobbies)
}
**(Press Enter)**

btech_b> store_arrays()
**(Press Enter)**

// Expected Output:
Classmates: [ 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J' ]
Hobbies: [ 'Reading', 'Music', 'Gaming', 'Traveling', 'Photography', 'Cricket', 'Dancing', 'Coding', 'Drawing', 'Singing' ]
```

---

### ❓ Question 4
**Delete an existing item from MongoDB Shell.**

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
btech_b> db.C2.deleteOne({ name: "Babin" })
**(Press Enter)**

// Expected Output:
{ acknowledged: true, deletedCount: 1 }
```

### 🔍 Verification & Expected Output
```javascript
btech_b> db.C2.find()
**(Press Enter)**

// Expected Output:
[ ]
```

---

## 🗓️ Day 2: API Integration & Automation

### ❓ Question 5
**Fetch Date/Time Data from a REST API.**

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
async function get_dt() {
    const res = await fetch("https://classmonitor.aucseapp.in/get_date_time.php");
    if (!res.ok) {
        console.log("ERROR: API Unreachable");
        return;
    }
    const data = await res.json();
    console.log(data);
}
**(Press Enter)**

get_dt()
**(Press Enter)**

// Expected Output (JSON Response):
{
  day_of_week: '2',
  weekday_name: 'Tuesday',
  day_of_month: '17',
  month: 'February',
  year: '2026',
  hour: '21',
  minutes: '10',
  seconds: '00',
  milliseconds: 80,
  date: '2026-02-17',
  time: '21:10:00.080',
  datetime: '2026-02-17 21:10:00.080',
  timezone: 'Asia/Kolkata'
}
```

---

### ❓ Question 6
**Automate script for Real-time API Data Ingestion (Cron Job).**

### ✅ Answer (MongoDB Shell – mongosh)
```javascript
async function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function watchAPI() {
    print("Watcher started...");
    while (true) {
        try {
            const res = await fetch("https://classmonitor.aucseapp.in/get_date_time.php");
            if (!res.ok) {
                print("API ERROR");
                await sleep(60000);
                continue;
            }

            const newData = await res.json();
            const lastDoc = db.currentDateTime.find().sort({ insertedAt: -1 }).limit(1).toArray();

            if (lastDoc.length === 0 || 
                lastDoc[0].date !== newData.date || 
                lastDoc[0].time !== newData.time) {
                
                db.currentDateTime.insertOne({
                    ...newData,
                    insertedAt: new Date()
                });
                print("New data inserted at:", new Date());
            } else {
                print("No change detected at:", new Date());
            }
        } catch (err) {
            print("Error:", err.message);
        }
        await sleep(60000); // Polling interval
    }
}
**(Press Enter)**

watchAPI();
**(Press Enter)**

// Expected Runtime Logs:
Watcher started...
New data inserted at: ISODate('2026-02-17T15:42:46.739Z')
No change detected at: ISODate('2026-02-17T15:43:47.054Z')
```

---

<p align="center">Created with ❤️ by <b>Babin Bid</b> | Adamas University</p>
