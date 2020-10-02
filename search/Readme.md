# Pacman

Bài tập AI - Trí tuệ nhân tạo
Nguyễn Thái Tiệp - 18021277

## Algorithm

### Question 1 : Finding a Fixed Food Dot using Depth First Search
    Chú thích
    ```
    actions : quá trình đi
    node : đỉnh đang xét
    visited : các đỉnh đã xét
    direction : các đỉnh kề
    child : đỉnh con gần nhất
    ```
    2. Giải thuật (mã giả) :
        ```Input = (startState, endState)
        Box = new Stack()
        Box push (node = StartState, actions = null, visited = null)
        while Box is not Empty
            get node, actions, visited from Stack pop
            check(endState == node) => return action
            for each child, direactions in getSuccessors(node)
                Box push (node = child, actions = actions + directions, visited = visited + child)
        return []
        ```
        
### Question 2 : Breadth First Search
    1. Giải thuật (mã giả) :
        ```Input = (startState, endState)
        Box = new Queue()
        Box push (node = StartState, actions = null, visited = null)
        while Box is not Empty
            get node, actions, visited from Stack pop
            check(endState == node) => return action
            for each boxItem in getSuccessors(node)
                Box push (node = child, actions = actions + directions, visited = visited + child)
        return []
        ```

### Question 3 : Varying the Cost Function
    1. Chú thích
    - Sử dụng priotyQueue, ưu tiên cost
    - Curcost : Chi phí hiện tại đi từ đầu tới điểm đang xét
    - cost : Chi phí từ điểm hiện tại tới điểm đang xet
    2. Giải thuật
    Input  = (startState, endState)
    ```Box = new PriorityQueue
    Box push ((node = startState, actions = null, curSost = 0), curCost = 0)
    path = []
    while Box is not Empty : 
        get node, actions, Curcost form Box pop
         check(node == endState) => return actions
         check(node is in path) => continue
         path.add(node)
         
         for each child, actions, cost in getSuccessors(node)
            Box.push ((node = child, actions += directions, curCost += cost), curCost += cost)
    return []```

### Question 4 : A* search
    1. Chus thích
     - heuristic(child, problem) : trả về số bước ngắn nhất từ điểm hiện tại đến đích
    2. Giải thuật
    Input  = (startState, endState)
    ```
    Box = new PriorityQueue
    Box push ((node = startState, actions = null, curSost = 0), curCost = 0)
    path = []
    while Box is not Empty : 
        get node, actions, Curcost form Box pop
         check(node == endState) => return actions
         check(node is in path) => continue
         path.add(node)
         
         for each child, actions, cost in getSuccessors(node)
            Box.push ((node = child, actions += directions, curCost += cost), curCost += cost + heuristic(child, problem))
    return []
    ```

### Question 5 : Finding All the Corners
    1. Chú thích
     - startState =  return (startingPosition, [])
     - isGoalState = return 
        ```Input = (node, visitedCorner)
        node = state[0]
        visitedCorners = state[1]
        if node in corners:
            if not node in visitedCorners:
                visitedCorners add node
            return len(visitedCorners) == 4
        return False```
    - corner = [(x = 1, y = 1),(x = 1, y = wall.height -2),(x = wall.width -2, y = 1),(x = wall.width - 2, y = wall.heigth - 2)]
    2. Giải thuật
    -getSuccessors
    ``` Input = (node, visitedCorner)
    successor = []
    for each  edge  in [leftEges, rigth, above,under]
        check(hasEdge == false)=> continue
        check(edge in corners ) => 
            check(edge not in corners )=> visitedCorner add edge
        successor add (node =  ( egde, successorVisitedCorners = visitedCorner), direction = action, cost = 1 )
    return successor```
            
### Question 6 : Corners Problem: Heuristic
    1. Chú thích
    - Sử dụng thuật toán A*, điều kiện ưu tiên : chi phí (cost)
    - UnvistedConner :Các conner chưa được thăm
    2. Giải thuật
    - Input = (node, VisitedConners)
    - currentPoint = node
    - sum = 0
    ```while VisitedConners is not Empty
        get MinConner, MinDistance from unvisitedCorners (consident : min(distance = Distance(currentPoint, corner)) )
        sum += MinDistance
        currentPoint = MinConner
        unvisitedCorners.remove(MinConner)
    return sum```
### Question 7 : Eating All The Dots
    1. Chú thích
        - Sử dụng thuật toán A*, ưu tiên với chi phí (cost)
    2. Giải thuật
    - Input = (position,foodGrid)
    - sum = 0
    - currentPoint = node
    ```while VisitedConners is not Empty
        get MinConner, MinDistance from unvisitedCorners (consident : min(distance = Distance(currentPoint, corner)) )
        sum += MinDistance
        currentPoint = MinConner
        unvisitedCorners.remove(MinConner)
    return sum```
    
### Question 8 : Suboptimal Search
    1. Chú thích
        - Sử dụng thuật toán A*, ưu tiên với chi phí (cost)
    2. Giải thuật
    - Input = (position,foodGrid)
    - sum = 0
    - currentPoint = node
    ```
    while VisitedConners is not Empty
        get MinConner, MinDistance from unvisitedCorners (consident : min(distance = Distance(currentPoint, corner)) )
        sum += MinDistance
        currentPoint = MinConner
        unvisitedCorners.remove(MinConner)
    return sum
    ```
