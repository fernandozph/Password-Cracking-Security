# Password Cracking and Security Android Application

## Description

This Android application aims to educate users about password security by allowing them to generate and crack their own passwords. Users can crack password hashes, or generate and crack their own passwords. There is also a short tutorial where users can learn more about password cracking and security in general. **Built for Google Pixel 5 API 33 and above.** App was developed following the Model-View-Controller design pattern and the Agile Development methodology.

## [Video Overview of the App](https://youtu.be/K8kAZK_qXyg)

## Functionality
Specific documentation, use case diagrams, class diagrams, etc. can be found in the [intellij directory](intellij/doc).

The app has three main use cases:
1) Generate Password : Generate a new password
   * User can choose length and whether to use numbers/symbols
   * Can copy password to clipboard
   * Option to crack the generated password to test it's security
2) Crack Password : Crack a password or password hash either by brute force or a built-in dictionary
   * Can crack plaintext passwords(the program hashes it to show the user how long it would take to crack) and password hashes
     * Must know the hash type, supports MD5 and SHA512
     * Option to add a salt to plaintext password to show users how it increases security
     * Option to not hash the plaintext password to show users how insecure plaintext is
   * Supports brute force attacks (aA-zZ 0-9 and some symbols), dictionary attack
     * Dictionary attack uses the built-in rockyou.txt dictionary
     * To use a different dictionary upload it to [the assets directory](astudio/app/src/main/assets) and change the wordlist name in ControllerActivity
   * Cracking occurs in a separate thread, supports status updates and pausing
3) Tutorial: Tutorial of how to use the app, and also information about password security and password cracking. Supports different screen sizes with scrolling.

## Limitations:
* Cracking is slower than with other cracking tools
* CrackPassword and CrackingPassword are locked vertically
* Status updates slow down cracking
* Only supports MD5 and SHA512 hashes, must know hash type
* Can't re-generate passwords

## Testing
* JUnit and Espresso tests
* The [DictionaryAttack JUnit test](astudio/app/src/androidTest/java/com/example/passwordapp/DictionaryAttackTest.java) is in the [androidTest directory](astudio/app/src/androidTest/java/com/example/passwordapp) because it needs to access the dictionary in resources

## Known Issues:
* Final time elapsed may be inaccurate in certain edge cases when cracking passwords
* [CrackPasswordFragmentTest](astudio/app/src/androidTest/java/com/example/passwordapp/CrackPasswordFragmentTest.java) may not pass due to cracking happening too fast/slow. Adjust sleepTime variable as needed.

## Authors
* Written by Fernando Panepinto Hattori and John Gador
