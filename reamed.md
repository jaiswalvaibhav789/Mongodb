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
	
	