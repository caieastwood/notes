## 通配符查询
db.getCollection('property').find({"propertyGroupName" : /.*walgreens.*/})  
db.getCollection('property').find({"propertyGroupName" : /walgreens/})