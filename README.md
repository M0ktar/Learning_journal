# My programming journal 
This is my learning journal for programming

## 2024-10-15

I was creating a new repository. I created a test. Not sure how to delete it though but I do know how to create a file.

## 2024-10-21

This is the first tutorial that I've done for this session, and I've learned how to program the player movement in Unity. I didn't face any particular problems during development, and it was easier to digest and apply what I've learned in this tutorial from the script with ease. So for example, code like **public float speed = 10;** and the **float inputX = Input.GetAxis("Horizontal");** & **float inputY = Input.GetAxis("Vertical");** were pretty easy to jot down off by heart (granted I was confused with what **Input.GetAxis** at the time, but what helped me overcome my confusion was understanding that it's a method that handles the user input. It involves the rotation and movement of the player. What I love the most is that even if I still am confused, I can use the unity documentation to gain further understanding of its function) considering I already garnered knowledge from researching tutorials from coding off of sessions.

I don't know much about the basics of C# besides mastering my understanding of variables (but besides that, there are still many topics in C# to unpack and learn from). During my free time I've tried to learn how to code, but reading scripts and digesting information felt uneasy. But, I felt like my knowledge of C# and unity (for someone who knows little of it) has increased thanks to this tutorial, and understanding aspects of programming has become a lot easier with me.

I think out of all the parts that I've programmed (despite how little I know of it so far), understanding something that I had trouble knowing in the past was a relief. I felt like I understood the difference between public and private classes, void start and update sections of the script (thanks to the support of unity), and methods compared to before. I think out of all of them though, I was mostly satisfied with learning how methods (aka functions) worked and what they meant when coding in Unity (for example, they're a block of code that tells the computer what to do. The difference to a variable is that when calling a method you're giving it an action name, whereas with variables you're just simply storing data).

Here's the script that I've generated for the player movement to work:


    public float speed = 10;

    void Update()
    {
        float inputX = Input.GetAxis("Horizontal");
        transform.Translate(inputX * speed * Time.deltaTime * Vector3.right);
        float inputY = Input.GetAxis("Vertical");
        transform.Translate(inputY * speed * Time.deltaTime * Vector3.left);
    }

However, wrapping my head around Time.deltaTime was a chore to understand. It was easily one of the most difficult parts of the project, as I was stuck for its purpose being in that specific block of code in the first place. But thanks to the unity documentation, and I now recognize that it's a variable Unity has built on its own, and its purpose was to make the game run smoothly and somewhat at a similar speed, even if the players are experiencing the game on different devices (it's also helps knowing that we use it when updating or moving the game).


## 2024-10-29

For the second tutorial, I've learned how to implement the pick-up mechanic and add coins in unity (building a sort of 3D side-scrolling platformer (granted positioned in a 2D perspective) for my game). Essentially, I've taken what I've made for my first tutorial on player movement and adding new features, paying homage to basic platform games (like Mario, Sonic, Crash Bandicoot etc...).

I've learned the GetInput.Key a little bit more (and a little bit better) and the force method while re-scripting the player movement (changing movement keys from using left to right stick (or alternatively A and D), to only pressing the spacebar- which was the goal when producing the script)

    void Update()
    {
        if (Input.GetKey(KeyCode.Space))
        {
            body.AddForce(Vector3.right * force, ForceMode.Impulse);
        }
    }

This was a session I was interested with, but faced the most difficulties on, almost to the point where I wanted to quit and move on to the next session. There were sections in the tutorial where I felt lost in where handling the prefabs for the coin objects (changing the colour of the coin to gold). There were also unusual ways the game turned out to be regarding the movements of the coins, which I was completely stuck on when scripting the coin's movement. The speed was working perfectly fine. But whenever I tried to run the game, rather than the coins staying in one place and spinning simultaneously, they all moved around the platform in a circle- and they didn't spin in the way it was supposed to spin.

It's hard for me to explain the overall issue I had when running the game, but I'll give you a visual aid for it: 

![Screen Recording 2024-11-10 at 21 10 35](https://github.com/user-attachments/assets/0bc79da7-35df-4e19-9207-94d5bdfa1f4e)

I decided to backtrack to the tutorial online, and decide to delete the script and objects for the pick-up coin. Through constant trial an error, I've thankfully overcame those issues. This is now what it looks like (and what it should've looked like):

![Screen Recording 2024-11-11 at 17 17 44](https://github.com/user-attachments/assets/8dca35b9-a4e7-4e35-a176-87eb54c5f2ec)

<u>What were the issues I had to overcome:</u>
- I didn't change the cylinder collider to the sphere collider at all, which is probably why the coins looked 2D
- I realized that you can add new material to unity, which in turn allows me to edit/render the colours of the object (this part I found the most difficult to complete)
- The reason why the objects were spinning in that way from the initial clip was that I accidentally made each of the five duplicated coins as child objects, and assigned all of them to a parent object (which is what the first coin was).

So when scripting the game for the second tutorial, I thought there were problems with the way I was scripting my projects. Instead, there were issues with more on how I was misleadingly navigating areas in unity outside of coding. I've learned that not only my understanding of code needs to be improved upon (which is going successfully thus far), but my knowledge of unity needs to be improved upon too.

## 2024-11-04

With this tutorial, I was able to create a first-person point and click game- where the player is able to control the camera in first person perspective. I followed a tutorial made by brickey, which taught me how to program first person movement in unity. When looking through his code, I think the least hardest part for me was to wrap my head around some aspects of the code that he implemented. New stuff that was introduced to me like Mathf.Clamp and the Quaternion structure (which I now know is always relevent to rotation when working/scripting in unity). Here's the code that I was working on when programming the camera movement for the player: 

    public float sensX;
    public float senseY;
    public float mouseSensitivty = 100f;

    public Transform playerBody;

    float xRotation = 0f;
    float yRotation;
    // Start is called before the first frame update
    void Start()
    {
    //Hides the cursor
        Cursor.lockState = CursorLockMode.Locked;
        Cursor.visible = false;
    }

    // Update is called once per frame
    void Update()
    {
        //mouse input for the player
        float mouseX = Input.GetAxis("Mouse X") * Time.deltaTime * mouseSensitivty * sensX;
        float mouseY = Input.GetAxis("Mouse Y") * Time.deltaTime * mouseSensitivty * senseY;

        xRotation -= mouseY;
        xRotation = Mathf.Clamp(xRotation, -90f, 90f);

        playerBody.Rotate(Vector3.up * mouseX);
        transform.localRotation = Quaternion.Euler(xRotation, 0f, 0f);

I also added the player movement (of course) in the player game object, which is basically the same code that I've done from a previous tutorial. One of the biggest issues that I've faced (which I got help from) was the camera, and how it was only applying the movement for the x-axis but not the y-axis. The problem was solved once I realised that the rigidbody and the transform components in my script are assigned differently in unity, indicating that the player object is the player body and the transform component is the main camera object. The overall issue was that the player object was moving in one direction because I added the script in one object. Once I understood that, all I have to do is to add the script as a component to both the player object and main camera objects, and that's pretty much it.   

## 2024-11-11
Developing a top-down 2D zelda like project. i jotted down the movement of the player pretty easily (thanks to the previous tutorial).
My task for this tutorial was to create specific mechanics for this project (less about making the actual game, more so experimenting with features I could adjust to when I get to creating my prototype) in order to feel comfortable creating my own prototype.

When working on this tutorial, I was able to script the player movement on a 2D canvas this time, and have the player use a weapon to attack an enemy (Hindsight, this is incredibly unpolished, though in the future I will be working on that to some point during later parts of the tutorial). I've also learned the coolDown, and Vector2 a little bit more (such as the Vector2.zero) and recently Quaternion. I've also learned about the method Physics2D.OverlapBoxAll when scripting my sword object as well.

This is what I've worked on today's session:

![Screen Recording 2024-11-17 at 13 06 04](https://github.com/user-attachments/assets/53fe45af-9b71-40fe-95a3-77c9a15ed7b4)

This is the script for the sword I've worked on (which I felt was one of the most challenging parts to do):
    
    public Transform swordTransform;
    public float attackSpeed = 5f;
    private float attackCooldown = -0.1f;
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.Z) && attackCooldown <= 0f)
        {
            Attack();
            attackCooldown = attackSpeed;
        }

        attackCooldown -= Time.deltaTime;
    }

    void Attack()
    {
        swordTransform.Rotate(Vector2.left * 90f);

        Collider2D[] hitEnemies = Physics2D.OverlapBoxAll(swordTransform.position, new Vector2(1f, 1f), 0f);

        foreach (Collider2D enemy in hitEnemies)
        {
            if (enemy.CompareTag("Enemy"))
            {
                Destroy(enemy.gameObject);
            }
        }

    }

There were a few issues I faced that didn't felt right during development. I felt like the one of the challenges for me was to make the player move WITH the sword. I fixed this by using the heirachy tool and assigned the parent and child tool (which was an issue I faced last time). It was a challenge because it literally took me a consider amount of my time to figure out on how I could fix this issue. At first I thought it had something to do with programming, but no it was just something I had to re-adjust with unity. There was also a challenge, and a little bit harder, on understanding the coolDown variable, and how it worked when programming my sword. I understand now that it's used for when player has time to take a small short break when attacking for a limited amount of time. So basically understanding the variable and what it means in gameplay *private float attackCooldown = -0.1f;*. 

This isn't the best, but I'm content with what I have so far with this tutorial so far. I'm hoping to polish the game when working on my prototype a lot more, this is just preperation for what's to come when working on my prototype. In the future, when working on the prototype, I could maybe fix the way the sword is function. So probably instead of attacking the enemy in one direction, I could attack by facing in four (depending on the direction the player is facing), or how I could fix more on how the sword appears when the player presses the attack button (the framework for how the sword appears and disappears is a bit too quick, so I'll get on that later on).
