# githubclass
import java.util.HashMap;

public class Game {
  // TODO - define your game "state" here
  // Think: what data do I need to play an instance of this game?
  // For example, a quiz game might have:
  // private HashMap<String, String> questions;
  // private int score;

  // Here is an example of game state for a simple game that
  // collects and saves info for each user
  private String name;  // User name
  private int age;      // Age
  private String color;    // Favorite color
  private int randNum;  // Favorite number (picked randomly)
  private String randCharacter; // Favorite character (picked randomly)
  private static String[] character = {"Harry Potter", "Superman", "Minnie Mouse" , "Spiderman"};
  private HashMap<String, Game> users; // Info on all users

  // Play the game
  public void play () {
    System.out.println ("Hello!");
    users = new HashMap<String, Game>();
    
    while (true) {
      name = Utils.inputStr ("\nWhat's your name? ");
      if (!users.keySet().contains(name)) {
        age = Utils.inputNum ("What's your age? ");
        randNum = Utils.randInt (1, 100);
        color= Utils.inputStr("\nWhat's your favorite color?");
        randCharacter = Utils.randChoice(character);
        users.put(name, this);
      } else {
        System.out.println ("Welcome back!");
        age = users.get(name).age;
        randNum = users.get(name).randNum;
        randCharacter = users.get(name).randCharacter;
      }
      print();

      String command = Utils.inputStr("\nWhat do you want to do next (q=quit, f=forget my data, anything else to continue)? ");
      switch (command) {
        case "q":
          return;
        case "f":
          users.remove(name);
      }
      
    }
  }

  public void print() {
      System.out.println ("Your name is " + name);
      System.out.println ("You are " + age + " years old");
      System.out.println ("Your favorite color is " + color);
      System.out.println ("Your random character is: " + randCharacter);
      System.out.println ("Your level of cool is " + randNum);
  }
}
