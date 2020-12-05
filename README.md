# score-board- 
//https://repl.it/@TysonMcMillan/SoccerScoreboardDrTCPPCOSC-1437#main.cpp
//Dr. Tyson McMillan a Soccer Scoreboard using 
//Ojbect Oriented Programming in C++
// Prajapati Deepkumara
#include <iostream>
#include <string> 
#include <unistd.h>
using namespace std; 

class Team 
{
  private:
    int score; 
    bool home_Status; 
    string name; 
    int shots_OnGoal; 
  public:
      Team() 
      {
        score = 0; 
        home_Status = false; 
        name = "TeamName"; 
        shots_OnGoal = 0; 
      }
      void setScore(int s) 
      { this->score = s; }
      void setHomeStatus(int hs)
       { this->home_Status = hs; }
      void setName(string n) 
      { this->name = n; }
      void setShotsOnGoal(int sog) 
      { this->shots_OnGoal = sog; }
      int getScore() const 
      { return this-> score; }
      bool getHomeStatus() const 
      {return this->home_Status; }
      string getName() const 
      {return this->name; }
      int getShotsOnGoal() const 
      { return this->shots_OnGoal; }
};

class Scoreboard
{
  private:
    int half; 
    Team home; 
    Team visitor; 
  public: 
    Scoreboard()
    {
      half = 0; 
    }  
    void setHalf(int h) { half = h; }
    void setHome(Team hSet) { home = hSet; }
    void setVisitor(Team vSet) { visitor = vSet; }
    int getHalf() const { return half; }
    Team getHome() const { return home; }
    Team getVisitor() const { return visitor; }
    void showScoreboard()
    {
      string color = ""; 
      string reset = "\x1b[0m";
      color = "\x1b[33;4m"; 
      string score = "\x1b[40;4m"; 
      cout << color << "Soccer Scoreboard " << reset << endl; 
      cout << home.getName() << "\t\t" << visitor.getName() << endl; 
      cout << score << home.getScore() << reset << "\t\t" << visitor.getScore() << endl; 
    }
};

int main() 
{
  Scoreboard s;
  Team t_One;
  Team t_Two; 
  string new_Name = "_"; 
  string your_Choice = "_"; 
  int new_Score = 0; 

 
  t_One.setHomeStatus(true);   

  
  s.setHome(t_One); 
  s.setVisitor(t_Two); 

 

  do 
  {
      system("clear");  
      s.showScoreboard();
      cout << "A  Home Team Name" << endl; 
      cout << "B  Home Team Score" << endl; 
      cout << "E = Exit" << endl;
      cout << ">"; 
      cin >> your_Choice; 

      if(your_Choice == "A" || your_Choice == "a")
      {
        
        cout << "Update Home Team Score module " << endl; 
        cout << "\nPlease enter a new name for the home team: ";
        cin >> new_Name; 
        
        t_One.setName(new_Name);
      }
      else if(your_Choice == "B" || your_Choice == "b")
      {
        cout << "\nUpdate Home Score Module" << endl; 
        cout << "\nPlease enter a new score for  home team: "; 
        cin >> new_Score; 
        t_One.setScore(new_Score);  
      }
      else if(your_Choice == "E" || your_Choice == "e")
      {
        cout << "Exit chosen." << endl; 
      }
      else 
      {
        cout << "\nInvalid input." << endl; 
        sleep(2); 
      }

      s.setHome(t_One); 
  
  }
  while(your_Choice != "E" && your_Choice != "e");

  return 0; 
}


