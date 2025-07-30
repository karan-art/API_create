from flask import Flask
from flask_restful import Api, Resource

app = Flask(__name__)
api = Api(app)

data = [{'student_id' : 1, 'Name': 'karan', 'Roll_no': 365}, 
        {'student_id' : 1, 'Name': 'karan', 'Roll_no': 365}]


class PeopleResource(Resource):
    def get(self):
        return data
    def post(Self):
        new_person = {"id": 5, "name":"Swati", "Roll_no":655}
        data.append(new_person)
        return new_person
    
api.add_resource(PeopleResource, '/people')

if __name__ == '__main__':

    app.run(debug = True)
    
