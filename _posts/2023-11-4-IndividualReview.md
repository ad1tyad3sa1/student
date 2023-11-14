---
comments: true
layout: post
title: Individual Review
description: Work for Passion Project
type: hacks
courses: { csp: {week: 12}}
---

## Car Info API

- My role in the passion project for my team was to work as a backend developer implementing our primary API into the project. 

1. Developing an API for our Car Information:

```python
from flask import Blueprint, jsonify, request
from flask_restful import Api, Resource, reqparse
from __init__ import db
from model.cars import Car  # Import the car model
import requests

# Create a Blueprint for the car API
car_api = Blueprint('car_api', __name__, url_prefix='/api/car')

# Create the API instance
api = Api(car_api)

class CarAPI:
    class _Create(Resource):
        def post(self):
            # Get request JSON data
            body = request.get_json()

            # Extract car information
            make = body.get('make')
            model = body.get('model')
            year = body.get('year')
            fuel = body.get('fuel')
            cylinders = body.get('cylinders')

            # Create a new car object
            car_obj = Car(make=make, model=model, year=year, fuel=fuel, cylinders=cylinders)

#2: Key Code block to add car to database 
            # create car in database
            car = car_obj.create()
            # success returns json of car
            if car:
                return jsonify(car.read())
            # failure returns error
            return {'message': f'Invalid input, correct fields should be make, model, year, and fuel, cylinders'}, 400

            
    class _Read(Resource):
        def get(self):
        # Retrieve all cars from the database
            Cars = Car.query.all()
            json_ready = [car.to_dict() for car in Cars]
        # Return the JSON response
            return jsonify(json_ready)

    # building RESTapi resources/interfaces, these routes are added to Web Server
    api.add_resource(_Create, '/create')
    api.add_resource(_Read, '/')
```

Define API, set up blueprint, and import required modules
Set the class for the API which connected the JSON information stored in our model
Extracted car information from our API in objects (cars)
Initialized two key endpoints
    - POST /api/car/create
    - GET /api/car/

2. Creating the model for our API

```python
from __init__ import db

# Define the "Car" model
class Car(db.Model):
    # Define the table name in the database
    __tablename__ = "Car"

    # This defines all of the attributes of a car that we will display
    id = db.Column(db.Integer, primary_key=True)  
    make = db.Column(db.String, nullable=False)
    model = db.Column(db.String, nullable=False)
    year = db.Column(db.String, nullable=False)
    fuel = db.Column(db.String, nullable=False)
    cylinders = db.Column(db.String, nullable=False)

    # Constructor to initialize a new car object
    def __init__(self, make, model, year, fuel, cylinders):
        self.make = make
        self.model = model
        self.year = year
        self.fuel = fuel
        self.cylinders = cylinders

    def to_dict(self):
        return {"make": self.make, "model": self.model, "year": self.year, "fuel": self.fuel, "cylinders": self.cylinders}
    # Create method to let users add a song to the DB
    def create(self):
        try:
            db.session.add(self)  # add prepares to persist object to table
            db.session.commit()  # SQLAlchemy requires a manual commit
            return self
        except: 
            db.session.remove() # remove object from table if invalid
            return None

    # Method to return car details for API response
    def read(self):
        return {
            "id": self.id,
            "make": self.make,
            "model": self.model,
            "year": self.year,
            "fuel": self.fuel,
            "cylinders": self.cylinders
        }

def initCars():
    BugattiChiron = Car(make="Bugatti", model="Chiron", year="2021", fuel="Gas", cylinders="16"); db.session.add(BugattiChiron)
    TeslaRoadster = Car(make="Tesla", model="Roadster", year="2024", fuel="Electricity", cylinders="None"); db.session.add(TeslaRoadster)
    RollsRoycePhantom = Car(make="Rolls Royce", model="Phantom", year="2021", fuel="Gas", cylinders="8"); db.session.add(RollsRoycePhantom)
    MercedesBenzGClass = Car(make="Mercedes Benz", model="G Class", year="2022", fuel="Gas", cylinders="10"); db.session.add(MercedesBenzGClass)
    AstonMartinDB11 = Car(make="Aston Martin", model="DB11", year="2023", fuel="Gas", cylinders="14"); db.session.add(AstonMartinDB11)
    Ferrari488GTB = Car(make="Ferrari", model="488GTB", year="2023", fuel="Gas", cylinders="9"); db.session.add(Ferrari488GTB)
    BentleyContinentalGT = Car(make="Bentley", model="Continental GT", year="2023", fuel="Gas", cylinders="10"); db.session.add(BentleyContinentalGT)
    Porsche911Targa = Car(make="Porsche", model="911 Targa", year="2023", fuel="Gas", cylinders="8"); db.session.add(Porsche911Targa)
    McLaren720S = Car(make="McLaren", model="720 S", year="2024", fuel="Gas", cylinders="6"); db.session.add(McLaren720S)
    MaseratiQuattroporte = Car(make="Maserati", model="Quattroporte", year="2021", fuel="CNG", cylinders="None"); db.session.add(MaseratiQuattroporte)
    AudiR8Spyder = Car(make="Audi", model="R8 Spyder", year="2022", fuel="Hydrogen Powered", cylinders="8"); db.session.add(AudiR8Spyder)
    MercedesBenz300SLGullwing = Car(make="Mercedes Benz", model="300 SL Gullwing", year="2021", fuel="Gas", cylinders="6"); db.session.add(MercedesBenz300SLGullwing)
    Ferrari250GTCalifornia = Car(make="Ferrari", model="250 GT California", year="2023", fuel="Gas", cylinders="8"); db.session.add(Ferrari250GTCalifornia)
    BentleyFlyingSpur = Car(make="Bentley", model="Flying Spur", year="2021", fuel="Gas", cylinders="4"); db.session.add(BentleyFlyingSpur)
    AudiA8 = Car(make="Audi", model="A8", year="2022", fuel="Gas", cylinders="8"); db.session.add(AudiA8)
    JaguarFType = Car(make="Jaguar", model="F-Type", year="2020", fuel="Gas", cylinders="10"); db.session.add(JaguarFType)
    LamborghiniHuracan = Car(make="Lamborghini", model="Huracan", year="2024", fuel="Hydrogen Powered", cylinders="12"); db.session.add(LamborghiniHuracan)
    RivianR1S = Car(make="Rivian", model="R1S", year="2023", fuel="Electricity", cylinders="None"); db.session.add(RivianR1S)
    MercedesBenzMaybachSClass = Car(make="Mercedes Benz", model="Maybach S Class", year="2022", fuel="Gas", cylinders="6"); db.session.add(MercedesBenzMaybachSClass)
    BMW7Series = Car(make="BMW", model="7 Series", year="2021", fuel="Hydrogen Powered", cylinders="8"); db.session.add(BMW7Series)
    LincolnContinental = Car(make="Lincoln", model="Continental", year="2020", fuel="Gas", cylinders="4"); db.session.add(LincolnContinental)
    RivianR1T = Car(make="Rivian", model="R1T", year="2022", fuel="Electricity", cylinders="None"); db.session.add(RivianR1T)
    db.session.commit()
```

* Creates the Car class specifying parameters (make, model, year, etc...) adds all information stored in an SQL database where the API add these elements for display

3. Getting our API to work:

```python
import threading

# import "packages" from flask
from flask import render_template  # import render_template from "public" flask libraries

# import "packages" from "this" project
from __init__ import app,db  # Definitions initialization
from model.jokes import initJokes
from model.users import initUsers
from model.players import initPlayers
from model.cars import initCars


# setup APIs
from api.covid import covid_api # Blueprint import api definition
from api.joke import joke_api # Blueprint import api definition
from api.user import user_api # Blueprint import api definition
from api.player import player_api
from api.car import car_api 


# setup App pages
from projects.projects import app_projects # Blueprint directory import projects definition


# Initialize the SQLAlchemy object to work with the Flask app instance
db.init_app(app)

# register URIs
app.register_blueprint(joke_api) # register api routes
app.register_blueprint(covid_api) # register api routes
app.register_blueprint(user_api) # register api routes
app.register_blueprint(player_api)
app.register_blueprint(app_projects) # register app pages
app.register_blueprint(car_api) #register car api

@app.errorhandler(404)  # catch for URL not found
def page_not_found(e):
    # note that we set the 404 status explicitly
    return render_template('404.html'), 404

@app.route('/')  # connects default URL to index() function
def index():
    return render_template("index.html")

@app.route('/table/')  # connects /stub/ URL to stub() function
def table():
    return render_template("table.html")

@app.before_first_request
def activate_job(): # activate these items 
    db.drop_all() #drops preexisting entries fetched by api
    db.create_all() #recreates api entries
    initJokes()
    initUsers()
    initPlayers()
    initCars()

# this runs the application on the development server
if __name__ == "__main__":
    # change name for testing
    from flask_cors import CORS
    cors = CORS(app)
    app.run(debug=True, host="0.0.0.0", port="8420")
```

* Flask web application includes database initialization, API endpoints, error handling, and routes for rendering HTML templates regarding our Car API.

API Testing:

I primarily tested our API's functionality and got it working...

Get Requests registered on Postman and web console

![Postman Test](https://cdn.discordapp.com/attachments/795744270732099634/1170926793495162981/postman.png?ex=655ad18e&is=65485c8e&hm=f67c021941cd92872300a835df43e59cfdc07f0431dcce0e7c47d940585c3001&)

![Web Console](https://cdn.discordapp.com/attachments/795744270732099634/1170929990741794906/web_console.png?ex=655ad488&is=65485f88&hm=4d5562dd6ff3d8b66773bf826b6cf9c9d905e831eb5d0821c7f3af07ac84522a&)

Evidence for commits:

- [API/Model](https://github.com/Swaggerplayer33/Flask-Server-Back-End-/commit/a8db0039ec21243916520b874790245698f27fed#diff-08918cab63a0ed5ce3fa108f6d5abcb69f19a0db54a0d627d5142d414a12eccf)

- [Fix for multiple instances](https://github.com/Swaggerplayer33/Flask-Server-Back-End-/commit/9f794f79ed669333da4f4e37554f6652d863d0eb)

- [API](https://github.com/Swaggerplayer33/Flask-Server-Back-End-/commit/b1eaa2120896d802d6e439032db6aab7c5176a9d)

- [Model](https://github.com/Swaggerplayer33/Flask-Server-Back-End-/commit/024e8d5be1602e4fed2c0bc7ef3ef075f5944b14)

- [main.py](https://github.com/Swaggerplayer33/Flask-Server-Back-End-/commit/8dc4b604e5a54e16cf0af553113cc222dfdc2bf5)

Challenges Faced: 

Finding an optimal way to store the data

Rooms for Improvement:

Working toward making a more interactive interface, with a pop up, that allows the user to display specific car info without fetching data directly from database.