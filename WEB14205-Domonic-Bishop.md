# Interactive Narrative

## Domonic Bishop

<img src="https://i.imgur.com/IHBFNt7.png" width="300">

## Index
- [Presentations](#formative-link)
- [Blogs](#blogs)
- [Research Pack](#research-pack)
- [Boardgame Production](#boardgame-production)
- [User Manuals](#user-manuals)
- [Phaser Production](#phaser-production)
- [Final Game Code](#final-game-code)



## [Formative Link](https://drive.google.com/open?id=19IfPvb-LPOdwrjAaCOnlHkbHE7v8pZ5FZW3ZMMakXxw)

## [Summative Link](https://docs.google.com/presentation/d/1fWIoRk3HG-4Df92BLTQKdy1PPOKL2YEXJVpg--n79WU/edit?usp=sharing)


## Blogs
1. [What is your favourite board game and why?](https://medium.com/@domonic_bishop/why-pokemon-master-trainer-is-amazing-d08f2e3e5c4c)
2. [When creating online content for children, what are some of the ethical considerations you need to take?](https://medium.com/@domonic_bishop/when-creating-online-content-for-children-what-are-some-of-the-ethical-considerations-you-need-to-16dac4670786)
3. [What are your strength and weaknesses in relation to completing this project? And how are you going to address them?](https://medium.com/@domonic_bishop/what-are-your-strength-and-weaknesses-in-relation-to-completing-this-project-5acbc4da357b)
4. [Reflect and evidence your contribution to this group project so far.](https://medium.com/@domonic_bishop/reflect-and-evidence-your-contribution-to-this-group-project-so-far-why-what-where-when-how-4786d80508c0)
5. [Evidence and analyse how games have developed through time](https://medium.com/@domonic_bishop/evidence-and-analyse-how-games-have-developed-through-time-14cb1ca48d6a)
6. [500 words reflective report on your (Why, what, where, when & how) contribution to this project](https://medium.com/@domonic_bishop/reflective-report-i-n-term-3-f167e912db6b)
7. [500 words, dissect and discuss a core game mechanics behind an online game of their choice.](https://medium.com/@domonic_bishop/game-report-zelda-breath-of-the-wild-7a38d2d29ad0)

## [Research Pack](https://drive.google.com/open?id=1xQiWhsqRuTuW6EQCn_P7gAJF-IgFCmxORhsWwZUpTiI)

The research pack is composed of the data we collected to create and develop our game. It details the process of our development and how that process caused our concept to change into something more accessible to an audience. We specifically focused on design orientated games and games that allowed creative ideas in how they were played. This allowed us to let our concept of a creative game about being creative to come alive.

Here is our design process illustrated:

<img src="https://i.imgur.com/yGiQ45K.png">

It was inspired by the double diamond process that I was taught during my time doing the Design Academy. Here's their version:

<img src="https://www.designcouncil.org.uk/sites/default/files/styles/dc_-_wysiwyg_-_smart_embed/public/assets/images/Double-Diamond-A3-for-publication-A-2000px_1.png?itok=uw0EBs5E">

## [Boardgame Production](https://drive.google.com/drive/folders/1uguvQgUp174xod0UFSq02qg2Zh_-GV6y?usp=sharing)

## User Manuals

- [Prototype v1 (initial idea) Manual](https://drive.google.com/file/d/1N3AltyInELrP6nsAI-3GDnVvXmG4x9sX/view?usp=sharing)

- [Prototype v2 (final product) Manual](https://drive.google.com/file/d/1sI2xT9iBEhbQd659quYU0bSYiuNsdRT6/view?usp=sharing)

## [Phaser Production](https://dombishop.github.io/I-N-Game/)

The game idea we had for Phaser is a game where a boss chases his creative employe (hipster) when it's past a deadline. The player needs to control the creative and collect lightbulbs which represent creative ideas and build up as big a score as he can. When the player is caught by the boss it's game over, when that happens, hit command+R to restart the game.

This is the initial code used for the Phaser production, it's from Phaser 2 and it was used due to a lack of technical documentation that we used 2 instead of Phaser 3. The initial code had the boss chasing the advertising creative at a steady pace and jumping consistently in terms of time and height. The code was used as a platform for me to learn Phaser while still learning to produce a final game:

~~~~
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>A Bobby's Tale - By wwwtf productions</title>
    <script type="text/javascript" src="js/phaser.min.js"></script>
       <style type="text/css">
        body {
            margin: 0;
        }
    </style>
</head>
<body>
 
<script type="text/javascript">
var game = new Phaser.Game(800, 600, Phaser.AUTO, 'phasergame', { preload: preload, create: create, update: update });
   
function preload() {
    game.load.image('city', 'Assets/city1.png');
    game.load.image('ground', 'Assets/platform4.png');
    game.load.image('clue', 'Assets/clue.png');
    game.load.image('floor', 'Assets/platform4.png');
    game.load.image('barrier', 'Assets/barrier.png');
    game.load.image('crate', 'Assets/crate.png');
    game.load.image('pause', 'Assets/pausebutton.jpg');
    game.load.spritesheet('police', 'Assets/policesprite.png', 32, 48);
    game.load.spritesheet('clapp', 'Assets/villian.png', 32, 48);
    game.load.spritesheet('startButton','Assets/startbutton.png');
}
var camSpeed = 2;
   
var button;
var player;
var platforms;
var cursors;
var villain;
var clues;
var score = 0;
var scoreText;
var timer;
var seconds = 0;
var minutes = 0;
var timerText;
function create() {
   
    //  We're going to be using physics, so enable the Arcade Physics system
    game.physics.startSystem(Phaser.Physics.ARCADE);
   
    //setting the world size - not just camera view like before
    game.world.setBounds(0, 0, 4000, 600);
    //  A simple background for our game
    game.add.tileSprite(0, 0, 4000, 600, 'city');
   
    //setting the colour of the 'sky'
    game.stage.backgroundColor = "#9ab4d7";
   
     // start button
    Button = game.add.button(100, 150, 'startButton', actionOnClick, this, 2, 1, 0);
    Button.scale.setTo(0.4,0.4);
    function actionOnClick () {
    Button.visible = false;
    player.visible = true;
    villain.visible = true;
    clue.visible = true;
    ground.visible = true;
    platforms.visible = true;}
   
    //  The platforms group contains the ground and the 2 ledges we can jump on
    platforms = game.add.group();
    //  We will enable physics for any object that is created in this group
    platforms.enableBody = true;
    // Here we create the ground.
    var ground = platforms.create(0, game.world.height - 34, 'floor');
    //  Scale it to fit the width of the game (the original sprite is 400x32 in size)
    ground.scale.setTo(1,1);
    //  This stops it from falling away when you jump on it
    ground.body.immovable = true;
   
    //creating a ledge for the villain to stand on at the start of the game.
    var ledge = platforms.create(-3960, 200, 'ground');
    ledge.body.immovable = true;
   
    //adding traffic barriers for the player to jump over
    var barrier = platforms.create(400, 530, 'barrier');
    barrier.body.immovable = true;
   
    var barrier = platforms.create(1700, 530, 'barrier');
    barrier.body.immovable = true;
   
    //adding crate for player to jump over
    var crate = platforms.create(1100, 550, 'crate');
    crate.body.immovable = true;
   
    var crate = platforms.create(2900, 550, 'crate');
    crate.body.immovable = true;
   
    var crate = platforms.create(3400, 550, 'crate');
    crate.body.immovable = true;
    // The player and its settings
    player = game.add.sprite(32, game.world.height - 150, 'police');
    //  We need to enable physics on the player
    game.physics.arcade.enable(player);
    //  Player physics properties. Give the little guy a slight bounce.
    player.body.bounce.y = 0.2;
    player.body.gravity.y = 300;
    player.body.collideWorldBounds = true;
    //  Our two animations, walking left and right.
    player.animations.add('left', [0, 1, 2, 3], 10, true);
    player.animations.add('right', [5, 6, 7, 8], 10, true);
    //clapp and his settings
    villain = game.add.sprite(10,10, 'clapp');
   
    //enables physics on the villain
    game.physics.arcade.enable(villain);
    //giving the villain the same physics properties.
    villain.body.bounce.y = 0.2;
    villain.body.gravity.y = 300;
    villain.body.collideWorldBounds = true;
   
    //animations for walking left and right
    villain.animations.add('clappRight', [5, 6, 7, 8], 10, true);
    villain.animations.add('clappLeft', [4, 3, 2, 1], 10, true);
   
    //  Finally some clues to collect
    clues = game.add.group();
    //  We will enable physics for any clue that is created in this group
    clues.enableBody = true;
    //  Here we'll create 12 of them evenly spaced apart
      for (var i = 0; i < 60; i++)
    {
        //  Create a clue inside of the 'clues' group
        var clue = clues.create(i * 250, 0, 'clue');
        //  Let gravity do its thing
        clue.body.gravity.y = 300;
        //  This just gives each clue a slightly random bounce value
        clue.body.bounce.y = 0.7 + Math.random() * 0.2;
    }
   
    //  The score
    scoreText = game.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#fff' });
    scoreText.fixedToCamera = true;
    //  Our controls.
    cursors = game.input.keyboard.createCursorKeys();
   
    //Creates the variable for the timer based on game time
//    timer = game.time.create(false);
//    
//    //Places the timer text at 550 pixels from left, 16 pixels from top, and sets the same font size and colour as the Scores
//    timerText = game.add.text(550, 16, 'Time: 00:00', { fontSize: '32px', fill: '#fff'});
//    
//    //Stops the timer scrolling with the background
//    timerText.fixedToCamera = true;
//    
//    //Sets up a countdown loop 65,000 milliseconds long (eg 65 seconds)
//  //  timer.loop(65000, gameEnd, this);
//
//    //Starts the timer (so could be linked to the outcome of another function, or a “start” button)
//    timer.start();
    }
function update() {
    //  Collide the player and the clues with the platforms
    game.physics.arcade.collide(player, platforms);
    game.physics.arcade.collide(clues, platforms);
    game.physics.arcade.collide(villain, platforms);
    //  Checks to see if the player overlaps with any of the clues, if he does call the collectClue function
    game.physics.arcade.overlap(player, clues, collectClue, null, this);
   
   
    //checks to see if the villain overlaps the player, then activates clappEat
    game.physics.arcade.overlap(villain, player, clappEat, null, this);
    //  Reset the players velocity (movement)
    player.body.velocity.x = 0;
    if (cursors.left.isDown)
    {
        //  Move to the left
        player.body.velocity.x = -150;
        player.animations.play('left');
    }
    else if (cursors.right.isDown)
    {
        //  Move to the right
        player.body.velocity.x = 150;
        player.animations.play('right');
    }
    else
    {
        //  Stand still
        player.animations.stop();
        player.frame = 4;
    }
   
    //  Allow the player to jump if they are touching the ground.
    if (cursors.up.isDown && player.body.touching.down)
    {
        player.body.velocity.y = -350;
    }
   
    if (game.input.keyboard.isDown(Phaser.Keyboard.LEFT))
    {
        game.camera.x -= camSpeed;
       // if (!game.camera.atLimit.x)
      //  {
        //    s.tilePosition.x += camSpeed / 10;
       //c.tilePosition.x += camSpeed / 10; }
    }
    else if (game.input.keyboard.isDown(Phaser.Keyboard.RIGHT))
    {
        game.camera.x += camSpeed;
      //  if (!game.camera.atLimit.x)
       // {
       //     s.tilePosition.x -= camSpeed / 10;
       //     c.tilePosition.x -= camSpeed / 10;}
    }
    if (player.body.x < villain.body.x - 48)
        {
            villain.body.velocity.x = -100;
            villain.animations.play('clappLeft');
        }
     else if (player.body.x > villain.body.x + 48)
        {
            villain.body.velocity.x = 100;
            villain.animations.play('clappRight');
        }
     else
        {
            villain.animations.stop();
            villain.frame = 4;
        }
   
    if (villain.body.touching.down)
        {
        villain.body.velocity.y = -350;
        }
    function collectClue (player, clue) {
   
    // Removes the clue from the screen
    clue.kill();
    //  Add and update the score
    score += 1;
    scoreText.text = 'Clues: ' + score;
   
    }    
   
    function clappEat (villain, player){
   
    //kills the player
    player.kill();
   
    //says text
    scoreText.text = 'You died! You were killed by the serial killer.';
   
    //reduces score to 0
    score = 0;
    }
   
    //updateTimer()
   
//    function updateTimer() {
//    minutes = Math.floor(game.time.time / 60000) % 60;
//    seconds = Math.floor(game.time.time / 1000) % 60;
//    //If any of the digits becomes a single digit number, pad it with a zero
//    if (seconds < 10)
//        seconds = '0' + seconds;
//    if (minutes < 10)
//        minutes = '0' + minutes;
// timerText.text = 'Time: ' + minutes + ':'+ seconds;
//    }
   
   
}
</script>
<div id="phasergame"></div>
</body>
</html>
~~~~

## Final Game Code

I made adjustments to the code so that I there where elements of randomness to keep the player guessing. When the player crosses the boss, who now spawns randomly, the boss can now slightly change his speed. His jumps are also now randomised so as to keep the player guessing and more engaged in the game.

I also made changes to how the player character could move. Initially, the jump was more than enough to cover the office supply obstacles, and I felt this made the game too easy for the player. So I made the jump have a lower peak, requiring the players jumps to be more skilful to survive.

The light bulbs also now spawn randomly on the map and reset when they've all been collected. This is so the game is more interesting and can also last longer for the player.

~~~~
<!doctype html>
<html lang="en">
<head>
    <title>Game</title>
    game.load.image('city', 'Assets/city.png');
    game.load.image('car1', 'Assets/car1.png');
    game.load.image('car2', 'Assets/car2.png');
function createClues() {
    for (var i = 0; i < 60; i++)
{
        //  Create a clue inside of the 'clues' group
        var clue = clues.create(4000*Math.random(), 0, 'clue');
        //  Let gravity do its thing
        clue.body.gravity.y = 900;
        //  This just gives each clue a slightly random bounce value
        clue.body.bounce.y = 0.2 + Math.random() * 0.2;
}
}
    game.add.tileSprite(0, 0, 4000, 700, 'city');
    //var ledge = platforms.create(-3960, 200, 'ground');
    //ledge.body.immovable = true;
    var barrier = platforms.create(400, 500, 'car1');
    var barrier = platforms.create(1700, 500, 'car1');
    var crate = platforms.create(1100, 500, 'car2');
    var crate = platforms.create(2900, 500, 'car2');
    var crate = platforms.create(3400, 500, 'car2');
    player.body.gravity.y = 600;
    villain = game.add.sprite(Math.random()4000,10, 'clapp');
        createClues();
    scoreText = game.add.text(16, 16, 'Ideas: 0', { fontSize: '32px', fill: '#fff' });
//
//
//
//villain.body.x=Math.random()4000;
    console.log(villain.body.x);
            villain.body.velocity.x = -100+Math.random()-70;
            villain.body.velocity.x = 100+Math.random()70;
        villain.body.velocity.y = -150+Math.random()*-300;
    scoreText.text = 'Ideas: ' + score;
        if (score %60==0){
            createClues();
        }
    }
    scoreText.text = 'You missed the deadline!!!!!';
    ~~~~
