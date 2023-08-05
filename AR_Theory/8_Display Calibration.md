# Display Calibration

#inside-out #outside-in #HMD #perspective-n-point 
## Single Point Active Alighment Method (SPAAM)

estimating P directly:
1. Given: 3D Points in a tracker target
2. Given: Corresponding 2D Points on Screen
3. Task: User Translates/Rotates Display  so crosshair aligns with a known 3D Point

→ Calibration when HMD is moved
→ Calibration with new user
→ easy to implement
## Display Relative Calibration (DRC)

1. Find Markers displayed inside the Display
2. Project 2D Points into 3D using known Camera Calibration

→ more advances but no better results than SPAAM
→ more complicated and elaborate setup
## INDICA (Interaction-free Display Calibration)

1. Detect Eye Position automatically (using Inside-Camera)

→ no user-interaction required (no user-error)
→ continuous recalibration possible

