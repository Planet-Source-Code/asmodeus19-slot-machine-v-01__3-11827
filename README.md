<div align="center">

## Slot Machine v\.01


</div>

### Description

Console Slot Machine Game - Please vote for me.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Asmodeus19](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/asmodeus19.md)
**Level**          |Beginner
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Games](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/games__3-13.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/asmodeus19-slot-machine-v-01__3-11827/archive/master.zip)





### Source Code

```
//Slot Machine v.01
#include <iostream> //Needed for cout and cin functions
#include <ctime> // Used to generate random numbers
#include <cstdlib> // Used to generate random numbers
#include <fstream> // Needed for file I/O
using namespace std; // Default namespace
int money = 0;
void newgame();
void savegame();
void loadgame();
void slot();
int main() // Main Function
{
  int mainmenu = 1;
  system("CLS"); // Clears console screen
  main:
  cout << "\n\n";
  cout << " ***********************************\n" // Title banner
     << " *    Slot Machine v.01     *\n"
     << " *     by Asmodeus       *\n"
     << " ***********************************\n"
     << "\n\n\n";
    cout << " [1] Start New Game\n" // Main menu
       << " [2] Save Game\n"
       << " [3] Load Game\n\n"
       << " [4] Quit\n\n";
    cin >> mainmenu;
    if (mainmenu < 1 || mainmenu > 4) // If check of user input
    {
           system("CLS");
           goto main;
    }
    if (mainmenu == 1)
    {
           newgame();
    }
    if (mainmenu == 2)
    {
           savegame();
    }
    if (mainmenu == 3)
    {
           loadgame();
    }
    if (mainmenu == 4)
    {
           return 0; // Quits the application
    }
}
void newgame() // Sets users beginning money - then moves to slot function
{
    cout << "\n\nWelcome to Slots - You currently have $100 to\n"
       << "play with - Have Fun.\n\n\n";
    money = money *= 0; // Sets money to zero
    money = money += 100; // Sets beginning cash to 100
    system("PAUSE");
    slot();
}
void savegame()
{
   cout<<"Saving Your Game\n\n";
   ofstream savfile("save.txt"); // Text file it saves to
   savfile << money << endl;
   savfile.close();
   main();
}
void loadgame() // Function to load saved games
{
   cout<<"\nLoading Your Saved Data\n\n";
   int money[50]; // Used To Hold The Integer Values From The Txt File
   ifstream loadsave("save.txt"); // Load The Save.txt
   loadsave >> ::money;// Read 1 line From File
   loadsave.close();
   system("PAUSE");
   system("CLS");
   slot();
}
void slot() // Function that controls all slot features
{
   slot:
   system("CLS");
   int slotmenu;
   cout << "\n\n";
   cout << "[1] Play Slot\n"
     << "[2] Check Money\n"
     << "[3] Main Menu\n\n";
   cin >> slotmenu;
   if (slotmenu == 1)
   {
     system("CLS");
     cout << "You insert $1 and pull the handle.\n\n\n";
     money--;
     srand(time(0));
     int slot1 = rand() % 9 + 1; //Generates number between 1 and 9
     int slot2 = rand() % 9 + 1;
     int slot3 = rand() % 9 + 1;
     cout << " ===============================\n"
        << " =     =     =     =\n"
        << " ="; cout << "  " << slot1; cout << "     " << slot2; cout << "     " << slot3; cout << "  =\n";
     cout << " =     =     =     =\n"
        << " ===============================\n\n\n";
     if (slot1 != slot2 && slot2 != slot3 && slot1 != slot3)
     {
          cout << "Sorry you lost.\n\n";
          system("PAUSE");
          slot();
     }
     else if (slot1 == slot2 && slot1 != slot3)
     {
          cout << "You Win - $10\n\n";
          money = money += 10;
          system("PAUSE");
          slot();
     }
     else if (slot1 != slot2 && slot1 == slot3)
     {
          cout << "You Win - $10\n\n";
          money = money += 10;
          system("PAUSE");
          slot();
     }
     else if (slot1 != slot2 && slot1 != slot3 && slot2 == slot3)
     {
          cout << "You Win - $10\n\n";
          money = money += 10;
          system("PAUSE");
          slot();
     }
     else if (slot1 == slot2 && slot1 == slot3)
     {
          cout << "You hit the Jackpot - $100\n\n";
          money = money += 100;
          system("PAUSE");
          slot();
     }
   }
   if (slotmenu == 2)
   {
     cout << "You have $" << money << endl << endl << endl;
     system("PAUSE");
     goto slot;
   }
   else if (slotmenu == 3)
   {
     main();
   }
}
```

