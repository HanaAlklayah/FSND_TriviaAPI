# Full Stack Trivia API Project

## Introduction
Trivia api is a web application that allows people to hold trivia on a regular basis using a webpage to manage the trivia app and play the game.

The app allows one to:
  1. Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer.
  2. Delete questions.
  3. Add questions and require that they include question and answer text.
  4. Search for questions based on a text query string.
  5. Play the quiz game, randomizing either all questions or within a specific category.

## API Reference
  ### Getting Started

  #### Installing Dependencies
  Developers using this project should already have Python3, pip, node, and npm installed.

  #### Backend Dependencies
  * `Backend` Base URL: http://127.0.0.1:5000/
  * From within the `backend` directory

        {
          pip install -r requirements.txt
        }
  * To run the server, execute:
  
        {
          export FLASK_APP=flaskr
          export FLASK_ENV=development
          flask run
        }

  #### Frontend Dependencies
  * `Frontend` Base URL: http://127.0.0.1:3000/

  * This project uses NPM to manage software dependencies. from the `frontend` directory run:

        {
          npm install
          npm start
        }

  ### Erorr Handling
  * Errors are returned in the following json format.
   
        {
          "error": 404, 
          "message": "Resource not found", 
          "success": false
        }

  * The error codes currently returned are:

         400 – bad request
         404 – resource not found
         422 – unprocessable
         500 – internal server error

  ### Endpoints
   #### GET /categories
   * General: Returns a list categories.
   * Sample: curl http://127.0.0.1:5000/categories
 
          {
            "categories": {
              "1": "Science", 
              "2": "Art", 
              "3": "Geography", 
              "4": "History", 
              "5": "Entertainment", 
              "6": "Sports"
            }, 
            "success": true
          }

   #### GET /questions
   * General: Returns a list questions.
   * Sample: curl http://127.0.0.1:5000/questions
   
          {
            "categories": {
              "1": "Science", 
              "2": "Art", 
              "3": "Geography", 
              "4": "History", 
              "5": "Entertainment", 
              "6": "Sports"
              }, 
            "questions": [
              {
                "answer": "Maya Angelou", 
                "category": "4", 
                "difficulty": 2, 
                "id": 3, 
                "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
              }, 
              {
                "answer": "Muhammad Ali", 
                "category": "4", 
                "difficulty": 1, 
                "id": 4, 
                "question": "What boxer's original name is Cassius Clay?"
              }, 
              {
                "answer": "Apollo 13", 
                "category": "5", 
                "difficulty": 4, 
                "id": 5, 
                "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
              }, 
              {
                "answer": "Tom Cruise", 
                "category": "5", 
                "difficulty": 4, 
                "id": 6, 
                "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
              }, 
              {
                "answer": "Edward Scissorhands", 
                "category": "5", 
                "difficulty": 3, 
                "id": 7, 
                "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
              }, 
              {
                "answer": "Brazil", 
                "category": "6", 
                "difficulty": 3, 
                "id": 8, 
                "question": "Which is the only team to play in every soccer World Cup tournament?"
              }, 
              {
                "answer": "Uruguay", 
                "category": "6", 
                "difficulty": 4, 
                "id": 9, 
                "question": "Which country won the first ever soccer World Cup in 1930?"
              }, 
              {
                "answer": "George Washington Carver", 
                "category": "4", 
                "difficulty": 2, 
                "id": 10, 
                "question": "Who invented Peanut Butter?"
              }, 
              {
                "answer": "Lake Victoria", 
                "category": "3", 
                "difficulty": 2, 
                "id": 11, 
                "question": "What is the largest lake in Africa?"
              }, 
              {
                "answer": "The Palace of Versailles", 
                "category": "3", 
                "difficulty": 3, 
                "id": 12, 
                "question": "In which royal palace would you find the Hall of Mirrors?"
              }
            ], 
            "success": true, 
            "total_questions": 19
          }

   #### DELETE /questions/int:id\
   * Sample: curl http://127.0.0.1:5000/questions/6 -X DELETE
  
          {
            "message": "Question successfully deleted", 
            "success": true
          }

   #### POST /questions
   * Sample: curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{ "question": "Frankie Fredericks represented which African country in  athletics?", "answer": "Namibia", "difficulty": 3, "category": "6" }'
   
          {
            "message": "Question successfully created!", 
            "success": true
          }

   #### POST /questions/search
   * Sample: curl http://127.0.0.1:5000/questions/search -X POST -H "Content-Type: application/json" -d '{"searchTerm": "Anne Rice"}'
     
         {
            "questions": [
              {
              "answer": "Tom Cruise", 
              "category": 5, 
              "difficulty": 4, 
              "id": 4, 
              "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
              }
            ], 
            "success": true, 
            "total_questions": 20
          }

   #### GET /categories/int:id\/questions
   * Sample: curl http://127.0.0.1:5000/categories/1/questions
   
    {
      "current_category": "Science", 
      "questions": [
        {
          "answer": "The Liver", 
          "category": 1, 
          "difficulty": 4, 
          "id": 20, 
          "question": "What is the heaviest organ in the human body?"
        }, 
        {
          "answer": "Alexander Fleming", 
          "category": 1, 
          "difficulty": 3, 
          "id": 21, 
          "question": "Who discovered penicillin?"
        }, 
        {
          "answer": "Blood", 
          "category": 1, 
          "difficulty": 4, 
          "id": 22, 
          "question": "Hematology is a branch of medicine involving the study of what?"
        }
      ], 
      "success": true, 
      "total_questions": 3
    }

   #### POST /quizzes
   * Sample: curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions": [5, 9], "quiz_category": {"type": "History", "id": "4"}}'
   
    {
      "question": 
      {
        "answer": "Scarab", 
        "category": 4, 
        "difficulty": 4, 
        "id": 19, 
        "question": "Which dung beetle was worshipped by the ancient Egyptians?"
      }, 
      "success": true
    }
