
**Introduction:**

Introduction: In 1987, Brooks [1] publish an essay ‘No Silver Bullet: Essence and Accidents of Software Engineering’, which proposes an influential perspective that there is not a single technological and management breakthrough can dramatically improve the software development. Brooks pinpoints two difficulties, namely essence and accidents. The essence difficult, such as complexity, conformity, changeability and invisibility, can not be eliminated by any approaches, while the accident difficult, such as inefficient programming languages, can be mitigated to some extent. In addition, he discussed the influence of past breakthroughs, such as high-level language and time-sharing techniques, and promising future tools, such as artificial intelligence and object-oriented languages. He believed these advancements are only capable of incrementally improving software engineer, instead of revolutionarily.



**Identified Key Challenges:**



**Changeability:** Changeability is caused because 1) software engineering is a continuously evolving subject due to changing requirement, technologies and environments; 2) the physical machines on which the software systems are based may change, leading to the new requirement to change the implementation of software system. In addition to the challenge of changing itself, additional maintenance also poses a key challenge.

**Invisibility:** Obviously, software system is invisible. Architects can sue blueprints and hardware engineers can examine circuit diagrams, which are intuitively and straightforward to help understand. However, as for software system, there is not an ideal diagram that can clearly and easily represent the whole system. This forces software engineers to work with abstract constructs without any clearly visual and physical diagrams. Therefore, invisibility causes all engineer need to conduct abstract reasoning and development.



**Two Selected Design Pattern and Application:**


Brooks pointed out that the inherent properties of software development are complexity, conformity, changeability and invisibility. These features are difficult to address with a single technological breakthrough. Therefore, it is inevitable for engineers to solve these problems when developing software. Among all design patterns, builder pattern and adapter pattern can be used to overcome these inherent properties. The **builder pattern** can be used to solve the complexity and changeability of software development. The **adapter pattern** can be used to solve conformity and invisibility in software development.


**Case Study Analysis:**


Game development is a comprehensive software project. The large size of the game makes it difficult to complete in a short time, and diverse game performance requires close teamwork by people who are good at different fields. Complex game logic brings great challenges to the optimization and testing of the code. The need for update makes the logic code must be brief and readable. At the same time, it should have a large space for expansion. These challenges create a strong need for good and clean code in game development. The knowledge of software engineering, especially design patterns, can greatly optimize code. Therefore, we will use design patterns to optimize a top-down TPS mini-game made by our team, and analyze the benefits of these optimizations to the game.

Implementation of Generic TankBuilder.
Figure 1: Implementation of Generic TankBuilder.

This optimization solves the following software development challenges:

Complexity: Breaking character building down into discrete steps (such as setting health and abilities) gives us the flexibility to manage the data of character generation and to build different characters in a distributed way as the player faces different game scenarios. This pattern reduces coupling between modules, which is consistent with Brooks' emphasis on managing complexity through structured decomposition.

Changeability: The extension system can support new role attributes. When a role needs new attributes to enrich its functionality, it can simply write corresponding methods in its subclasses without modifying other classes. At the same time, the system also simplifies the construction of new role types by subclassing TankBuilder, which conforms to the open-closed principle. This avoids modifying existing code, thereby minimizing the risk of regression.

Case II: Adapter Pattern in Audio System Integration
Subsequent games need to be compatible with multiple audio backends, including Unity's native audio engine and FMOD, each with different playback and volume control APIs. Direct integration prevents flexibility by tying the core logic tightly to a specific implementation. To solve this problem, we designed the framework as shown in Figure 2.

Adapter pattern implementation in Audio System Integration

Figure 2: Adapter pattern implementation in Audio System Integration

We define the IAudioSystem interface and use two adapter classes (UnityAudioAdapter and FMODAudioAdapter) to implement this interface, converting generic calls to back-end specific operations. In this way, we only need to modify the adapter class reference, we can switch different audio backends as output, thus achieving a more concise setting switching audio function. For example, you can map PlaySound methods to Unity's AudioSource component by changing the reference to audioSystem to UnityAudioAdapter and the name to FMODAudioAdapter to interface with FMOD's event system. This allows the client code to interact only with the abstract interface, as shown in Figure 3.

The abstract interface of IAudio System.

Figure 3: The abstract interface of IAudio System.

**Reference**

[1] F. P. Brooks Jr., "No Silver Bullet: Essence and Accidents of Software Engineering," IEEE Computer, vol. 20, no. 4, pp. 10-19, Apr. 1987.

