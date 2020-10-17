# PACMAN - Multi Agent Search
## Question 1 : Reflex Agent
1. Giải thích
- Input : curent gameState, action
- Ouput : best score at action
- minFoodist : best score at action, default : Infinity
2.  PseudoCode
 ```
    function eval (gameState, action) : 
    pos = gameState
        for ghost in listGhost:
            if Distance(pos, ghost) <= 1
                => return -infinity
        for food in List Food : 
            minFoodList = min ( Distance(pos, food) )
        return currentScore + 1/minFoodList;
 ```
## Question 2 : Minimax
1. Giải thích
- Input : Curren gameState, curent depth, agent (max | min)
- Output: Action best at Evalaution
2. PseudoCode
    ```
    depth = 0, agent = true | 1;
    function minimax(gameState, depth, agent)  : 
        node = gameState.getSuccessor();
        if depth = 0|| GameWin || GAMELOSE
            return  STOP
        if maximizingPlayer then
            value := −Infinity
            for each child of node do
                value := max(value, minimax(child, depth − 1, FALSE))
            return value
        else (* minimizing player *)
            value := +Infinity
            for each child of node do
                value := min(value, minimax(child, depth − 1, TRUE))
        return value
    ```
## Question 3 : Alpha-Beta Pruning
1. Giái thích
- Input : gameState, alpha, beta, depth, agent (max|min)
- Output : best Action
2. PseudoCode
 ```
 function alphabeta(gameState, depth, alpha, beta, agent)
    nodes = getSuccessor();
   if depth = 0|| GameWin || GAMELOSE then
        return STOP
    if agent then
        value := −Infinity
        for each child of node do
            value := max(value, alphabeta(child, depth − 1, alpha, beta, FALSE))
            alpha := max(alpha, value)
            if alpha ≥ beta then
                break 
        return value
    else
        value := +Infinity
        for each child of node do
            value := min(value, alphabeta(child, depth − 1, alpha, beta, TRUE))
            beta := min(beta, value)
            if beta ≤ αlpha then
                break 
        return value
 ```
 ## Question 4 : Expectimax
1. Giải thích
- Input : Curren gameState, curent depth, agent (max | min)
- Output: Action best at Evalaution
2. PseudoCode
    ```
    depth = 0, agent = true | 1;
    function minimax(gameState, depth, agent)  : 
        node = gameState.getSuccessor();
        if depth = 0|| GameWin || GAMELOSE
            return  STOP
        if maximizingPlayer then
            value := −Infinity
            for each child of node do
                value := max(value, minimax(child, depth − 1, FALSE))
            return value
        else (* minimizing player *)
            value := +Infinity
            for each child of node do
                value := min(value, minimax(child, depth − 1, TRUE))
        return value
    ```
## Question 5 : Evaluation Function
1. Giải thích
- Input : Curren GameState
- Ouput : betterEvaluation
2. PseudoCode
```
    Function betterEvaluationFunction(gameState) : 
        for ghost in shostList :
            if Distance(pos, ghost) return - Infinity
        for foodPosition in foodPositions:
        foodDistance = util.manhattanDistance(pacmanPosition, foodPosition)
        if foodDistance < minDistance:
            minDistance = foodDistance
            setMinDistance = True
        if setMinDistance:
            evalNum += minDistance
        evalNum += 1000*currentGameState.getNumFood()
        evalNum += 10*len(currentGameState.getCapsules())
        evalNum -= 10*currentGameState.getScore()
        return evalNum*(-1)
```