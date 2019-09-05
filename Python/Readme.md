## Python concepts need to learn


Modules
  - Json
  - CSV
  - OS
  - Requests
  - Regular Expressions
  - Random
  - collections
  - multi processing
  - SQLAlchemy
  - Numpy
  - Scipy
  - Pandas
  - Matplotlib
  - Boto3
  - Flask
  - PrettyTable
  
  Reference: 
    - https://medium.com/activewizards-machine-learning-company/top-15-python-libraries-for-data-science-in-in-2017-ab61b4f9b4a7


### Proxy issue behind the firwall then use like below.

    -  pip install --proxy http://user:password@proxyserver:port TwitterApi
    -  pip install --proxy http://proxy-wsa.esl.cisco.com:80 flask     --- Worked for me



## Flask

	    Flask is a lightweight Python framework for web applications that provides the basics for URL routing and page rendering.

	    Flask is called a "micro" framework because it doesn't directly provide features like form validation, database abstraction, authentication, and so on. Such features are instead provided by special Python packages called Flask extensions. The extensions integrate seamlessly with Flask so that they appear as if they were part of Flask itself.

   #### Sample flask application

	    from flask import Flask, escape, request

	    app = Flask(__name__)

	    @app.route('/')
	    def hello():
		name = request.args.get("name", "Anand")
		return f'Hello, {escape(name)}!'

   #### For execution :

	    - set the execution path
		     set FLASK_APP=flasktest.py

	    - for running application
		     flask run

	    -  For Running application in debug mode (if you did any changes that need to be reflect in main application automatically)
		     set FLASK_DEBUG=1
		     then try to run 
			  - flask run

		(or)

		if __name__ == '__main__':
		      app.run(debug=True)



#### Reference Program 

		from flask import Flask, escape, request

		app = Flask(__name__)

		@app.route('/')
		def hello():
		    name = request.args.get("name", "Anand")
		    return f'Hello, {escape(name)}!'


		if __name__ == '__main__':
			app.run(debug=True)

  
#### Pass a Single HTML page under a Route


		from flask import Flask, escape, request

		app = Flask(__name__)

		@app.route('/')
		def hello():
		     return '''
		    <!Doctype html>
			<html>
			<head>
				<h1> Home Page </h1>
			</head>
			<body> 
			<h2> this is the Home page body section </h2>
			</body>
			</html>
		     '''

		@app.route('/about')
		def about():
		    return "<h1> About Page </h1>"
		if __name__ == '__main__':
			app.run(debug=True)
		
		

Exceptions & Error Handling : 
-----------------------------
		An exception is an error that happens during execution of a program. When that
		error occurs, Python generate an exception that can be handled, which avoids your
		program to crash.

		try:
		     p = open('csv_data.csv')
		     data = big_data
		except FileNotFoundError as e:
		    print(e)
		except Exception as e:
		    print(e)


#### Example with try , except, else and Finally block : 


		try:
		     p = open('csv_data.csv')
		    # data = big_data
		except FileNotFoundError as e:
		    print(e)
		except Exception as e:
		    print(e)
		else:
		    print(p.read())
		    p.close()
		finally:
		    print("Finally Executing Successfully")
	    
#### Raise Your own Exception :

		try:
		     p = open('csv_data.csv')
		     if p.name == 'csv_data.csv':
			 raise Exception
		except FileNotFoundError as e:
		    print(e)
		except Exception as e:
		    print('Manual Error')
		else:
		    print(p.read())
		    p.close()
		finally:
		    print("Finally Executing Successfully")