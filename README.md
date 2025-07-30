from flask import Flask
from flask_restful import Api, Resource

app = Flask(__name__)

api = Api(app)

data = [{'id': 1, 'name':'karan', 'Age':16}, 
        {'id':5, 'name':'karan', 'Age':85}]

def find_person(person_id):
    for person in data:
        if person['id'] == person_id:
            return person
    
    return None



class PeopleResource(Resource):
    def get(Self):
        return data
    def post(self):
        new_person = [{'id':6, 'name':'karan', 'Age':85}]
        data.append(new_person)
        return new_person
    

class PersonResource(Resource):
    def get(self, person_id):
      person = find_person(person_id)
      if person:
        return person
      return ({'message': 'person not found'})



api.add_resource(PeopleResource, '/people')
api.add_resource(PersonResource, '/people/<int:person_id>')

if __name__ == '__main__':

    app.run(debug = True)
