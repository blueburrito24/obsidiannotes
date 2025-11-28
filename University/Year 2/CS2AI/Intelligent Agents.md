An intelligent agent is a reactive component of AI, it perceives and reacts to its environment.
An agent is anything that can perceive or ==sense== its environment and act upon the environment or ==actuate==.
==Percept== = agent's perceptual input at a given time.
==Percept== sequence" history of everything the agent has perceived.
An agent's ==action== at any time depends on the percept sequence observed.
==Agent program== run in cycles of :
- Perceive
- Think
- Act rationally
Agents often ==assume== - they perceive their own actions but not the effects.
![[{70B7DBCD-83B5-4E46-A66D-A3B98D4DA36C}.png]]
==Sensor== is a device that detects change in an environment and directs the information to other components/devices.
==Actuator== is a component that converts energy into motion, such as an electric motor or a gear.

"Human agent"
- eyes, ears and other organs for sensors
- hands, legs, mouth etc for actuators
"Robotic agent"
- cameras and infrared range finders for sensors;
- various motors for actuators
"Software agent"
- Keystrokes, file contents, received network packages as sensors
- Screen display, files and sent network packets as actuators

Think of a roomba for an example of an agent!!
![[{1B2A12F8-A787-40AD-AA52-4F4E6DAC6A89}.png]]

## Agent Functions and programs
Agent behaviour is described by the agent function, which maps percept histories to actions,
- f:P* -> A
We need to implement a rational agent function concisely AKA design an agent program.
==Agent = Agent program + Architecture==
"Architecture" is a computing device that provides the sensors and actuators.
"Agent program" takes the percept as input from the sensors and returns an action to the actuators.
Agent programs take current percept as input whereas agent function takes the whole percept history.
Agents need to remember the entire percept sequence.