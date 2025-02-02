![Quizbot banner_final](https://github.com/user-attachments/assets/6a336189-219d-4402-827c-e7cfaf3ea781)
# How to run quizbot
To run the script, paste this code into your preferred executor:
```lua
local CategoryManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/Damian-11/quizbot/master/quizbot.luau"))()

--[[ Custom category template:
local myCategory = CustomCategoryManager.New("Category Name") -- create a new category
myCategory:Add("This is a test question?", {"Correct Answer", "Wrong Answer1", "Wrong Answer2", "Wrong Answer3"}) -- add a question
myCategory:Add("What does the word 'Agua' mean in Spanish?", {"Water", "Milk", "Dog", "The number 5"}, 2) -- add a double point question

Check out https://github.com/Damian-11/quizbot/blob/master/README.md#how-to-add-custom-categories-and-questions for more information about adding custom questions
--]]
```

# How to add custom categories and questions
First, let's go over the difference between a `category`, a `quiz`, and a `question`:
- Category: A group/container of one or more `quizzes` about the same topic. Two categories can never share a name. Some examples of categories included with the script are:
  - Geography
  - Science
  - Sayings and Idioms
- Quiz (created automatically when you add a category): A group/container that can include any number of `questions`. Just like categories, two quizzes can never have the same name. Some examples are:
  - Science1
  - Science2
  - Math-easy
  - Biology
- Question: A single question. Includes information such as question text, the correct and wrong answers, and the amount of points that an user gets when they answer correctly. An example of a question in the "Chemistry" quiz is:
  - What is the chemical formula of water? [worth 1 point]
    - H2O
    - CO2
    - O2
    - 2HO
   
You will only be dealing with `categories` and `questions` while creating custom categories; `quizzes` will be handled automatically by the script.

The script returns the CustomCategoryManager class, which can be used to create custom categories using the CustomCategoryManager.New() function.
```lua
local CustomCategoryManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/Damian-11/quizbot/master/quizbot.luau"))()
local spanish = CustomCategoryManager.New("Spanish") -- create a new category
```
The `CustomCategoryManager.New("Category Name")` function will create a new category with the name you specifed. If the category already exists, it will simply add a new quiz to the existing category.
For the sake of this tutorial, I will be creating a *Spanish* category with questions about the meanings of Spanish words.

**Note: You should never worry about two categories using the same name. Just enter your desired category name, and the script will automatically handle the naming for you.**

Now that you have created a category, you will need to add some questions to it. You can do this by using the `:Add()` method of the category you just created:
```lua
spanish:Add("What does the word 'Agua' mean in Spanish?", {"Water", "Milk", "Dog", "The number 5"}, 2)
```
The `:Add()` method accepts three arguments:
- **The question text (string).** This is the message that the script will send once it reaches this question. Make it short and concise.
  `"What does the word 'Agua' mean in Spanish?"`
- **Possible choices (table containing a list of strings).** **The first item in the table is the correct answer.** The order you specify the answer options in does not affect the order they are sent in. The order they are sent in will always be randomized.
  `{"Water", "Milk", "Dog", "The number 5"}`. The correct answer here is *Water*, since it is the first item.
- **Number of points. (number, optional).** If you do not specify this value, the default (1) will be used. This is the amount of points the person who answered the question will receive. I recommend only setting this
  to 2 for hard questions. Otherwise, leave it blank to use the default.

That's it! You've created your first category with one question. Obviously, you should add more than one question to your category (I recommend about 5), but there is no hard-coded limit. You can add as many or as little as you please.
This category is treated the same way as the premade categories—you can choose it from the dropdown menu, type its name in, and it can even be played automatically through autoplay!

These are some tips/rules that'll help you make good categories:
- AI is a great tool for creating questions. I've personally had the most success with [Claude](https://claude.ai).
- Have either three or four options per question, and make sure the number of options is consistent throughout the whole quiz!
  Don't have three options in one question and then suddenly four in the next; it'll cause a lot of confusion for the players.
- Include five questions per quiz. I found this to be the sweet spot—not too long, not too short.
- Don't make your quizzes too hard. The average Roblox player should be able to answer them. Remember: people are having the most fun when they know the answers.
- If a specific question or option keeps getting filtered (tagged) by Roblox, consider rephrasing it or changing it out completely. Roblox has extremely sensitive chat
  filters. To minimze filtering, try to avoid the following in your quizzes:
  - Excessive number use. Some here and there are generally fine, but Roblox doesn't like it when you send too many of them in a row. A question such as
    "What is 2+2?", with the options being: "4", "22", "10", "2" will almost certainly get filtered every time.
  - Names of controversial or religious figures.
  - Politics/world events. For example: 9/11, Donald Trump, Joe Biden, facism, etc.
    I'd recommend testing the filter by yourself, as Roblox does allow some historical questions (see quizzes such as WWI, WWII, Anarchy, and Cold War for examples of what Roblox **does allow.**

## Difficulties

You might have noticed that difficulties are present in many of the premade categories, such as:
- Math
  - Math-easy
  - Math-hard
- Guess the country
  - Guess the country-easy1
  - Guess the country-easy2
  - Guess the country-medium
  - Guess the country-hard
- Geography
  - Geography-easy
  - Geography-medium
  - Geography-hard

Those are not separate categoires, but separate quizzes under their respective category. `Math`, `Guess the country`, and `Geography` being the categoires, while `Math-easy`, `Math-hard`, etc. are the quizzes.

Difficulties serve two main purposes:
 - Distinguising between similar quizzes
 - Acting as a filtering option for autoplay

Creating new quizzes with difficulties is very straightforward. You just need to include the difficulty name when using the `.New()` function:
```lua
local myCategory = CustomCategoryManager.New("Category Name", "Difficulty name")
```
The difficulty name can be anything (difficulties are not case sensitive, e.g. EASY = easy). The ones used in the premade quizzes are: `easy`, `medium`, `hard`.
I'd recommend sticking to those if you can to prevent overcomplicating things, but you're free to create your own difficulties if you want.
Difficulties only get appended to the names of quizzes when the category contains two or more quizzes with different difficulties from each other.
Let's say you wanted to create a *birds* quiz:
```lua 
local birdsEasy = CustomCategoryManager.New("Birds", "easy")
[questions]
```
The quiz works; however it simply appears as "Birds" in the dropdown menu and when sending the category list (with *detailed category list* turned on in settings).

Dropdown menu:

![image](https://github.com/user-attachments/assets/2215ac4d-afcd-426e-abe0-110e096a685e)

When sending the category list in chat:

![image](https://github.com/user-attachments/assets/d99f6073-e0c5-42cc-9e2b-388e3622ac25)

This is because since there is only one birds category, the script does not need to distinguish it by appending the difficulty. 

Note: The difficulty is registered and can still be used for autoplay filtering.
![image](https://github.com/user-attachments/assets/7c457676-fa72-4eef-be17-97ec2eed46bd)

Now let's say that you wanted to create a new bird quiz, but this time make it more challenging:
```lua 
local birdsEasy = CustomCategoryManager.New("Birds", "hard")
[questions]
```
And voila, the script now distinguishes between the two quizzes by appending their difficulty.

In the dropdown menu:

![image](https://github.com/user-attachments/assets/7db5d286-4b77-43d5-92e8-0bf98dbcbb3e)

And when sending the category list in chat:

![image](https://github.com/user-attachments/assets/0bf4d519-d80f-4dc6-876e-0a17653d8423)

My script now looks like this:
```lua
local CustomCategoryManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/Damian-11/quizbot/master/quizbot.luau"))()

local birdsEasy = CustomCategoryManager.New("Birds", "easy")
birdsEasy:Add("Which bird is known for its ability to mimic human speech?", {"Parrot", "Eagle", "Penguin", "Ostrich"})
birdsEasy:Add("What is the smallest bird in the world?", {"Hummingbird", "Sparrow", "Robin", "Finch"})
birdsEasy:Add("Which bird is the symbol of peace?", {"Dove", "Hawk", "Owl", "Raven"})
birdsEasy:Add("What bird lays the largest egg in relation to its body size?", {"Kiwi", "Ostrich", "Emu", "Cassowary"}, 2)
birdsEasy:Add("Which bird is known for its distinctive 'cuckoo' call?", {"Cuckoo", "Pigeon", "Seagull", "Woodpecker"})

local birdsHard = CustomCategoryManager.New("Birds", "hard")
birdsHard:Add("Which bird species has the largest wingspan?", {"Wandering Albatross", "Andean Condor", "California Condor", "Golden Eagle"})
birdsHard:Add("What is the only bird known to fly backwards?", {"Hummingbird", "Kiwi", "Penguin", "Ostrich"})
birdsHard:Add("What is the fastest bird in level flight?", {"Common Swift", "Peregrine Falcon", "Golden Eagle", "Frigatebird"})
birdsHard:Add("What is the only bird known to sleep while flying?", {"Common Swift", "Albatross", "Frigate Bird", "Hummingbird"})
birdsHard:Add("What is the only bird known to have a poisonous bite?", {"Hooded Pitohui", "Harpy Eagle", "Cassowary", "Secretary Bird"}, 2)
```

### Footer
Let me know if you have any feedback either about this tutorial or quizbot. I'd be happy to help clarify and answer any questions. 😁
