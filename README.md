# My programming journal 
This is my learning journal for programming

## 2024-10-15

I was creating a new repository. I created a test. Not sure how to delete it though but I do know how to create a file.

## 2024-10-21

For this tutorial, I've learned how to program the player movement in Unity. I didn't face any particular problems during development, and it was easier to digest and apply what I've learned in this tutorial from the script with ease. So for example, code like **public float speed = 10;** and the **float inputX = Input.GetAxis("Horizontal");** & **float inputY = Input.GetAxis("Vertical");** were pretty easy to jot down off by heart (granted I was confused with what **Input.GetAxis** at the time, but what helped me overcome my confusion was understanding that it's a method that handles the user input. It involves the rotation and movement of the player. What I love the most is that even if I still am confused, I can use the unity documentation to gain further understanding of its function) considering I already garnered knowledge from researching tutorials from coding off of sessions.

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
