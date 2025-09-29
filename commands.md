# CAD Command Reference for AI Assistant

  ## BASIC SHAPES

  ### Triangle
  ```json
  {"action":"createTriangle", "id":"triangle1", "color":"#ff0000"}

  Cube

  {"action":"createCube", "id":"cube1", "size":3.0, "color":"#00ff00"}

  Sphere

  {"action":"createSphere", "id":"sphere1", "radius":2.0, "color":"#0000ff"}

  Line

  {"action":"createLine", "id":"line1", "length":5.0, "color":"#ffff00"}

  ADVANCED SHAPES

  Bezier Spline

  {"action":"createBezierSpline", "id":"spline1", "controlPoints":[{"x":-1,"y":0,"z":0},{"x":1,"y":1,"z":0}],
  "color":"#ff00ff"}

  OpenCASCADE Cube

  {"action":"createOccCube", "id":"occ_cube1", "width":3, "height":3, "depth":3, "color":"#00ffff"}

  SKETCHING

  Sketch Profile (2D shapes for extrusion)

  {"action":"createSketchProfile", "id":"profile1",
  "lines":[{"start":{"x":0,"y":0},"end":{"x":5,"y":0}},{"start":{"x":5,"y":0},"end":{"x":5,"y":3}},{"start":{"x":5,"y":
  3},"end":{"x":0,"y":3}},{"start":{"x":0,"y":3},"end":{"x":0,"y":0}}]}

  3D OPERATIONS

  Extrude (Make 2D profile into 3D)

  {"action":"extrudeSolid", "id":"extruded1", "profileId":"profile1", "height":5.0, "color":"#888888"}

  Revolve (Spin profile around axis)

  {"action":"revolveSolid", "id":"revolved1", "profileId":"profile1", "angle":360, "color":"#888888"}

  BOOLEAN OPERATIONS

  Subtract (Cut one object from another)

  {"action":"booleanSubtract", "targetId":"object1", "toolId":"object2"}

  Fillet (Round edges)

  {"action":"filletSolid", "targetId":"object1", "radius":0.5}

  EXAMPLES

  Simple House

  {"action":"createSketchProfile", "id":"house_base", 
  "lines":[{"start":{"x":0,"y":0},"end":{"x":10,"y":0}},{"start":{"x":10,"y":0},"end":{"x":10,"y":8}},{"start":{"x":10,
  "y":8},"end":{"x":0,"y":8}},{"start":{"x":0,"y":8},"end":{"x":0,"y":0}}]}
  {"action":"extrudeSolid", "id":"house", "profileId":"house_base", "height":3.0, "color":"#8B4513"}

  Tower with Roof

  {"action":"createCube", "id":"tower_base", "size":4.0, "color":"#A0522D"}
  {"action":"createTriangle", "id":"roof", "color":"#8B0000"}

  Curved Vase

  {"action":"createBezierSpline", "id":"vase_profile", 
  "controlPoints":[{"x":0,"y":0,"z":0},{"x":3,"y":2,"z":0},{"x":2,"y":5,"z":0},{"x":4,"y":8,"z":0}], "color":"#00ffff"}
  {"action":"revolveSolid", "id":"vase", "profileId":"vase_profile", "angle":360, "color":"#888888"}

  RULES FOR AI

  1. Always use unique IDs for each object
  2. Colors in #rrggbb hex format (red: #ff0000, green: #00ff00, blue: #0000ff)
  3. For buildings/complex shapes: Create sketch profile first, then extrude
  4. For round objects: Create profile, then revolve
  5. Use realistic dimensions (typically 1-20 units)
  6. One JSON command per line
  7. Return only JSON commands, no explanatory text

  COMMON PATTERNS

  - Simple shapes: Direct creation (createCube, createSphere)
  - Buildings: createSketchProfile → extrudeSolid
  - Cylindrical objects: createSketchProfile → revolveSolid (360°)
  - Complex shapes: Multiple objects + booleanSubtract
  - Organic shapes: Use createBezierSpline
