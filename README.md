# mongodb-query

### 1. Membuat databse academic
```
use academic
```

### 2. Menampilkan semua collection dan data dalam database
```
db.getCollectionNames()
```

### 3. Membuat dan mengaktifkan database
```
use academic
```

### 4. Membuat collection department
```
db.createCollection("department");
```

### 5. Membuat collection student
```
db.createCollection("student");
```

### 6. Melihat struktur collection student
```
var col_list= db.student.findOne();
for (var col in col_list) { print (col) ; }
```

### 7. menginputkan 5 data data ke dalam collection department
```
db.department.insert([
{
  code: "1",
  name: "Hacktiv8",
  major: "Computer"
},
{
  code: "2",
  name: "Hacktiv9",
  major: "Dokter"
},
{
  code: "3",
  name: "Hacktiv10",
  major: "Akutansi"
},
{
  code: "4",
  name: "Hacktiv11",
  major: "Masak"
},
{
  code: "5",
  name: "Hacktiv12",
  major: "hotel"
}])
```

### 8. menginputkan 3 data ke dalam collection student beserta reference ke department.
```
db.student.insert([
{
  studentId: "1",
  name: "alexander",
  address: "jl. pluit",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a02"),
        "$db" : "users"
    },
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a03"),
        "$db" : "users"
    }
  ]
},
{
  studentId: "2",
  name: "yoni",
  address: "jl. pim",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a05"),
        "$db" : "users"
    }
  ]
},
{
  studentId: "3",
  name: "ken",
  address: "jl. kudo",
  department: [
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a02"),
        "$db" : "users"
    },
    {
        "$ref": "department",
        "$id" : ObjectId("5890166668c31f5259343a06"),
        "$db" : "users"
    }
  ]
}])
```

### 9. Melihat isi collection student
```
db.student.find({})
```

### 10. Menampilkan key name dan address dalam collectino student
```
db.student.find({}, { name: 1, address: 1})
```

### 11. Menampilkan key studentId, name, dan address dari data student yang mempunyai studentId tertentu.
```
db.student.find({studentId:"1"})
```

### 12. Menampilkan semua data student secara urut berdasarkan name dengan sort() secara ascending maupung descending.
```
/* asc | sort document ascending by studentId */
db.student.find().sort( { studentId: 1 } )
/* desc | sort document descending by studentId */
db.student.find().sort( { studentId: -1 } )
```

### 13. Menampilkan semua data department secara urut berdasarkan name secara scending maupun descending.
```
/* asc | sort document ascending by studentId */
db.department.find().sort( { name: 1 } )
/* desc | sort document descending by studentId */
db.department.find().sort( { name: -1 } )
```

### 14. Mencari data student dengan name
```
db.student.find({ name: "ken" })
```
