Download Link: https://assignmentchef.com/product/solved-eecs-285-project-2-tefball
<br>
For this project, you will implement a simple game called <em>TefBall</em> (tef = <strong>t</strong>wo <strong>e</strong>ighty-<strong>f</strong>ive). The game has some remote resemblance to American football, but is very simple in comparison. No knowledge of football is necessary to be successful on this project.

TefBall is played on a rectangular field. The game consists of multiple objects on the field, including a ball, and some number of players. All players progress through the game via a function named performMove() – however, different types of players act differently, so this project will utilize polymorphism to provide multiple implementations (ways to move) for a common interface (the performMove() method). The primary focus of this project is the use of polymorphism, so be sure not to try to circumvent the use of it during your design. <strong>If you do not make good use of inheritance and polymorphism as expected, you will not receive credit for your project.</strong> The goal of TefBall is to successfully throw the ball and have a receiver catch it without being caught by a defender.

<strong>Authors</strong>

The original project was written by Andrew M. Morgan for EECS 285.

<h1>Table of Contents</h1>

<h1>Project Roadmap</h1>

This is a big-picture view of what you’ll need to do to complete this project. Most of the pieces listed here also have a corresponding section later on in the spec that goes into more detail.

<a href="https://eecs285.github.io/eecs285.org/style.html">This project will be autograded for correctness. We will also hand grade it for both </a><a href="https://eecs285.github.io/eecs285.org/style.html">programming practices</a><a href="https://eecs285.github.io/eecs285.org/style.html"> and the comprehensiveness of your test cases. We will also run automated style and </a>programming-practice checks on your code.

The following is a tentative grade breakdown for this project:

80% autograded correctness, style, and programming practices

20% hand-graded style, programming practices, and test cases

You may work alone or with a partner. Please see the syllabus for partnership rules.

<h2>Download the starter code</h2>

The starter code is available at <a href="https://eecs285.github.io/p2-tefball/starter-files.zip">https://eecs285.github.io/p2-tefball/starter-files.zip</a>. The following files are included:

<table width="554">

 <tbody>

  <tr>

   <td width="192"><strong>File(s)</strong></td>

   <td width="362"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="192">PlayingField.java</td>

   <td width="362">Game driver – implements the game simulation</td>

  </tr>

  <tr>

   <td width="192">PlayTefball1.javaPlayTefball2.java</td>

   <td width="362">Command-line interface, intended as test code</td>

  </tr>

  <tr>

   <td width="192">PlayTefball1.correctPlayTefball2.correct</td>

   <td width="362">Correct output from running the test code</td>

  </tr>

 </tbody>

</table>

Extract the files to a temporary directory.

<h2>Set up your project</h2>

Follow the <a href="https://eecs285.github.io/p1-sentiments/setup.html">Project 1 setup tutorial</a> to set up your project. Use the package name described below.

Your Java files should all be in a package with the structure eecs285.proj2.&lt;uniqname&gt; , where

&lt;uniqname&gt; is your uniqname. <strong>If you are working in a partnership, then use both of your uniqnames, in alphabetical order, separated by an underscore.</strong> For example, if I am working alone, I would put the following package directive at the top of each .java file: <strong>package</strong> eecs285<strong>.</strong>proj2<strong>.</strong>akamil<strong>;</strong>

If I am working with schatzju , then I would use the following: <strong>package</strong> eecs285<strong>.</strong>proj2<strong>.</strong>akamil_schatzju<strong>;</strong>

<strong>Familiarize yourself with the game rules below</strong>

Read through and make sure you understand the rules for Tefball before writing any code.

<strong>Familiarize yourself with the required interface</strong>

Your implementation must adhere to the required interface described below.

<h2>Design, implement, and test your classes</h2>

Implement your game simulation in the PlayingField class that is part of the starter code. Define the other parts of the required interface and any other classes you need and place them appropriately as standalone classes in their own .java files, nested classes, or anonymous classes.

Write your test code in files that follow the PlayTefball*.java naming pattern. We will exclude them from some of the automated style checks (e.g. code duplication, since it is likely there will some duplication in setting up individual tests).

<h2>Submit</h2>

Submit the following files to the autograder.

PlayingField.java any other .java files you write, including test code

As per course policy, we will grade your last submission to the autograder. It is your responsibility to ensure that your last submission is complete.

<h2>Early Submission Bonus</h2>

If your final submission occurs at least two days before the due date (at or before 11:59pm two days before the due date), you will receive bonus points calculated at 5% of your overall score for the project (including both autograder tests and hand grading). In other words, if your overall score is <em>N</em>, it will be <em>1.05 * N</em> after the bonus is applied.

If your final submission occurs on the day before the due date (by 11:59pm), you will receive bonus points calculated at 2.5% of your overall score for the project. In other words, if your overall score is <em>N</em>, it will be <em>1.025 * N</em> after the bonus is applied.

<h1>Game Rules</h1>

<h2>Player Types and Descriptions</h2>

There are only three types of players in this version of TefBall, and they are described below. Each specific type of player must inherit from a more generic class that represents any player, regardless of type. You should put attributes and functionality that apply to all players, regardless of type, in the base class, and attributes and functionality that apply only to specific types in the appropriate subclass. You should avoid placing functionality that doesn’t apply to all subclasses in the base class.

<h3>Quarterback</h3>

The quarterback is the player that has possession of the ball at the start of the game. In TefBall, there is exactly one quarterback, who acts in a very specific way. First, the quarterback starts at a specified location, and upon starting the game, moves toward a specified final position while holding the ball (that is, the ball moves with the quarterback at the beginning of the game, until thrown). Upon arriving at the final (actual floating point, non-rounded) position, the quarterback throws the ball to a pre-determined specified location. After throwing the ball, the quarterback stops moving and is no longer a factor in the game.

<h3>Receiver</h3>

TefBall allows multiple receivers to play at the same time. Each individual receiver starts at a specified location, and upon starting the game, moves toward a specified intermediate position. Upon arriving at the intermediate (actual floating point, non-rounded) position, the receiver changes direction and moves toward a specified final location. When a receiver arrives at the final location, they wait there, without further movement.

<h3>Defender</h3>

TefBall allows multiple defenders to play at the same time. A defender starts at a specified location, and upon starting the game, moves toward the quarterback’s current location. Once the quarterback throws the ball, the defenders change their strategy and begin running to the location that the ball is being thrown to (i.e. the ball’s destination).

<h2>Progression of the Game</h2>

As the game progresses, the user is shown a view of the field. Players and the ball move in a continuous way (i.e. their positions, and destinations are maintained and calculated as doubleprecision floating point values). However, when the field is drawn to the screen, an object in the game (ball or player) is drawn at the nearest (integer rounded) row and nearest (integer rounded) column. If two objects occupy the same row and column, the object that moved last is the one that is displayed. Since we are using polymorphism, players will move <em>in the order they were specified</em> by the user. The order that players move is an important strategy in TefBall, since if a defender moves before the quarterback moves and ends up occupying the same space, a sack will have been made. However, if the quarterback moves first, the quarterback may have moved to a different location before the defender arrives, and when the defender moves, they are occupying different spaces. Due to this, you must ensure that players move in the order specified – it is not acceptable for all receivers to move first, followed by all defenders, etc.

The game proceeds in <em>rounds</em>. During each round, the players take <em>turns</em> moving. Before the ball is thrown, its position is the same as the quarterback’s, as described above. Starting the round <em>after</em> the ball is thrown, the ball moves to its destination in each round <em>before</em> any other players move.

Before a round of the game, the current state of the field is drawn to the screen as shown here for a field with width 16 and height 12:

01234567890123456

0—————–

1——–Q——–

2—————–

3—————–

4—————–

5——–D——–

6—————–

7———-B——

8—-R—–R——

9—————–

0—————–

1—————–

2—————–

Note: Column and row indicators are provided to allow easy determination of game-object positions. The indicators are just the last digit of the 0-based column or row index. The largest column and row are equal to the width and height, respectively; since positions are rounded to the nearest integer when drawn, a column position of 15.8 would be rounded up to 16.

Field elements are printed as follows:

Q shows the location of the quarterback

B shows the location of the ball (not shown when the ball is still held by the quarterback)

D shows the location of each defender (only 1 in this example)

R shows the location of each receiver (2 in this example)

– shows an unoccupied space on the field

After the field is printed, each object in the game will perform a move. If, at the end of the round, the game is still ongoing, play continues with another round.

<h2>Ending the Game</h2>

All objects in the game continue to move as described above. The game ends when one of the following conditions occurs in your program:

While the quarterback has possession of the ball, a defender ends their turn occupying the same (rounded integer) location as the quarterback (this is a <em>sack</em> in TefBall)

When the ball has been thrown, a defender ends their turn occupying the same (rounded integer) location as the ball (this is an <em>interception</em> in TefBall)

When the ball has been thrown, a receiver ends their turn occupying the same (rounded integer) location as the ball (this is a <em>reception</em> in TefBall)

After a full round is complete (i.e. all players have moved), if the ball has been thrown and has reached its final (actual floating point, non-rounded) destination, and no receiver or defender occupies the same (rounded integer) location (this is an <em>incomplete pass</em> in TefBall)

Note that games don’t only end when a full round is complete. The game can end whenever any of the above criteria is met, even if some objects have not yet moved.

<h1>User Interaction</h1>

There is no user interaction for this project. Instead, we have provided two test files,

PlayTefball1.java and PlayTefball2.java , that contain main() functions used to to test the other classes. You should develop your own test files as well – the provided ones do not fully test your program. When grading, we will utilize PlayTefball classes that cover a wider range of test cases, so be sure to develop your own tests to ensure your implementation performs as expected in all cases.

We have also included the expected output from running the two test files. Your implementation must match the output exactly. Use the command-line diff tool or an online diff checker to make sure this is the case.

<h1>Error Handling</h1>

In an attempt to make this programming project less work, most error handling will not be required. You can safely assume we will <strong><em>not</em></strong> test your program with the following cases:

Placing players outside the valid field size (setting location, destination, etc., to a value less than 0 or greater than the specified height or width)

Ridiculous speeds (negative values, zero, etc.)

Duplicate or invalid player indices (adding a receiver at index 4 and then adding a defender at index 4, adding a player at index -1, etc.)

Some error checking <em>is</em> required, though. Specifically, in order to play a game of TefBall, the user (the person who wrote the main() function) must add exactly one quarterback and exactly the number of players they indicated would play in the playing field’s constructor. These criteria must be checked inside your implementation of the checkIsValidGame() method of PlayingField .

There certainly is a lot of error checking that could (and really should) be done for a project like this. However, you may assume that, except for the specific error checking described for

checkIsValidGame() , the user will do what they are supposed to.

<h1>Required Interface</h1>

You must implement a specified interface so that users can write main() functions to test your version of TefBall. Unlike Project 1, however, you are free to make as many additional members (data and/or functions) as you need to complete the project. Some of your grade will be based on your design, so think carefully about where attributes or functionality belong, and make sure you don’t duplicate code more than absolutely necessary. When grading, we will be looking for inappropriate members, methods at the wrong level of the inheritance tree, etc. An example of an inappropriate member is having a variable called j in a class simply because many methods need a loop counter. Since that value doesn’t describe an attribute of the object at all, it should <em>not</em> be a member variable, even if that means declaring a loop variable in 12 different member functions.

The following is the required interface you must develop. You must follow this exactly, including class and method names. However, you may add other data attributes, methods, classes, enumerated types, etc., as needed by your implementation. The additional items you add will not be utilized directly by the author of main() .

<h2>Class: PlayingField</h2>

An object of this class will be used to represent the TefBall playing field that objects in the game move around on as described. Read through the documentation in the starter code for what you should implement. You must adhere to the interface provided in the starter code.

<h2>Enum: GameResultEnum</h2>

A list of possible outcomes from a round of Tefball. The possible values are: ONGOING , SACK ,

INTERCEPTION , RECEPTION , and INCOMPLETION . While the enum definition will likely be short, you must put the definition in its own Java source file named GameResultEnum.java .

<h2>Player-Type Classes: Quarterback , Receiver , Defender</h2>

You should define a class for each type of player. These classes allow you to instantiate player objects that participate in the game. Each player class has a unique implementation of a method named performMove() . You may use whatever parameters you need for this method.

<h3>A Base Player Class</h3>

While the individual player type classes have different implementations of performMove() (and potentially other methods too), the interface is common across different player types. Therefore, you’ll need to set up an inheritance tree and ensure the common interface is defined at a base class level (in Player or above). Polymorphism must be used to a full extent in this way, as this is the primary learning goal for this project.

You may find it appropriate to introduce additional base classes for interfaces and functionality that is common among other classes (e.g players and non-players).

<h1>Movement in the Tefball Simulation</h1>

All objects that move in TefBall move the same way. To move, first determine the object’s 2D vector of travel by subtracting its current location from its destination location. Next, make this 2D vector be a unit vector (with a magnitude of 1.0) by dividing the vector elements by the total length of the 2D vector. At this point, you have a unit vector describing the direction that the object will travel. Multiplying the unit vector by the object’s speed will indicate how far, and in which direction, the object could travel on its next turn. To ensure your objects move in the same way as the objects in our solution do, be sure to follow this algorithm when developing your solution.

Movement Example: Let’s say a Receiver starts its turn at a position of (4.0, 4.0) having a destination of (2.0, 6.0), and runs at a speed of 1.4143. The receiver’s movement would be performed as follows:

Calculate direction: destination – current = (2.0, 6.0) – (4.0, 4.0) = (-2.0, 2.0)

Compute direction unit vector (this is the step one would take if speed were exactly 1.0):

Direction length: length(dirVec) = sqrt(-2.0 * -2.0 + 2.0 * 2.0) = 2.828427

Direction unit: dirVec / dirLength = (-2.0, 2.0) / 2.828427 = (-0.7071068, 0.7071068)

Step for turn: dirUnit * speed = (-0.7071068, 0.7071068) * 1.4143 = (-1.0, 1.0)

Location after turn: current + stepForTurn = (4.0, 4.0) + (-1.0, 1.0) = (3.0, 5.0)

A game object never overshoots its destination. If the movement calculated above would take it past its destination, the object stops at its destination instead.

An object only performs one action in each turn. Specifically, a quarterback does not throw the ball until the turn <em>after</em> they reach their destination. (If a quarterback’s destination is the same as their initial location, they don’t throw the ball until their second turn.) Similarly, a receiver does not start moving to their final destination until the turn <em>after</em> they reach their intermediate destination. (If the receiver’s starting and intermediate locations are the same, they don’t move toward their final destination until their second turn.)

<h1>Requirements, Restrictions, and Clarifications</h1>

<strong>You may <em>not</em> have any references declared (local or member) to be of any specific player type. For example, you are not allowed to declare a reference to a </strong><strong>Quarterback , etc. (Remember, we’re making use of polymorphism here.) You may use the </strong><strong>Quarterback constructor, but the resulting object cannot be referred to by a </strong><strong>Quarterback reference.</strong>

You may, however, declare reference(s) to a Ball if this helps, as it is not a player type.

You may also maintain a specific reference to the quarterback, but the reference must be of Player type.

<strong> You may <em>not</em> use type casting to cast base class references to subclass types, </strong><strong>instanceof , or any other approaches to try to circumvent the polymorphism requirement.</strong> You may not have “if/else if” conditionals that say something along the lines of “if the type of the object is Quarterback then perform some action that is Quarterback-specific, else if the type of the object is Receiver then perform some action that is Receiver-specific”, etc.

Some examples of practices that subvert polymorphism:

Keeping track of different player types in different data structures (a Player reference to a quarterback is fine though, as mentioned above).

Using a player’s character representation to determine what kind of player it is.

Performing an action that is specific to a type of player outside of the class for that player.

Instead, you should introduce abstract methods in the base Player class and override them in derived classes to perform type-specific actions.

<strong> Any violation of the two restrictions above will be considered an invalid solution to the project, and you will receive few or no points for your project.</strong>

The main objective for this project is to gain experience in designing and writing code that is properly object-oriented. Subverting the polymorphism requirements means that you did not meet the learning goals for the project, so you will not receive credit.

There is no requirement that the number of defenders equals the number of receivers, or that there are any receivers or defenders. TefBall can be played with as little as a quarterback and no other players (although it’s not very interesting that way).

Players can start at any location within the field – there is no concept of a “line of scrimmage” in TefBall.

There is no concept of the ball’s altitude in this 2D version of TefBall. Anytime the ball and a defender or receiver occupy the same space, the game is over, regardless of whether the ball is in mid-flight, etc.

The final state of the field is never drawn to the screen. When an end-of-game criteria is met, the game ends and the result is reported, but the final state of the field will not be visualized.

<h1>Final Thoughts</h1>

This project is fairly involved, but it does not necessarily require a lot of code. There is no requirement for number of lines of code, but just to give you a feel, my implementation has about 300 lines of code, excluding comments and blank lines. It’s fine if you have more or less than that, but if you find you’re writing 1200 lines of code, you may be making it more complicated than it needs to be.