# Easy Game Center [![](http://img.shields.io/badge/Swift-1.2-blue.svg)]() [![](http://img.shields.io/badge/iOS-7.0%2B-blue.svg)]() [![](http://img.shields.io/badge/iOS-8.0%2B-blue.svg)]() [![](https://img.shields.io/packagist/l/doctrine/orm.svg)]()

<p align="center">
        <img src="http://s2.postimg.org/jr6rlurax/easy_Game_Center_Swift.png" height="200" width="200" />
</p>
<p align="center">
        <img src="https://img.shields.io/badge/Easy Game Center-2.0-D8B13C.svg" />
</p>
**Easy Game Center** helps to manage Game Center in iOS. Report and track high scores, achievements. Easy Game Center falicite management of Game Center.  

<p align="center">
        
        <img src="http://g.recordit.co/K1I3O6BEXq.gif" height="500" width="280" />
</p>

# Project Features
Easy Game Center is a great way to use Game Center in your iOS app.

* Swift
* Submit, Save, Retrieve any Game Center leaderboards, achievements in only one line of code.
* GKachievements & GKachievementsDescription are save in cache and automatically refreshed
* Delegate fucntion when player is connected or not etc...
* Most of the functions callBack (Handler, completion)
* Useful methods and properties by use Singleton (EasyGameCenter.exampleFunction)
* Just drag and drop the files into your project (EasyGameCenter.swift)
* Easy Game Center is asynchronous
* Frequent updates to the project based on user issues and requests  
* Example project
* Easily contribute to the project :)
* More is coming ... (Multiplayer etc..)

## Requirements
[![](http://img.shields.io/badge/Swift-1.2-blue.svg)]()

[![](http://img.shields.io/badge/iOS-7.0%2B-blue.svg)]() 

[![](http://img.shields.io/badge/iOS-8.0%2B-blue.svg)]()

[![](https://img.shields.io/badge/Easy Game Center-2.0-D8B13C.svg)]()

## Contributions & Share
* Any contribution is more than welcome! You can contribute through pull requests and issues on GitHub. :D
* Send me your application's link, if you use Easy Game center, I will add on the cover page and for support [@RedWolfStudioFR](https://twitter.com/RedWolfStudioFR) :)

# Documentation
## Setup
Setting up Easy Game Center it's really easy. Read the instructions after.

**1.** Add the `GameKit`, `SystemConfiguration` frameworks to your Xcode project
<p align="center">
        <img src="http://s27.postimg.org/45wds3jub/Capture_d_cran_2558_03_20_19_56_34.png" height="100" width="500" />
</p>

**2.** Add the following classes (GameCenter.swift) to your Xcode project (make sure to select Copy Items in the dialog)

**3.** You can initialize Easy Game Center by using the following method call (This is an example, see doc)
```swift
// Add Protocol for delegate fonction "EasyGameCenterDelegate"
class MainViewController: UIViewController,EasyGameCenterDelegate {
    override func viewDidLoad() {
        super.viewDidLoad()
        // Init Easy Game Center
        EasyGameCenter.sharedInstance(self)
        // If you doesn't want see message Easy Game Center, delete this ligne
        EasyGameCenter.debugMode = true
    }

    override func viewDidAppear(animated: Bool) {
        super.viewDidAppear(animated)
        //Set New view controller delegate, that's when you change UIViewController
        EasyGameCenter.delegate = self
    }
    /**
        Player conected to Game Center, Delegate Func of Easy Game Center
    */
    func easyGameCenterAuthentified() {
        println("\nPlayer Authentified\n")
    }
    /**
        Player not connected to Game Center, Delegate Func of Easy Game Center
    */
    func easyGameCenterNotAuthentified() {
        println("\nPlayer not authentified\n")
    }
    /**
        When GkAchievement & GKAchievementDescription in cache, Delegate Func of Easy Game Center
    */
    func easyGameCenterInCache() {
        println("\nGkAchievement & GKAchievementDescription in cache\n")
    }
}
```

## Initialize
###Protocol Easy Game Center
* **Description :** You should add **EasyGameCenterDelegate** protocol if you want use delegate functions (**easyGameCenterAuthentified,easyGameCenterNotAuthentified,easyGameCenterInCache**)
* **Option :** It is optional (if you do not use the functions, do not add)
```swift
    class ExampleViewController: UIViewController,EasyGameCenterDelegate { }
```
###Initialize Easy Game Center
* **Description :** You should setup Easy Game Center when your app is launched. I advise you to **viewDidLoad()** method
```swift
    override func viewDidLoad() {
        super.viewDidLoad()

        // Init Easy Game Center
        EasyGameCenter.sharedInstance(self)
    }
```
###Set new delegate when you change UIViewController
* **Description :** If you have several UIViewController just add this in your UIViewController for set new Delegate
* **Option :** It is optional 
```swift
    override func viewDidAppear(animated: Bool) {
        super.viewDidAppear(animated)

        //Set New view controller delegate, that's when you change UIViewController
        EasyGameCenter.delegate = self
    }
```
##Delegate function for listen
###Listener Player is authentified
* **Description :** This function is call when player is authentified to Game Center
* **Option :** It is optional 
```swift
    func easyGameCenterAuthentified() {
        println("\nPlayer Authentified\n")
    }
```
###Listener Player is not authentified
* **Description :** This function is call when player is not authentified to Game Center
* **Option :** It is optional 
```swift
    func easyGameCenterNotAuthentified() {
        println("\nPlayer not authentified\n")
    }
```
###Listener when Achievement is in cache
* **Description :** This function is call when GKachievements GKachievementsDescription is in cache
* **Option :** It is optional 
```swift
    func easyGameCenterInCache() {
        println("\nGkAchievement & GKAchievementDescription in cache\n")
    }
```
#Show Methods
##Show Achievements
* **Show Game Center Achievements with completion**
* **Option :** Without completion 
```swift 
    EasyGameCenter.showGameCenterAchievements()
```
* **Option :** With completion
```swift
    EasyGameCenter.showGameCenterAchievements { 
        (isShow) -> Void in
        if isShow {
                println("Game Center Achievements is shown")
        }
    }
```
##Show Leaderboard
* **Show Game Center Leaderboard  with completion**
* **Option :** Without completion 
```swift
    EasyGameCenter.showGameCenterLeaderboard(leaderboardIdentifier: "IdentifierLeaderboard")
```
* **Option :** With completion
```swift
    EasyGameCenter.showGameCenterLeaderboard(leaderboardIdentifier: "IdentifierLeaderboard") { 
        (isShow) -> Void in
        if isShow {
            println("Game Center Leaderboards is shown")
        }
    }
```
##Show Challenges
* **Show Game Center Challenges  with completion**
* **Option :** Without completion 
```swift 
    EasyGameCenter.showGameCenterChallenges()
```
* **Option :** With completion 
```swift
    EasyGameCenter.showGameCenterChallenges {
        (isShow) -> Void in
        if isShow {
            println("Game Center Challenges Is shown")
        }
    }
```
##Show authentification page Game Center
* **Show Game Center authentification page with completion**
* **Option :** Without completion 
```swift
    EasyGameCenter.showGameCenterAuthentication()
```
* **Option :** With completion 
```swift
    EasyGameCenter.showGameCenterAuthentication { 
        (result) -> Void in
        if result {
            println("Game Center Authentication is open")
        }
    }
```
##Show custom banner
* **Show custom banner Game Center with completion**
* **Option :** Without completion 
```swift
    EasyGameCenter.showCustomBanner(title: "Title", description: "My Description...")
```
* **Option :** With completion 
```swift
    EasyGameCenter.showCustomBanner(title: "Title", description: "My Description...") { 
        () -> Void in
        println("Custom Banner is finish to Show")
    }
```
##Show custom dialog
* **Show custom dialog Game Center Authentication with completion**
* **Option :** Without completion
```swift
    EasyGameCenter.openDialogGameCenterAuthentication(
        titre: Title", 
        message: "Please login you Game Center", 
        buttonOK: "Cancel", 
        buttonOpenGameCenterLogin: "Open Game Center")
```
* **Option :** With completion
```swift
    EasyGameCenter.openDialogGameCenterAuthentication(
        titre: "Title", 
        message: "Please login you Game Center", 
        buttonOK: "Ok", 
        buttonOpenGameCenterLogin: "Open Game Center") {
            (openGameCenterAuthentification) -> Void in
            if openGameCenterAuthentification {
                println("Player open Game Center authentification")
            } else {
                println("Player cancel Open Game Center authentification")
            }
        }
```
#Achievements Methods
##Progress Achievements
* **Add progress to an Achievement with show banner**
* **Option :** Report achievement 
```swift
EasyGameCenter.reportAchievement(progress: 42.00, achievementIdentifier: "Identifier")
```
* **Option :** Without show banner 
```swift 
    EasyGameCenter.reportAchievement(progress: 42.00, achievementIdentifier: "Identifier", showBannnerIfCompleted: false)
```
* **Option :** Add progress to existing (addition to the old)
```swift
    EasyGameCenter.reportAchievement(progress: 42.00, achievementIdentifier: "Identifier", addToExisting: true)
```
* **Option :** Without show banner & add progress to existing (addition to the old)
```swift
    EasyGameCenter.reportAchievement(progress: 42.00, achievementIdentifier: "Identifier", showBannnerIfCompleted: false ,addToExisting: true)
```
##If Achievement completed 
* **Is completed Achievement**
```swift
    if EasyGameCenter.isAchievementCompleted(achievementIdentifier: "Identifier") {
        println("Yes")
    } else {
        println("No")
    }
```
##All Achievements completed for banner not show
* **Get All Achievements completed and banner not show**
```swift
    if let achievements : [GKAchievement] = EasyGameCenter.getAchievementCompleteAndBannerNotShowing() {
        for oneAchievement in achievements  {
            println("\n[Easy Game Center] Achievement where banner not show \(oneAchievement.identifier)\n")
        }
    } else {
        println("\n[Easy Game Center] No Achievements with banner not showing\n")
    }
```
##Show all Achievements completed for banner not show
* **Show All Achievements completed and banner not show with completion**
* **Option :** Without completion 
```swift
EasyGameCenter.showAllBannerAchievementCompleteForBannerNotShowing()
```
* **Option :** With completion 
```swift
    EasyGameCenter.showAllBannerAchievementCompleteForBannerNotShowing { 
        (achievementShow) -> Void in
        if let achievementIsOK = achievementShow {
            println("\n[Easy Game Center] Achievement show is \(achievementIsOK.identifier)\n")
        } else {
            println("\n[Easy Game Center] No Achievements with banner not showing\n")
        }
    }
```
##Achievements GKAchievementDescription
* **Get all achievements descriptions (GKAchievementDescription) with completion**
```swift
    EasyGameCenter.getGKAllAchievementDescription {
        (arrayGKAD) -> Void in
        if let arrayAchievementDescription = arrayGKAD {
            for achievement in arrayAchievementDescription  {
                println("\n[Easy Game Center] ID : \(achievement.identifier)\n")
                println("\n[Easy Game Center] Title : \(achievement.title)\n")
                println("\n[Easy Game Center] Achieved Description : \(achievement.achievedDescription)\n")
                println("\n[Easy Game Center] Unachieved Description : \(achievement.unachievedDescription)\n")
            }
        }
    }
```
##Achievements GKAchievement
* **Get One Achievement (GKAchievement)**
```swift
    if let achievement = EasyGameCenter.getAchievementForIndentifier(identifierAchievement: "AchievementIdentifier") {
        println("\n[Easy Game Center] ID : \(achievement.identifier)\n")
    }
```
##Tuple Achievements GKAchievement GKAchievementDescription
* **Get Tuple ( GKAchievement , GKAchievementDescription) for identifier Achievement**
```swift
    EasyGameCenter.getTupleGKAchievementAndDescription(achievementIdentifier: "AchievementIdentifier") {            
        (tupleGKAchievementAndDescription) -> Void in
        if let tupleInfoAchievement = tupleGKAchievementAndDescription {
            // Extract tuple
            let gkAchievementDescription = tupleInfoAchievement.gkAchievementDescription
            let gkAchievement = tupleInfoAchievement.gkAchievement
            // The title of the achievement.
            println("\n[Easy Game Center] Title : \(gkAchievementDescription.title)\n")
            // The description for an unachieved achievement.
            println("\n[Easy Game Center] Achieved Description : \(gkAchievementDescription.achievedDescription)\n")
        }
    }
```
##Achievement progress
* **Get Progress to an achievement**
```swift
let progressAchievement = EasyGameCenter.getProgressForAchievement(achievementIdentifier: "AchievementIdentifier")
```
##Reset all Achievements
* **Reset all Achievement**
* **Option :** Without completion 
```swift
    EasyGameCenter.resetAllAchievements()
```
```swift
    EasyGameCenter.resetAllAchievements { 
        (achievementReset) -> Void in
        println("\n[Easy Game Center] ID : \(achievementReset.identifier)\n")
    }
```
#Leaderboards
##Report
* **Report Score Leaderboard**
```swift
    EasyGameCenter.reportScoreLeaderboard(leaderboardIdentifier: "LeaderboardIdentifier", score: 100)
```
##Get GKLeaderboard
* **Get GKLeaderboard with completion**
```swift
    EasyGameCenter.getGKLeaderboard { 
        (resultArrayGKLeaderboard) -> Void in
        if let resultArrayGKLeaderboardIsOK = resultArrayGKLeaderboard as [GKLeaderboard]? {
            for oneGKLeaderboard in resultArrayGKLeaderboardIsOK  {
                println("\n[Easy Game Center] ID : \(oneGKLeaderboard.identifier)\n")
                println("\n[Easy Game Center] Title :\(oneGKLeaderboard.title)\n")
                println("\n[Easy Game Center] Loading ? : \(oneGKLeaderboard.loading)\n")
            }
        }
    }
```
##Get GKScore
* **Get GKScore Leaderboard with completion**
```swift
    EasyGameCenter.getGKScoreLeaderboard(leaderboardIdentifier: "LeaderboardIdentifier") {
        (resultGKScore) -> Void in
        if let resultGKScoreIsOK = resultGKScore as GKScore? {
            println("\n[Easy Game Center] Leaderboard Identifier : \(resultGKScoreIsOK.leaderboardIdentifier)\n")
            println("\n[Easy Game Center] Date : \(resultGKScoreIsOK.date)\n")
            println("\n[Easy Game Center] Rank :\(resultGKScoreIsOK.rank)\n")
            println("\n[Easy Game Center] Hight Score : \(resultGKScoreIsOK.value)\n")
        }
    }
```
##Get Hight Score (Tuple)
* **Get Hight Score Leaderboard with completion, (Tuple of name,score,rank)**
```swift
    EasyGameCenter.getHighScore(leaderboardIdentifier: "LeaderboardIdentifier") {
        (tupleHighScore) -> Void in
        //(playerName:String, score:Int,rank:Int)?
        if let tupleIsOk = tupleHighScore {
            println("\n[Easy Game Center] Leaderboard Identifier : \(tupleIsOk.playerName)\n")
            println("\n[Easy Game Center] Date : \(tupleIsOk.score)\n")
            println("\n[Easy Game Center] Rank :\(tupleIsOk.rank)\n")
        }
    }
```
#Other methods Game Center
##Player identified to Game Center
**Is player identified to gameCenter**
```swift
if EasyGameCenter.isPlayerIdentifiedToGameCenter() { /* Player identified */ } 
```
##Local Player
**Get local Player (GKLocalPlayer)**
```swift
let localPlayer = EasyGameCenter.getLocalPlayer()
```
#Other
**Is Connected to NetWork**
```swift
if EasyGameCenter.isConnectedToNetwork() { /* You have network */ } 
```
#Debug Mode
**If you doesn't want see message of Easy Game Center**
```swift
// If you doesn't want see message Easy Game Center, delete this ligne
// EasyGameCenter.debugMode = true
```
### Legacy support
For support of iOS 7+ & iOS 8+ [@RedWolfStudioFR](https://twitter.com/RedWolfStudioFR) 

Yannick Stephan works hard to have as high feature parity with **Easy Game Center** as possible. 

### License
The MIT License (MIT)

Copyright (c) 2015 Red Wolf Studio, Yannick Stephan

[Red Wolf Studio](http://www.redwolfstudio.fr)

[Yannick Stephan](http://yannickstephan.com)
