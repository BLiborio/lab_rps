CompSci 308 : RPS Design
===================

> This is the link to the Lab Description: 
[Lab - RPS](http://www.cs.duke.edu/courses/compsci308/spring16/classwork/02_design_rps/index.php)

Initial Design
=======

###Class 1: Main
1. Methods/Responsibilities
    * create Game using Game class
    * input file to the game -> initalize map
    * input line/string to the game -> update current map
###Class 1: Game
1. Methods/Responsibilites
    * read line of file and set up map of weapons to a list of what they beat -> initialize map
    * read line and update map -> update current map 
    * set game parameters with number of turns total and list of possible weapons
    * initialize players with id, turn, and score
    * play game -> incement turn and call the player.getWeapon() method
    * use faceoff method with players' weapons -> use .contains to see if chosen weapons are in the weaponsBeat list of each weapon
    * after all turns, retrieve scores from players 
    * declare winner 
###Class 2: Weapons
    * win against list 
    * lose against list
    * get and set methods to obtain and manipulate these lists
###Class 3
3. Player
    * choose weapon
    * give weapon to game class
    * track score, id, and turn

CRC Design
=======

![This is cool, too bad you can't see it](crc-example.png "Our CRC cards")

Use Cases
=======

A new game is started with two player, scores of 0:
In the Game class...
```java 
    public void init () {
        int initialScore = 0;
        Player player1 = new Player(1,initialScore);
        Player player2 = new Player(2,initialScore);
    }
```
A player chooses his RPS "weapon" with which he wants to play for this round:
In the Player class...
```java 
    public Weapon chooseWeapon (ArrayList<Weapon> weaponList) {
        int rand = (0 + (int)(Math.random() * ((weaponList.size() - 0) + 1))); //randomly chooses index cooresponsing to weaponList
        return weaponList(rand); // returns choosen weapon
    }
```
Given two players' choices, one player wins the round, and their scores are updated.
```java 
    public void faceOff(Weapon Player1Weapon, Weapon Player2Weapon) {
       ArrayList<Weapon> Player1BeatList = map.get(Player1Weapon);
       ArrayList<Weapon> Player2BeatList = map.get(Player2Weapon);
        if (Player1Weapon.equals(Player2Weapon)){
            return;
        }
        else if (Player2BeatList.contains(Player1Weapon)){
            Player2.addScore();
        }
        else {
           Player1.addScore(); 
        }
    }
```
