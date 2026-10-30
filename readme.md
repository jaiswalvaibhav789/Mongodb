Mongodb :- 
		Mongodb is a NOSQL Database management system.
	a. If you want to create database in mongodb
		syntax:- use database_name
		ex- use school
	b. if you want to create collection
	Syntax- db.createCollection('student')
	
	c. if you want to check how many collections.
	Syntax:- show collections
	
	CRUD Operations
		
		C=> Create
			if You wanto to insert any document 
			Syntax:-
				db.collection_name.insertOne({
					"name":"Priyanka Chopra",
					"branch":"CSE",
					"age":"42"
				})
				
				db.student.insert_one({
					"name":"Priyanka Chopra",
					"branch":"CSE",
					"age":"42"
				})
			if you want to insert many documents in one time.
			syntax:- db.student.insertMany([
			{
			name:"Govinda",
			age:55,
			course:"BA"
			},
			{
			name:"Hrithik Roshan",
			age:52,
			course:"Diploma",
			city:"Mumbai"
			},
			{
			name:"Virat Kohli",
			age:39,
			course:"12th",
			city:"London"
			}
			])
		
	d. If you want to show documents.
	Syntax:-
		db.collection_name.find();
		Ex:-
			db.student.find()
			
		i. if you want to find any document on the behalf of condition
		Syntax:-
			db.collection_name.find({fieldname:condition});
		Ex:-
			db.student.find({age:55})
			db.student.find({city:"Londom"})
		
		
	E. If you want to update any document.
	syntax:-
	db.student.updateOne({name:"Virat Kohli"},{$set:{
	name:"Run Machine",
	age:30
	}})
	
	D Delete=>
		a. If you want to delete one document at a time
			db.employee.deleteOne(); //it deletes first document 
			db.employee.deleteOne(Condition); // it deletes particular document
		
		b. If you want to delete all document at a time
			db.employee.deleteMany(); //it deletes all document 
			db.employee.deleteMany(Condition); // it deletes Many document on the behalf of condition.

	
Practice Sessions=>
		a.create a database which name is company.
		ans:  use company
		b. create a collection which name is employee.
		ans: db.createCollection("employee")
		c. insert at least 5 documents in employee.
		ans: db.employee.insertMany([
		{
		name:"Shikhar Dhawan",
		Department:"IT",
		salary:40000,
		city:"Delhi"
		},
		{
		name:"Smrit",
		Department:"Sales",
		salary:35000,
		city:"Amritsar"
		},
		{
		name:"Shreyas Iyer",
		Department:"IT",
		salary:30000,
		city:"Mumbai"
		},
		{
		name:"Bhuvi",
		Department:"Sales",
		salary:30000,
		city:"Meruth"
		},
		{
		name:"Yuvi",
		Department:"CSE",
		salary:30000,
		city:"Amritsar"
		}
		])
		
		
		d. find all employee on the behalf of departments
		
		ans:  db.employee.find({Department:"IT"})
		e. update all employee department from sales to BD
		ans : db.employee.updateMany({Department:"Sales"},{
		$set:{
		Department:"BD"
		}
		});
	
	

Query Operators =>
	Query Operators are used to help us to perform the query on the database.
	ex-> $lt= , $gt ,$lte , $gte , $ne etc.
	1. $lt => $lt used for less then query operators.
	Ex->db.employee.find({age:{$lt:20}})

	2.$gt => $gt is used for greater then query operators
		Ex->db.employee.find({age:{$gt:20}})

	3.$lte => it is used for less than and equal.
		ex-> db.employee.find({age:{$lte:20}})
Aggregation Pipeline =>
	Aggregation pipeline is a way to to perform the computation on documents in mongodb.
	Ex=> $group , $match , $limit , $skip etc.

	1.$limit =>
		db.employee.aggregate([
			{
				$limit:3
			}
		]);
	2.$skip =>
		Skip are used to skip the documents 
		Ex->
			db.employee.aggregate([
				{
					$skip:3
				}
			])

	3.$sort =>
		$sort are used to perform the sorting in accending, decnding orders.
		Ex-> db.employee.aggregate([
			{
				$sort:{
					age:-1
				}
			}
		])
Normal Operations =>
	a. If you want to fetch limited documents from db.
	Ex=> db.employee.find().limit(3);
		it fetches only three documents 
	b. If you want to skip any document
		Ex-> db.employee.find().skip(3)
	c. If you want to performing sorting for any documents
		Ex-> db.employee.find().sort({age:-1})
	
	d. If you want to find all documents after that you want to sort them on the behalf of age then you want to skip 2 documents then you want to find only 2 documents 

	Solution :-
		db.employee.find().sort({age:1}).skip(2).limit(2)
		Aggregate pipeline+>
		db.employee.aggregate([
			{
				$sort:{
				age:1
			}
			},
			{
				$skip:2
			
			},
			{
				$limit:2
			}
		])



	db.employee.insertMany([
		{
			name:"Vaibhav",
			salary:20000,
			city:"Lucknow",
			branch:"Lucknow",
			department:"IT"
		},
		{
			name:"Shatrughan",
			salary:10000,
			city:"Delhi",
			branch:"Lucknow",
			department:"Sales"
		},
		{
			name:"Raman",
			salary:30000,
			city:"Delhi",
			branch:"Lucknow",
			department:"IT"
		},
		{
			name:"Naman",
			salary:40000,
			city:"Delhi",
			branch:"Lucknow",
			department:"Sales"
		},
		{
			name:"Aniket",
			salary:22000,
			city:"RB",
			branch:"Noida",
			department:"IT"
		},
		{
			name:"Utkarsh",
			salary:35000,
			city:"KLD",
			branch:"Noida",
			department:"IT"
		},
		{
			name:"Sumit",
			salary:21000,
			city:"KLD",
			branch:"Noida",
			department:"Accounts"
		},
		{
			name:"Dixi",
			salary:25000,
			city:"KLD",
			branch:"Noida",
			department:"CSE"
		}
	])

	$match are used for find the document that is matched on the behalf of condition
	db.employee.aggregate([
		{
			$match:{
				branch:"Lucknow"
			}
		},
		{
			$group:{
				_id:"$department",
				"totalSalary":{
					$sum:"$salary"
				}
			}
		}
	])