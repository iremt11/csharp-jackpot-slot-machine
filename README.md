# Console Jackpot Slot Machine

![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=.net&logoColor=white)
![Console](https://img.shields.io/badge/Console-Application-blue?style=for-the-badge)
![Game](https://img.shields.io/badge/Game-Entertainment-red?style=for-the-badge)

An interactive console-based jackpot slot machine game built with C#. Experience the thrill of gambling with colorful visual effects, complex scoring systems, and bonus rewards - all from your terminal!

## 🎰 Game Overview

**Console Jackpot Slot Machine** brings the excitement of casino gaming to your console. Spin three slots with numbers 1-6 in vibrant colors (Red, Blue, Green) and watch as winning combinations light up your screen with rewards!

### Key Features
- **🎨 Colorful Console Output**: Numbers displayed in their corresponding colors
- **💰 Complex Scoring System**: 10 different winning combinations
- **🎁 Bonus Rewards**: Extra points for even/odd number patterns
- **🔄 Replay Functionality**: Keep playing with session score tracking
- **✅ Input Validation**: Robust error handling and user guidance

## 🎮 How to Play

### Game Rules
1. **Spin the Slots**: Three random numbers (1-6) appear in random colors
2. **Check for Wins**: Multiple winning patterns available
3. **Collect Points**: Earn money based on your combination
4. **Bonus Chance**: Get extra points for all even or all odd numbers
5. **Play Again**: Continue playing to build your total score

### Winning Combinations

| Combination | Description | Points |
|------------|-------------|--------|
| 🏆 **Jackpot** | Same numbers + same colors | **30** |
| 🥇 **High Win** | Same numbers + different colors | **28** |
| 🎯 **Triple Match** | Same numbers + mixed colors | **26** |
| 📈 **Sequence + Color** | Consecutive numbers + same color | **20** |
| 📊 **Sequence** | Consecutive numbers + different colors | **18** |
| 🔢 **Sequence Mixed** | Consecutive numbers + mixed colors | **16** |
| 🌈 **Different + Color** | Different numbers + same color | **10** |
| 🎲 **All Different** | All different numbers and colors | **8** |
| 🎨 **Color Match** | Same colors only | **6** |
| 🎁 **Bonus** | All even or all odd numbers | **+3** |

### Example Gameplay
```
5 3 1 
(Red) (Blue) (Green)

You lost :(
Do you want to play again? (y or n): y

-----------------------------------
4 4 4 
(Blue) (Blue) (Blue)

Congratulations!
You win $30.
You win $3 bonus.
Do you want to play again? (y or n): n

...................................
The game is finished!
Total score obtained is $33
```

## 🚀 Getting Started

### Prerequisites
- **.NET 6.0 or higher**
- **Windows/Linux/macOS** (cross-platform compatible)
- **Console/Terminal** with color support

### Installation & Running

#### Option 1: Clone and Run
```bash
# Clone the repository
git clone https://github.com/your-username/console-jackpot-slot-machine.git
cd console-jackpot-slot-machine

# Run the game
dotnet run
```

#### Option 2: Build and Execute
```bash
# Build the project
dotnet build

# Run the executable
dotnet bin/Debug/net6.0/JackpotGame.dll
```

#### Option 3: Direct Compilation
```bash
# Compile and run in one command
csc JackpotGame.cs && ./JackpotGame.exe
```

## 🎯 Game Features Deep Dive

### Advanced Scoring Algorithm
The game implements a sophisticated scoring system that evaluates multiple conditions:

```csharp
// Primary win conditions (mutually exclusive)
if (allSameNumber && allSameColor)         return 30;  // Jackpot
if (allSameNumber && allDifferentColors)   return 28;  // High win
if (allSameNumber)                         return 26;  // Same numbers
if (consecutiveNumbers && allSameColor)    return 20;  // Sequence + color
if (consecutiveNumbers && allDifferentColors) return 18; // Sequence
if (consecutiveNumbers)                    return 16;  // Sequence mixed
if (allDifferentNumbers && allSameColor)   return 10;  // Different + color
if (allDifferentNumbers && allDifferentColors) return 8; // All different
if (allSameColor)                          return 6;   // Color match only

// Bonus condition (independent)
if (allEvenOrOdd)                         bonus += 3;  // Even/odd bonus
```

### Color System Implementation
```csharp
// Dynamic color assignment
string[] colors = { "Red", "Blue", "Green" };
ConsoleColor[] consoleColors = { 
    ConsoleColor.DarkRed, 
    ConsoleColor.DarkBlue, 
    ConsoleColor.DarkGreen 
};

// Visual output with color coordination
PrintColoredNumber(number, color);
```

### Input Validation System
```csharp
bool validInput = false;
do {
    Console.Write("Do you want to play again? (y or n): ");
    string userInput = Console.ReadLine();
    
    if (userInput == "y") {
        // Continue game logic
        validInput = true;
    } else if (userInput == "n") {
        // End game logic
        validInput = true;
    } else {
        Console.WriteLine("Sorry, that's not valid. Use 'y' to retry or 'n' to stop.");
    }
} while (!validInput);
```

## 🎲 Game Mechanics

### Probability Analysis
- **Total Possible Combinations**: 6³ × 3³ = 5,832
- **Jackpot Probability**: 6 × 1 / 5,832 = 0.103%
- **High Win Probability**: 6 × 6 / 5,832 = 0.617%
- **Any Win Probability**: ~15-20% (varies by condition)

### Consecutive Number Detection
```csharp
int min = Math.Min(number1, Math.Min(number2, number3));
int max = Math.Max(number1, Math.Max(number2, number3));
int mid = number1 + number2 + number3 - min - max;

bool consecutiveNumbers = (mid == min + 1) && (max == mid + 1);
```

### Even/Odd Bonus Logic
```csharp
bool allEvenOrOdd = (number1 % 2 == number2 % 2) && 
                    (number2 % 2 == number3 % 2);
```

## 🏗️ Code Architecture

### Project Structure
```
JackpotGame/
├── JackpotGame.cs          # Main game logic
├── JackpotGame.csproj      # Project configuration
└── README.md               # Documentation
```

### Core Methods
- **`Main()`**: Game loop and session management
- **`GetRandomColor()`**: Color generation utility
- **`PrintColoredNumber()`**: Visual output handler
- **Scoring Logic**: Inline condition evaluation

### Design Patterns
- **Procedural Programming**: Straightforward game flow
- **Static Utility Methods**: Reusable helper functions
- **State Management**: Session-based score tracking

## 🎨 Visual Experience

### Color Coding
- 🔴 **Red Numbers**: Displayed in dark red
- 🔵 **Blue Numbers**: Displayed in dark blue  
- 🟢 **Green Numbers**: Displayed in dark green

### Game States
- **🎰 Playing**: Colorful number display
- **🎉 Winning**: Green congratulations message
- **😞 Losing**: Red disappointment message
- **🎁 Bonus**: Special bonus notification

### Session Summary
```
...................................
The game is finished!
Total score obtained is $127
```

## 🧪 Testing & Quality

### Manual Testing Scenarios
1. **All Same Numbers + Same Color** → Verify 30 points
2. **Consecutive Numbers** → Verify sequence detection
3. **All Even/Odd Numbers** → Verify bonus +3 points
4. **Invalid Input** → Verify error handling
5. **Session Tracking** → Verify total score accumulation

### Edge Cases Handled
- **Invalid User Input**: Comprehensive validation loop
- **Console Color Support**: Graceful degradation
- **Random Seed**: Proper randomization
- **Score Overflow**: Integer bounds checking

## 🚀 Future Enhancements

### Potential Features
- **💾 High Score Persistence**: Save top scores to file
- **🎵 Sound Effects**: Audio feedback for wins
- **📊 Statistics**: Win/loss ratio tracking
- **🃏 Multiple Game Modes**: Different difficulty levels
- **🏆 Achievements**: Unlock special rewards
- **💸 Betting System**: Variable stake amounts

### Technical Improvements
- **🔧 Configuration File**: Customizable game parameters
- **🧪 Unit Tests**: Comprehensive test coverage
- **📱 Cross-Platform UI**: GUI version
- **🌐 Network Play**: Multiplayer capabilities

## 🤝 Contributing

### How to Contribute
1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit changes**: `git commit -m 'Add amazing feature'`
4. **Push to branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Contribution Ideas
- **🎮 New Game Modes**: Additional winning patterns
- **🎨 Enhanced Graphics**: ASCII art displays
- **📊 Analytics**: Detailed game statistics
- **🔧 Code Optimization**: Performance improvements

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Developer

**İrem** - Game Developer & C# Enthusiast
- GitHub: [@iremt11](https://github.com/iremt11)
- Focus: Console applications and interactive gaming

## 🙏 Acknowledgments

- **Random Number Generation**: .NET's cryptographically secure Random class
- **Console Color API**: Cross-platform color support
- **Game Design**: Classic slot machine mechanics inspiration
- **User Experience**: Modern console application best practices

## 📞 Support

### Getting Help
- **🐛 Bug Reports**: Use GitHub Issues
- **💡 Feature Requests**: Submit enhancement proposals
- **❓ Questions**: Check existing documentation first

### Known Issues
- **Color Support**: Some terminals may not support all colors
- **Performance**: Minimal system requirements needed
- **Compatibility**: Requires .NET 6.0 or higher

---

**Ready to try your luck?** 🎰 **Download, compile, and start spinning!** 🎮
