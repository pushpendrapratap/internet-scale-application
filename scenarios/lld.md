1.  **Design a pen:**

        requirement gathering:
        -----------------------
        - pen should provide write fluently
        - anything with nib and filled with ink will be a pen (chalk, charcoal, pencil, etc. not allowed)
        - two types of pen:
        	- ball pen
        	- ink pen
        - diff. write behaviour for both pen
        - assumption: proper surface will be used bu yser to write
        - refill feature -> ink shoild decrease with writing
        - criteria for reducing ink:
        	- pen is credited with x units of ink and 1 unit will be deducted with each write (i.e., 1 unit ink per char).

        classes:
        ----------------
        - pen:
        	- ball pen
        	- ink pen
        - nib
        - ink

        relationships:
        ---------------------
        - pen -> inheritance
        - pen - nib -> composition i.e., each pen will have nib or nib can't exist without pen
        	- that means if pen is destroyed than nib also needs to be destoyed
        - ink - ink pen - refill -> aggregation

        class diagram:
        -----------------------
        - pen:
        	- some attributes
        	- write()
        	- refill()
        - ink pen:
        - ball pen:
        - nib:
        - refill:
        - ink:

        - writeable (interface): in case we want to include chalk, pencil, etc.
        	- write()
        - refill_strategy: in case we want to include sketch, etc.

        NOTE:
        -----------
        - composition: one entity can't exist independently (filled arrow/diamond) and relationship will be unidirectional
        - aggregation: both diff. entities can exist independenlty (empty arrow/diamond), relationship will be bidirectional

2.  **Design a tic-tac-toe:**

        requirement gathering:
        -----------------------
        - nXn board - 2 player game
        - 'x' and 'o' are the only symbol
        - assign symbols to user randomly
        - 'x' starts first

        classes:
        ----------------
        -   game:
        -   board:
        -   player (it will be abstract class because it has symbol as attribute and no instance of it will be needed to create. Also, it can't be interface because it has symbol as attribute):
        	-   human
        	-   bot
        -   symbol:
        -   strategy (abstract class):

        class diagram:
        ---------------------
        -   player:
        	-   symbol
        	-   make_move()

        relationship:
        ----------------------------
        -   game - board -> composition
        -   symbols as ENUM
        -   game - strategy -> composition (strategy pattern)

        NOTE:
        -----------------------------
        -   interface can't have attributes, everything will be static. Also, it allows multiple inheritance
        -   interface has collections of methods. It's group of behavior. usually verb.
        -   abstract class is usually noun
        -   strategy design pattern (usecase - diff. game can have diff. difficulty level e.g., bot vs human, bot vs bot):
        	-   cat - hunting_behavior -> composition
        	-   hunting_behavior (abstract class):
        		-   stalk
        		-   chase
        		-   etc.

3.  **snake and ladder:**

        requirement gathering:
        --------------------------------
        - dimension of board can vary (nXn)
        - provide board state before start (once game starts, yuo can't change it)
        - no. of dices can vary
        - player type (bot, human, etc.)

        classes:
        -------------------
        - game:
        - player:
        	- position
        - board:
        	- snake (start, end)
        	- ladder (start, end)
        - dice as a service (math.random(), only even or odd random no., etc.) not class

        - game logic: (queue ds is more appropriate)
        	- player 1 rolls dice
        	- find position
        	- is it over for player 1
        - so, game should have queue of players rather than list of players
        - prob(1-6) -> 1/6
          prob(2-12) -> ?
