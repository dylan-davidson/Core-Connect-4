The final project is worth **130** points, which will be awarded as follows:

| Category | Points |
|-------------------|----------|
| [Proposal](Grading#proposal) | 10 pts |
| [Core](Grading#core) | 50 pts |
| Core Team Evaluations | 5 pts |
| [Reach](Grading#reach) | 50 pts |
| Reach Team Evaluations | 5 pts |
| [Showcase](Grading#showcase) | 10 pts |

## Proposal

All groups must submit a project proposal.

The team that you submit your proposal with constitutes your team for the Final Project. There will be no revisions to these teams except in situations which merit staff intervention. You may not change your team once this document has been submitted.

#### Names, Uniqnames, and Github Names
Begin your proposal with each member of your team's full name, their uniqname, _and_ their Github name. Even if your team member's Github name is the exact same as your uniqname, do be _specific_ and clear in order to help avoid grading errors. If you want to be fun, pick a team name! However, this is not a requirement.

#### Overall Project Description
Your proposal must include a **brief** description (5 to 6 sentences) of what the program will do, and how users will interact with it. Think about how you would describe your program to a friend. You should describe the basic functionality of your program and what features you are planning for the reach.

#### Group Logistics
Your group should be meeting regularly. In your proposal, list when and where your group will be holding meetings. Also, describe how your group will communicate with each other (we like GroupMe). Finally, describe how your group will divide and assign tasks among group members.

#### Submission
Submit your proposal (one per team) in PDF format by **11/19 at 6:00pm**. Submissions are accepted until **11/19 at 11:59pm** under the **Proposal: Connect 4** assignment. To do so please follow these instructions:

1. Head to [EECS 183 on Gradescope](https://gradescope.com/courses/12014), then choose Proposal: Connect 4 from the assignments list. Select Submit PDF and upload proposal.pdf.

2. Once the PDF file has been uploaded, select pages corresponding to each part (i.e. question) of the proposal assignment. Click Save.

3. Click on Add Group Member on top right. Add the three other members of your team by typing their names or email addresses. Once everyone on your team is in the list, click Save. Everyone who has been added to the group on Gradescope will receive an email and will be able to access the submission, including the score and staff's comments after the proposal has been graded.

4. Finally, have **ONE PERSON** on your team head over to [register.eecs183.org](http://register.eecs183.org) to sign your team up for a GitHub repository. Fill out all of the necessary information. For project, select "Connect4" from the drop-down menu. If you receive the message "Submission has been recorded! Thank You!", then you are done. **YOU SHOULD ONLY SUBMIT ONCE PER TEAM.** If you have some issues, the website will alert you of the fields that were incorrectly filled out. Correct any mistakes, and submit again. Continue until you see the message above. If you are having trouble with this form, post on Piazza to get help."

Remember that the team you submit your proposal with will be your finalized team for the Final Project.

## Core

Your Core grade will be determined by how well your function implementations adhere to the RME's specified in the distributed code. Please note that your core grade will not be based on overall functionality but rather on successful implementation of RME's for each independent function in **board.cpp** and **connect4.cpp**.

**The core is due 12/1 by 6:00 and excepted until 12/1 11:59pm** The following table shows a breakdown of the points based general functionality. 

| Category | Description | Points |
|----------------|---------------------------------------|----------|
| Compilation | Your implementation successfully compiles. | 5 pts |
| Basic Functionality | • Reading in two names<br/>• Having a loop that prints the board and menu, and reads in user input<br/>• Alternating menu options for both players | 10pts |
| Making a Move | • Determining an illegal move<br/>• Finding the lowest empty row in the selected column<br/>• Changing the state of the board based on the move<br/>• Putting the correct player's token in the board | 10pts |
| Determine End of Game| • Determining if a player has won<br/>• Determining if a draw has occurred<br/>• Checking for a win or a draw after every move<br/>• Stopping all gameplay if there is a win or a draw | 15pts |
| File I/O | • Reading a board from a file correctly<br/>• Creating the correct FEN string for a board and writing it to a file | 10pts |
| | | 50pts |

**Important note: the above breakdown is for reference only. All functions implemented must comply with their respective RMEs in order to get full credit for each category.** 

## Reach

Make sure you update your README.md file in your repository with what reach you chose and what functionalities you decided to implement. In the scenario that you implemented both reaches, we will only grade one! Ensure you specify which one you implemented in the README.md file. Note for the AI reach that there is a total of 60 points available to earn, depending on how many times your AI wins. However, you only need to earn 50 to receive full points. Any extra points will not be counted towards your reach grade.

### Graphics

If you want to implement ideas that are not given in the table **(highly encouraged!)**, contact us at 183connect4@umich.edu so we can let you know if it would fit in the Medium Functionality or the Hard Functionality.

| Category | Description | Points |
|----------------|---------------------------------------|----------|
| Medium Functionality | The following are some ideas that fit in this category (two are needed to get full points):<br/>• Having the player's token follow the mouse<br/>• Making a move using a mouse click<br/>• Resizing or centering the board when the window is resized | 15pts |
| Hard Functionality | The following are some ideas that fit in this category (two are needed to get full points):<br/>• Animating the token dropping down a column<br/>• Highlighting the winning tokens<br/>• Creating a menu or splash screen for the game | 35pts |
| | | 50pts |

### Artificial Intelligence

| Category | Description | Points |
|----------------|---------------------------------------|----------|
| Easy | Your implementation beats our [easy](Reach#Easy_AI) AI. We will run 5 games against our easy AI and you implementation must beat our easy AI 3 out of the 5 times to earn full points. Otherwise, you earn 0 points. | 25 pts |
| Medium | Your implementation beats our medium AI. We will run 5 games against our medium AI with each run worth 4 points. | 20 pts |
| Hard | Your implementation beats our hard AI. We will run 5 games against our hard AI with each run worth 3 points. | 15 pts |
| | | 50 pts |

## Showcase

At the showcase you will be demo-ing your project. We expect your demos to be about 3 minutes long, and walk us through the major features of your project. All team members should be prepared to answer technical questions about how different features were implemented. We will be grading the showcase based on attendance (you get points just for showing up!), the quality of your presentation and your technical explanations. We encourage you to be creative and enthusiastic!
 
Try to tell the story of why someone should play your Connect 4 game.  After seeing your demo, we should get a good idea of what your program can do and how it is unique. You should prepare and practice your demo with your teammates.
 
We recommend doing your demo off a laptop, no poster required. But if you wish to do something else, that should be fine, but please let us know in advance. Table space is limited. Make sure you have at least 2 fully charged laptops ready to go for the presentation. You will not have access to electrical power at your table.