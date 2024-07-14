### Programming Quiz Game Documentation

#### Overview
The Programming Quiz Game is a non-web-based application developed using Python and Tkinter. The game provides users with a series of questions related to programming languages. The user interface is designed to be interactive and user-friendly, with a full-screen dark mode theme, green color buttons, and intuitive navigation.

#### Features
1. **Interactive UI:** The game uses a full-screen mode with a dark theme and green-colored buttons to enhance visual appeal.
2. **Question Navigation:** Users can navigate through questions using 'Previous' and 'Next' buttons. On the last question, a 'Submit' button appears to finish the quiz.
3. **Score Calculation:** The score is calculated based on the number of correct answers selected by the user.
4. **Result Display:** After submitting the quiz, the result page displays the score and feedback based on the user's performance. It also highlights the wrong answers with the correct answers for review.
5. **Quit Option:** A 'Quit' button is available on every page except the last one to allow users to exit the game at any time.
6. **Window Controls:** Custom close and minimize buttons are provided to control the application window.

#### Game Flow
1. **Start Page:** The game starts with a welcome page displaying the title "PROQUIZ" and two buttons: 'Start Game' and 'Quit'.
2. **Quiz Interface:** Upon starting the game, the user is presented with the first question. Users can navigate through the questions using the 'Previous' and 'Next' buttons.
3. **Answer Selection:** Users select an answer by clicking on one of the radio buttons. The selected answer turns green.
4. **Score Update:** The score is updated in real-time as the user selects the correct answer.
5. **Submission:** On the last question, the 'Next' button is replaced by the 'Submit' button. Clicking 'Submit' ends the quiz and displays the result page.
6. **Result Page:** The result page shows the total score, feedback based on the score, and a list of incorrectly answered questions with the correct answers.

#### Code Explanation

##### 1. Importing Required Libraries
```python
import tkinter as tk
```
- `tkinter` is imported to create the GUI application.

##### 2. Defining Questions, Options, and Answers
```python
questions = [
    "What is the output of print(2**3) in Python?",
    "Which keyword is used to create a function in Python?",
    "What is the correct file extension for Python files?",
    "Which language is primarily used for web development?",
    "What is the main difference between a list and a tuple in Python?",
    "What does 'var' mean in JavaScript?",
    "What is the purpose of inheritance in object-oriented programming?",
    "Which keyword is used to define a class in Java?",
    "How do you write a comment in Python?",
    "What is the use of the 'import' statement in Python?"
]

options = [
    ["6", "8", "9", "7"],
    ["function", "def", "fun", "define"],
    [".pyth", ".pt", ".pyt", ".py"],
    ["Python", "C++", "JavaScript", "Java"],
    ["Lists are immutable, tuples are mutable", "Lists are mutable, tuples are immutable", "Both are mutable", "Both are immutable"],
    ["Variable declaration", "Function declaration", "Class declaration", "None of the above"],
    ["Code reuse", "Memory management", "Syntax highlighting", "None of the above"],
    ["class", "Class", "define", "function"],
    ["# This is a comment", "// This is a comment", "/* This is a comment */", "<!-- This is a comment -->"],
    ["To include functions from other modules", "To declare variables", "To define classes", "To handle exceptions"]
]

answers = [
    "8", "def", ".py", "JavaScript", 
    "Lists are mutable, tuples are immutable", "Variable declaration", 
    "Code reuse", "class", 
    "# This is a comment", 
    "To include functions from other modules"
]
```
- Lists of questions, options, and correct answers are defined for the quiz.

##### 3. Creating the Quiz Application Class
```python
class QuizApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Programming Quiz Game")
        self.root.attributes('-fullscreen', True)
        self.root.configure(bg="#2e2e2e")
        ...
```
- The `QuizApp` class is initialized with the root window. The window is set to full-screen mode with a dark background.

##### 4. Creating the Start Page
```python
        self.main_frame = tk.Frame(root, bg="#2e2e2e", bd=5, relief=tk.RIDGE)
        self.main_frame.pack(expand=True)

        self.title_label = tk.Label(self.main_frame, text="PROQUIZ", font=("Arial", 48, "bold"), bg="#2e2e2e", fg="#ffffff")
        self.title_label.pack(pady=20)

        self.start_button = tk.Button(self.main_frame, text="Start Game", command=self.start_game, font=("Arial", 24), bg="#00a86b", fg="#ffffff")
        self.start_button.pack(pady=20, fill=tk.X, padx=30)

        self.quit_button = tk.Button(self.main_frame, text="Quit", command=root.destroy, font=("Arial", 24), bg="#FF4C4C", fg="#ffffff")
        self.quit_button.pack(pady=20, fill=tk.X, padx=30)
```
- A frame is created for the start page with the title, 'Start Game' button, and 'Quit' button.

##### 5. Starting the Game
```python
    def start_game(self):
        self.main_frame.destroy()
        self.create_quiz_interface()
```
- The `start_game` method destroys the start page frame and creates the quiz interface.

##### 6. Creating the Quiz Interface
```python
    def create_quiz_interface(self):
        self.question_frame = tk.Frame(self.root, bg="#2e2e2e", bd=5, relief=tk.RIDGE)
        self.question_frame.pack(expand=True)

        self.question_label = tk.Label(self.question_frame, text="", font=("Arial", 18), bg="#2e2e2e", fg="#ffffff")
        self.question_label.pack(pady=20)

        self.user_answer = tk.StringVar(value="")
        self.option_buttons = []
        for i in range(4):
            rb = tk.Radiobutton(self.question_frame, text="", variable=self.user_answer, value='', font=("Arial", 16), bg="#2e2e2e", fg="#ffffff", anchor="w", command=lambda i=i: self.select_option(i))
            rb.pack(fill="x", padx=20, pady=5)
            self.option_buttons.append(rb)

        self.nav_frame = tk.Frame(self.question_frame, bg="#2e2e2e")
        self.nav_frame.pack(pady=20)

        self.prev_button = tk.Button(self.nav_frame, text="Previous", command=self.prev_question, font=("Arial", 16), bg="#00a86b", fg="#ffffff")
        self.prev_button.pack(side=tk.LEFT, padx=10)

        self.next_button = tk.Button(self.nav_frame, text="Next", command=self.next_question, font=("Arial", 16), bg="#00a86b", fg="#ffffff")
        self.next_button.pack(side=tk.RIGHT, padx=10)

        self.submit_button = tk.Button(self.nav_frame, text="Submit", command=self.submit_answer, font=("Arial", 16), bg="#00a86b", fg="#ffffff")

        self.question_index = 0
        self.score = 0
        self.user_answers = [""] * len(questions)

        self.quit_button = tk.Button(self.nav_frame, text="Quit", command=self.root.destroy, font=("Arial", 16), bg="#FF4C4C", fg="#ffffff")
        self.quit_button.pack(side=tk.LEFT, padx=10)

        self.update_question()
        self.update_navigation_buttons()
```
- A frame is created for the quiz interface, including the question label, option buttons, and navigation buttons ('Previous', 'Next', 'Submit').

##### 7. Selecting an Option
```python
    def select_option(self, index):
        for i, button in enumerate(self.option_buttons):
            button.config(fg="#ffffff")  # Reset color
        self.option_buttons[index].config(fg="#00ff00")  # Change color to green
```
- The `select_option` method highlights the selected option in green.

##### 8. Updating the Question
```python
    def update_question(self):
        self.question_label.config(text=questions[self.question_index])
        for i in range(4):
            self.option_buttons[i].config(text=options[self.question_index][i], value=options[self.question_index][i])
            self.option_buttons[i].deselect()
            self.option_buttons[i].config(fg="#ffffff")  # Reset color
```
- The `update_question` method updates the question and option buttons based on the current question index.

##### 9. Navigation Buttons
```python
    def update_navigation_buttons(self):
        if self.question_index == len(questions) - 1:
            self.next_button.pack_forget()
            self.submit_button.pack(side=tk.RIGHT, padx=10)
        else:
            self.submit_button.pack_forget()
            self.next_button.pack(side=tk.RIGHT, padx=10)

        if self.question_index > 0:
            self.prev

_button.pack(side=tk.LEFT, padx=10)
        else:
            self.prev_button.pack_forget()

    def next_question(self):
        self.user_answers[self.question_index] = self.user_answer.get()
        if self.user_answer.get() == answers[self.question_index]:
            self.score += 1
        self.question_index += 1
        self.update_question()
        self.update_navigation_buttons()

    def prev_question(self):
        self.question_index -= 1
        self.update_question()
        self.update_navigation_buttons()
```
- `update_navigation_buttons` manages the visibility of navigation buttons.
- `next_question` and `prev_question` handle question navigation.

##### 10. Submitting the Quiz
```python
    def submit_answer(self):
        self.user_answers[self.question_index] = self.user_answer.get()
        if self.user_answer.get() == answers[self.question_index]:
            self.score += 1
        self.display_result()

    def display_result(self):
        self.question_frame.destroy()
        result_frame = tk.Frame(self.root, bg="#2e2e2e", bd=5, relief=tk.RIDGE)
        result_frame.pack(expand=True)

        result_label = tk.Label(result_frame, text=f"Your Score: {self.score} / {len(questions)}", font=("Arial", 18), bg="#2e2e2e", fg="#ffffff")
        result_label.pack(pady=20)

        result_text = "Results:\n"
        for i in range(len(questions)):
            if self.user_answers[i] != answers[i]:
                result_text += f"Q{i + 1}: {questions[i]}\nYour answer: {self.user_answers[i]}\nCorrect answer: {answers[i]}\n\n"

        result_details = tk.Label(result_frame, text=result_text, font=("Arial", 14), bg="#2e2e2e", fg="#ffffff", justify=tk.LEFT)
        result_details.pack(pady=20)

        feedback_label = tk.Label(result_frame, text=self.get_feedback(), font=("Arial", 18), bg="#2e2e2e", fg="#ffffff")
        feedback_label.pack(pady=20)

        quit_button = tk.Button(result_frame, text="Quit", command=self.root.destroy, font=("Arial", 16), bg="#FF4C4C", fg="#ffffff")
        quit_button.pack(pady=20)
```
- The `submit_answer` method saves the user's answer and calculates the score.
- The `display_result` method shows the score, feedback, and a list of incorrectly answered questions.

##### 11. Feedback Based on Score
```python
    def get_feedback(self):
        score = self.score
        if score == 10:
            return "Outstanding!"
        elif score >= 8:
            return "Well done!"
        elif score >= 6:
            return "Keep going!"
        elif score >= 4:
            return "You need to improve."
        elif score >= 2:
            return "Try hard!"
        else:
            return "Better luck next time!"
```
- The `get_feedback` method provides feedback based on the user's score.

##### 12. Running the Application
```python
def create_quiz_app():
    root = tk.Tk()
    app = QuizApp(root)
    root.mainloop()

# Run the app
create_quiz_app()
```
- The `create_quiz_app` function initializes and runs the quiz application.

#### Conclusion
This documentation provides an overview and detailed explanation of the Programming Quiz Game. The game is designed to be engaging and educational, offering users a fun way to test their programming knowledge. Feel free to customize and expand the game according to your preferences and requirements.
