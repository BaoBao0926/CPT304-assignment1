
**Introduction:**

Introduction: In 1987, Brooks [1] publish an essay ‘No Silver Bullet: Essence and Accidents of Software Engineering’, which proposes an influential perspective that there is not a single technological and management breakthrough can dramatically improve the software development. Brooks pinpoints two difficulties, namely essence and accidents. The essence difficult, such as complexity, conformity, changeability and invisibility, can not be eliminated by any approaches, while the accident difficult, such as inefficient programming languages, can be mitigated to some extent. In addition, he discussed the influence of past breakthroughs, such as high-level language and time-sharing techniques, and promising future tools, such as artificial intelligence and object-oriented languages. He believed these advancements are only capable of incrementally improving software engineer, instead of revolutionarily.

Relevance: The insights proposed in this paper remain a fundamental role in modern software engineering, which help later software engineers distinct the differences between essential and accidental difficulties and cultivate the motivation to design efficient tools and frameworks to work more efficiently. In this paper, one section that discuss the role of great designer highlights the significance of skilled designers and engineers in designing the robust and systematic software systems. Overall, this paper comprehensively discussed essential and accidental difficulties, past breakthroughs, future promising tools and the role of designer, which reject a simple way of “silver bullet” but encourages a disciplined and incremental progress. The idea of Brooks continually guides the development of the software engineering.

**Identified Key Challenges:**



**Changeability:** Changeability is caused because 1) software engineering is a continuously evolving subject due to changing requirement, technologies and environments; 2) the physical machines on which the software systems are based may change, leading to the new requirement to change the implementation of software system. In addition to the challenge of changing itself, additional maintenance also poses a key challenge.

**Invisibility:** Obviously, software system is invisible. Architects can sue blueprints and hardware engineers can examine circuit diagrams, which are intuitively and straightforward to help understand. However, as for software system, there is not an ideal diagram that can clearly and easily represent the whole system. This forces software engineers to work with abstract constructs without any clearly visual and physical diagrams. Therefore, invisibility causes all engineer need to conduct abstract reasoning and development.



**Two Selected Design Pattern and Application:**


Brooks pointed out that the inherent properties of software development are complexity, conformity, changeability and invisibility. These features are difficult to address with a single technological breakthrough. Therefore, it is inevitable for engineers to solve these problems when developing software. Among all design patterns, builder pattern and adapter pattern can be used to overcome these inherent properties. The **builder pattern** can be used to solve the complexity and changeability of software development. The **adapter pattern** can be used to solve conformity and invisibility in software development.



For the **Builder pattern**, it is a creational design pattern. When engineers need to create many approximate projects, they often choose to use builder pattern to avoid creating too many constructors. Using the builder pattern will separate out the code from the constructor and add it to a class named builder [6]. Using the methods in the builder class, the engineers can create complex and diverse objects and representations. Therefore, the builder pattern allows you to build up a complex object step by step. It also allows the user to use a builder class to create multiple different types of objects and representations. So builder pattern has four main advantages:


* In the process of object creation, we can use the methods in the builder class to create an object according to the user's needs.
* Following the Single Responsibility Principle, the complex construction code is separated from the constructor [4].
* You can use the same constructor when creating different objects, improving code reusability.
* New methods can be added to the builder class to meet the new needs of users, without modifying the constructor and affecting other objects.

An **example of the builder pattern** is given in the study of Dhait [4]. In a house customization software, a House object is created to record the user's requirements for a house. Instead of writing a specific constructor for each user, the software created a class called House Builder to create objects. The House Builder has a number of methods that allow you to add different numbers of Windows and different kinds of furniture to an object. By using builder pattern, the house customization software can create complex objects and can meet the different needs of different users


As for the **adapter pattern**, it is a structural design pattern. In software development, there are often interface mismatches, such as when you want to use an existing class or subclass, the interface of the class is not match the one you need [5]. At this point, directly modifying the interface to fit our needs could break some of the code that has already been done and cause some errors. To solve this problem, we can use the adapter pattern and create an adapter class to convert the interface type to meet our requirements. Existing classes can safely use their own interfaces to call methods on the adapter class and send data, the adapter class will then send the data to our software in the format we want [5]. The adapter pattern has four main advantages:

* The single responsibility principle. Separating the interface and data transformation code from the main program code [6].
* The open/closed principle. New adapters can be introduced into the program without breaking existing code [6].
* Improve visibility by decoupling the client from the implementation of the system.
* Improving the maintainability and expansibility of the software [1].

Xiaoxi Chen's research shows the application of adapter design pattern in container ship stowage system [3]. In the container ship stowage system, an adapter named IMin is created and used to connect the system's main program, a class named MyControl, with other entity classes. By using adapter pattern, the system successfully improves the visibility and reusability of the code, enhances the maintainability of the system, and ensures the consistency of the system interfaces.

**Case Study Analysis:**


Game development is a comprehensive software project. The large size of the game makes it difficult to complete in a short time, and diverse game performance requires close teamwork by people who are good at different fields. Complex game logic brings great challenges to the optimization and testing of the code. The need for update makes the logic code must be brief and readable. At the same time, it should have a large space for expansion. These challenges create a strong need for good and clean code in game development. The knowledge of software engineering, especially design patterns, can greatly optimize code. Therefore, we will use design patterns to optimize a top-down TPS mini-game made by our team, and analyze the benefits of these optimizations to the game.


***Case I: Builder Pattern in Tank Construction：***
The game has a variety of characters. The different characters have different attributes, such as health, speed and AI logic (such as whether they are player characters, attack willingness, preferred attack mode, patrol strategy). As the level progresses and special items are used, the character's attributes will change slightly. Therefore, building player and enemy characters requires configuration of different attributes. Traditional methods rely on overloading constructors, resulting in code redundancy. The need to assign all the properties of the built character at the same time increases the difficulty of managing game data. To solve this problem, we designed the following structure as shown in Fig.[1]

We have implemented a generic TankBuilder<T> class for method chains and decoupling of object construction and representation. The TankBuilder<T> class encapsulates core attributes (such as prefabrication, spawn location, and health) and allows derived classes like PlayerTankBuilder and EnemyTankBuilder to extend functionality. For example, PlayerTankBuilder introduces a way to enable melee attacks, while EnemyTankBuilder supports reinforcement and patrol behavior. An example is shown in Fig.[2]


<div align="center">
  <img src="https://github.com/user-attachments/assets/976ee558-bdfb-46cd-8b7f-789f36b70e97" alt="Example1">
</div>

<div align="center">Figure 1: Implementation of Generic TankBuilder.</div>

This optimization solves the following software development challenges:

Complexity: Breaking character building down into discrete steps (such as setting health and abilities) gives us the flexibility to manage the data of character generation and to build different characters in a distributed way as the player faces different game scenarios. This pattern reduces coupling between modules, which is consistent with Brooks' emphasis on managing complexity through structured decomposition.

Changeability: The extension system can support new role attributes. When a role needs new attributes to enrich its functionality, it can simply write corresponding methods in its subclasses without modifying other classes. At the same time, the system also simplifies the construction of new role types by subclassing TankBuilder, which conforms to the open-closed principle. This avoids modifying existing code, thereby minimizing the risk of regression.

***Case II: Adapter Pattern in Audio System Integration***

Subsequent games need to be compatible with multiple audio backends, including Unity's native audio engine and FMOD, each with different playback and volume control APIs. Direct integration prevents flexibility by tying the core logic tightly to a specific implementation. To solve this problem, we designed the framework as shown in Figure 2.

<div align="center">
  <img src="https://github.com/user-attachments/assets/e80abb1b-7c9f-498c-aa66-22d44ed7b726" alt="URL2">
</div>

<div align="center">Figure 2: Adapter pattern implementation in Audio System Integration</div>

We define the IAudioSystem interface and use two adapter classes (UnityAudioAdapter and FMODAudioAdapter) to implement this interface, converting generic calls to back-end specific operations. In this way, we only need to modify the adapter class reference, we can switch different audio backends as output, thus achieving a more concise setting switching audio function. For example, you can map PlaySound methods to Unity's AudioSource component by changing the reference to audioSystem to UnityAudioAdapter and the name to FMODAudioAdapter to interface with FMOD's event system. This allows the client code to interact only with the abstract interface, as shown in Figure 3.

<div align="center">
  <img src="https://github.com/user-attachments/assets/337c2b0e-7239-45cd-8fdc-7964ef1a46f6" alt="Example2">
</div>

<div align="center">Figure 3: The abstract interface of IAudio System.</div>

***Case Summary***
Optimizing existing game code using Builder and Adapter patterns enabled us to mitigate some of the inherent challenges of software engineering. We use Builder pattern to optimize the construction of characters so that the production team can generate characters more freely and provide a flexible solution for creating new characters. Extending existing character attributes solves the problem that modifying a character in the past required modifying all code related to the generation of that character, greatly improving the efficiency of game development and testing. We also used Adapter pattern to optimize the audio system of the game so that the game can be quickly compatible with different audio backends in a simple and consistent way, improving the docking efficiency between different members of the project so that members who are skilled in different areas can focus on their own work. At the same time, the code also uses methods such as singleton mode to manage the core control script to resolve the administrative conflicts that may arise in situations such as scene loading that may generate duplicate controllers.

Both patterns embody the core principles of object orientation.

- Single responsibility: the character generator focuses on object construction, while the adapter isolates audio background interactions.
- Open-closed principle: Extensions (such as new character types or audio engines) require minimal changes to existing code.
- Dependency inversion: high-level modules (such as game logic) rely on abstractions (IAudioSystem) rather than concrete implementations
- Interface isolation: Clients interact with minimal, role-specific interfaces to avoid unnecessary dependencies.

Thus, our optimization by breaking down complexity, encapsulating changeability, and adhering to design principles aligns with Brooks' thesis that progress lies in methodical incremental innovation rather than elusive "silver bullets." Future work could explore hybrid models or quantify productivity gains from larger scale projects.

# Conclusion

In conclusion, we analyze the paper "No Silver Bullet" and its four essential challenges, exactly complexity, conformity, changeability and invisibility. We realize that software system development is difficult and abstract, facing numerous difficulties, and there is no "silver bullet" can revolutionarily address issue. Instead, we only can incrementally develop a more reasonable way to advance the improvement of software engineer. This study demonstrates that the Builder and Adapter patterns provide pragmatic responses to software engineering's inherent challenges. By decomposing complexity, encapsulating variability, and adhering to design principles, these patterns align with Brooks' thesis that progress lies in disciplined, incremental innovation rather than elusive "silver bullets." In addition, we analyze two patterns, exactly builder pattern and adapter patter with corresponding case study. We explain the influence of two design pattern in their application.

# Bibliography
ecai

# Appendix

**Case Study 1**

```csharp
public abstract class TankBuilder<T> where T : TankBuilder<T>
{
    protected GameObject tankPrefab;
    protected Vector3 spawnPosition;
    protected float health;
    protected float speed;
    protected float fireRate;
    protected GameObject bulletPrefab;
    protected float bulletSpeed;
    protected int bulletDamage;

    public T SetPrefab(GameObject prefab)
    {
        tankPrefab = prefab;
        return (T)this;
    }

    public T SetSpawnPosition(Vector3 position)
    {
        spawnPosition = position;
        return (T)this;
    }

    public T SetHealth(float value)
    {
        health = value;
        return (T)this;
    }

    public T SetSpeed(float value)
    {
        speed = value;
        return (T)this;
    }

    public T SetFireRate(float value)
    {
        fireRate = value;
        return (T)this;
    }

    public T SetBulletProperties(GameObject prefab, float speed, int damage)
    {
        bulletPrefab = prefab;
        bulletSpeed = speed;
        bulletDamage = damage;
        return (T)this;
    }

    public abstract GameObject Build();
}

public class PlayerTankBuilder : TankBuilder<PlayerTankBuilder>
{
    private bool hasMeleeAttack;
    private bool hasSprintAbility;

    public PlayerTankBuilder SetMeleeAttack(bool enabled = true)
    {
        hasMeleeAttack = enabled;
        return this;
    }

    public PlayerTankBuilder SetSprintAbility(bool enabled = true)
    {
        hasSprintAbility = enabled;
        return this;
    }

    public override GameObject Build()
    {
        GameObject tank = GameObject.Instantiate(tankPrefab, spawnPosition, Quaternion.identity);
        
        PlayerTank playerTank = tank.GetComponent<PlayerTank>();
        if (playerTank != null)
        {
            playerTank.maxHealth = (int)health;
            playerTank.ResetHealth();
            playerTank.SetRespawnPoint(spawnPosition);
            
            if (hasMeleeAttack)
            {
                playerTank.gameObject.AddComponent<PlayerMeleeAttack>();
            }
        }

        return tank;
    }
}

public class EnemyTankBuilder : TankBuilder<EnemyTankBuilder>
{
    private bool isReinforced;
    private bool usePatrolBehavior;

    public EnemyTankBuilder SetReinforced(bool reinforced = true)
    {
        isReinforced = reinforced;
        return this;
    }

    public EnemyTankBuilder SetPatrolBehavior(bool enabled = true)
    {
        usePatrolBehavior = enabled;
        return this;
    }

    public override GameObject Build()
    {
        GameObject tank = GameObject.Instantiate(tankPrefab, spawnPosition, Quaternion.identity);
        
        EnemyTank enemyTank = tank.GetComponent<EnemyTank>();
        if (enemyTank != null)
        {
            enemyTank.isReinforced = isReinforced;
        }

        return tank;
    }
}
```
**Case Study 2**

```csharp
public interface IAudioSystem
{
    void PlaySound(string name);
    void StopSound(string name);
    void StopAllSounds();
    void SetMasterVolume(float volume);
    void SetSFXVolume(float volume);
    void SetMusicVolume(float volume);
    void SetUIVolume(float volume);
}

public class UnityAudioAdapter : IAudioSystem
{
    private readonly AdvancedAudioManager audioManager;

    public UnityAudioAdapter(AdvancedAudioManager manager)
    {
        audioManager = manager;
    }

    public void PlaySound(string name)
    {
        var s = audioManager.sounds.Find(sound => sound.name == name);
        if (s == null)
        {
            UnityEngine.Debug.LogWarning($"Sound: {name} not found!");
            return;
        }
        if (s.source.clip == null)
        {
            UnityEngine.Debug.LogWarning($"AudioSource for {name} is null!");
            return;
        }

        switch (s.type)
        {
            case AdvancedAudioManager.AudioType.SFX:
                s.source.volume = s.volume * audioManager.masterVolume * audioManager.sfxVolume;
                break;
            case AdvancedAudioManager.AudioType.Music:
                s.source.volume = s.volume * audioManager.masterVolume * audioManager.musicVolume;
                break;
            case AdvancedAudioManager.AudioType.UI:
                s.source.volume = s.volume * audioManager.masterVolume * audioManager.uiVolume;
                break;
        }

        s.source.Play();
    }

    public void StopSound(string name)
    {
        var s = audioManager.sounds.Find(sound => sound.name == name);
        if (s == null)
        {
            UnityEngine.Debug.LogWarning($"Sound: {name} not found!");
            return;
        }

        s.source.Stop();
    }

    public void StopAllSounds()
    {
        foreach (var s in audioManager.sounds)
        {
            s.source.Stop();
        }
    }

    public void SetMasterVolume(float volume)
    {
        audioManager.UpdateAllVolumes();
    }

    public void SetSFXVolume(float volume)
    {
        audioManager.UpdateAllVolumes();
    }

    public void SetMusicVolume(float volume)
    {
        audioManager.UpdateAllVolumes();
    }

    public void SetUIVolume(float volume)
    {
        audioManager.UpdateAllVolumes();
    }
}

public class FMODAudioAdapter : IAudioSystem
{
    // FMOD specific fields would go here
    
    public void PlaySound(string name)
    {
        // FMOD implementation
    }

    public void StopSound(string name)
    {
        // FMOD implementation
    }

    public void StopAllSounds()
    {
        // FMOD implementation
    }

    public void SetMasterVolume(float volume)
    {
        // FMOD implementation
    }

    public void SetSFXVolume(float volume)
    {
        // FMOD implementation
    }

    public void SetMusicVolume(float volume)
    {
        // FMOD implementation
    }

    public void SetUIVolume(float volume)
    {
        // FMOD implementation
    }
}
```

**Reference**

[1] F. P. Brooks Jr., "No Silver Bullet: Essence and Accidents of Software Engineering," IEEE Computer, vol. 20, no. 4, pp. 10-19, Apr. 1987.

[3] Xiaoxi Chen, Jia Chen, Shengwen Zhang, and Lili Sui, ‘Application of adapter pattern in container ship stowage system’, in 2010 2nd International Conference on Industrial and Information Systems, volume1, pp.120–123.IEEE,(2010).

[4] Saurav Dhait, Atharva Sapate, Atharva Gadge, Pradnya Borkar, Sagarkumar Badhiye, and Ujjwala Bal Aher, ‘Analysis of the best creational design patterns in software development’ in 2024 8th International Conference on Computing, Communication, Control and Automation (ICCUBEA), pp.1–5. IEEE, (2024).

[5]  Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, Design patterns: elements of reusable object-oriented software, Pearson Deutschland GmbH,1995.

[6] Refactoring.Guru.Refactoringguru,n.d.Accessed:2025-04-07.

