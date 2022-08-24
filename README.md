# Womanium Quantum Hackathon 2022

## General Information
   *Team Name*       -- QUI

   *Team members*    -- Alentev Igor, m8dotpie#6577, 44410570, i.alentev@innopolis.university
                        Domrachev Ivan, domrachev03#8886, 28687492

   *Pitch Presenter*--  Domrachev Ivan

   *Challenge name* --  Humans-vs-Quantum-Computers---Ibm

## Project Overview
Our project is **Quantum Trap the Cat Game**. You are given a hexagonal field with a cat spawned somewhere in the middle. The cat wants to escape the field by reaching its end. Your task is to stop the cat by surrounding it with dogs. Simply click on selected hexagon and the dog will immidiately appear. However, this cat is not the ordinary, but **quantum** one. Anytime he wants, he can make a superposition move and appear in two places simultaneously.

More strictly, this is a turn based game. Each step you can either spawn an obstacle in the selected hexagon or make the measurement of the cats state. The cat each step can either make an ordinary step in the desired (not blocked) direction, or make a superposition step into multiple directions simultaneously. To win, you should isolate the cat from the borders of the field.

## Game requirenments
The game is just a jupyter notebook built to run on any machine. The only requirements are to install used libraries. It was heavilly tested on IBM Quantum Lab runtime. 

## Implementation Details
Our project is built as a monolitic jupyter notebook. It is only necessary to download the sprites of the cat and the dog for the proper functioning. 

Due to the lack of computing power at Quantum Lab it was decided to run the game completely on simulator
### Stack
- ipycanvas
- ipywidgets
- qiskit
### Internals Overview
The game consists primarily of several classes. The most important of them:
1. GameEngine - game engine class which manages drawing to the canvas, AI and field management and cat simulation
2. SimulatorCat - a cat class capable of making entangled and superposition moves as well as measuring itself
3. AI - a class specialised on finding and prioriting the winning paths on the field for further traversing
### Quantumm Internals
Even though the cat is ran on the simulated hardware, it is completely quantum based. The main feature of the cat is quantum coordinates.
Quantum coordinates allow to entangle the position of the cat properly depending on the moves. It is much more elegant and efficient solution then straightforward encoding of the possible states. Moreover, this behaviour allows us to create a high level of abstraction, where a usde is not required to understand the internals of the cat, but just call a simple self-descriptive and well-documented methods. Finally, quantum coordinates are absolutely necessary to create quantum AI for this game.
### Classicals Internals
In this project we used five different coordinate systems. Each coordinate system is perfectly designed to solve one specific problem.
1. **Canvas coordinates** - default coordinates used in canvas to draw and layout widgets
2. **Complex plane** - complex plane is perfect for constructing different objects, such as hexagons using complex surface transformations
3. **Field coordinate system** - a system used as a bijection onto the corresponding rectangular table to store and update objects information and simplify objects iteration and drawing into the canvas
4. **Ai coordinate system** - AI uses its own variation of a coordinate system, perfectly polished for table traversal and conversion into the graph.
5. **Quantum cat coordinates** - the cat uses its own coordinates which solve the issue of moves encoding into quantum coordinates

Graph algorithms and euristics are used to traverse and find specific paths which will increase the success of the player which follows these paths. Tweaking these algorithms allowed us to create a non-trivial AI which can seriously challenge the player during the game, even though the game looks more adorable rather than challenging.

Game engine uses mathematical theory behind analytical and vector geometry to detect and classify user interaction with the game objects

## Usecases
The perfect usecase of this project is the demonstration of the capabillities of quantum computer to the begginners or even children in the world of quantum. Minimalistic and simplistic design in cope with the real simplicity of the rules makes this game much easier to understand and beat than, for example, quantum chess.

## Issues
- The cat runs on simulator
- IBM Quantum Lab does not properly run ipycanvas
- Low performance of canvas on IBMQ Lab
- After a few games AI is predictable
- Even though AI is predictable, it is still unbeatable

## Further Development
- [ ] Migrate to the real hardware
- [ ] Improve ipycanvas performance
- [ ] or Migrate to other platform
- [ ] Improve Artificial Intelligence
