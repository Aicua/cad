# CAD Command Reference for AI Assistant

## CLI COMMAND FORMAT

Use this CLI syntax for CAD commands:

## BASIC OBJECT CREATION

### Create Object
```
obj ObjectName
```

### Add Lines to Object
```
ObjectName.line LineName Length
```

### Set Line Points
```
LineName.start(x,y,z)
LineName.end(x,y,z)
```

### Connect Lines
```
Line1.end = Line2.start
```

### Extrude Object
```
extrude ObjectName Height
```

## EXAMPLES

### Simple Cube
```
obj cube
cube.line edge1 5
cube.line edge2 5
cube.line edge3 5
cube.line edge4 5
edge1.start(0,0,0)
edge1.end = edge2.start
edge2.end = edge3.start
edge3.end = edge4.start
edge4.end = edge1.start
extrude cube 5
```

### Simple House
```
obj house
house.line wall1 10
house.line wall2 8
house.line wall3 10
house.line wall4 8
wall1.start(0,0,0)
wall1.end = wall2.start
wall2.end = wall3.start
wall3.end = wall4.start
wall4.end = wall1.start
extrude house 3
```

### Triangle
```
obj triangle
triangle.line side1 6
triangle.line side2 6
triangle.line side3 6
side1.start(0,0,0)
side1.end = side2.start
side2.end = side3.start
side3.end = side1.start
```

### Rectangle
```
obj rect
rect.line top 8
rect.line right 5
rect.line bottom 8
rect.line left 5
top.start(0,0,0)
top.end = right.start
right.end = bottom.start
bottom.end = left.start
left.end = top.start
```

### L-Shape
```
obj L
L.line line1 3
L.line line2 2
L.line line3 1
L.line line4 2
L.line line5 2
L.line line6 3
line1.start(0,0,0)
line1.end = line2.start
line2.end = line3.start
line3.end = line4.start
line4.end = line5.start
line5.end = line6.start
line6.end = line1.start
```

## RULES FOR AI

1. **Always use unique names** for objects and lines
2. **Use realistic dimensions** (typically 1-20 units)
3. **For closed shapes**: Connect all lines in sequence
4. **For 3D objects**: Create 2D profile first, then extrude
5. **One command per line**
6. **Return only CLI commands, no explanations**

## COMMAND PATTERNS

- **obj name**: Creates new object
- **object.line name length**: Adds line to object
- **line.start(x,y,z)**: Sets line start point
- **line.end(x,y,z)**: Sets line end point
- **line1.end = line2.start**: Connects two lines
- **extrude object height**: Makes 3D from 2D profile

## COORDINATES

- Use (x,y,z) format for 3D points
- Use (x,y,0) for 2D points
- Example: wall1.start(0,0,0)
- Example: wall1.end(10,0,0)

## STEP-BY-STEP PROCESS

1. Create object: `obj name`
2. Add lines: `name.line line1 length`
3. Set start point: `line1.start(x,y,z)`
4. Connect lines: `line1.end = line2.start`
5. Close shape: `lastLine.end = firstLine.start`
6. Extrude if needed: `extrude name height`
