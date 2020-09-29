Programming Exercise
====================

**Instructions for Users:**

To start the program run the main function at /my-chat/src/main/java/com/mindlinksoft/recruitment/mychat/MyChat.java with the following parameters:

input file   |  Path to the input file  |  E.g. C:\Inputs\input.txt  |  *Mandatory*

output file  |  Path to the output file |  E.g. C:\Outputs\output.txt   |  *Mandatory*
   
-u <user>   |  Only messages sent by the user specified will be outputted. Case sensitive.   |  E.g. -u bob   |  *Optional*
   
-k <keyword>   |  Only messages containing the keyword will be outputted. Case sensitive. |  E.g. -k pie   |  *Optional*
   
-b <blacklist> |  The blacklist word will be replaced by *redacted* in the output. Case sensitive.   |  E.g. -b Hello	|  *Optional*
   
-h |  Any 16-digit card numbers found in messages will be replaced by *redacted* and any UK mobile number will be replaced by *redacted*  |  E.g. -h |  *Optional*

-o |  All user Ids will be obfuscated by an encryption key using AES.   |  E.g. -o |  *Optional*

<br />

The input file and output file parameters are mandatory and must always be the first and second parameters respectively. Any combination of the optional parameters may also be used.

<br />
<br />

**Developer Notes:**

*	The Factory Pattern design was used for the message filters so they could be place in separate classes implementing the Message Filter Interface. This Factory Pattern design has not been Implemented elsewhere in the code base, as there is no need for it at the moment. However, it could be utilised in the future for example if the program needed to read or write to different file types. An interface and class implementer already exists to accommodate for this, but a factory could also be used to remove the dependency to a specific reader or writer class in the Exporter class. For now, this is not necessary.
*	Exceptions are now logged with the original type and the message. 
*	The obfuscating function has been changed to properly encrypt user ids, improving security.
*	Unit tests have been updated to match the new design and include extra empty messages tests.

<br />
<br />
<br />

This is a skeleton application to be used as part of a software development interview.

Instructions
------------

* Treat this code as if you owned this application, do whatever you feel is necessary to make this your own.
* There are several deliberate design, code quality and test issues that should be identified and resolved.
* Below is a list of the current features supported by the application; as well as additional features that have been requested by the business owner.
* In order to work on this take a fork into your own GitHub area; make whatever changes you feel are necessary and when you are satisfied submit back via a pull request. See details on GitHub's [Fork & Pull](https://help.github.com/articles/using-pull-requests) model
* Be sure to put your name in the pull request comment so your work can be easily identified.
* The project is written utilising some Java 8 features (java.time), we encourage using Java 7 or 8, but this is your project now, so you are free to choose a different version.
* The project uses maven to resolve dependencies however if you want to avoid maven configuration the only external JARs that are required is junit-4.12 and gson-2.5.
* Refactor and add features (from the below list) as you see fit; there is no need to add all the features in order to "complete" the exercise.
* We will only consider candidates that implemented at least the "essential" features.
* Keep in mind that code quality is the critical measure and there should be an obvious focus on __TESTING__.
* REMEMBER: this is YOUR code, make any changes you feel are necessary.
* You're welcome to spend as much time as you like.
* The code will be a representation of your work, so it's important that all the code--new and pre-existing--is how you want your work to be seen.  Please make sure that you are happy with ALL the code.

#### Things We Value

* Good code structure - separation of concerns,
* A well-formed exception model,
* Tidy code,
* Application of appropriate design patterns,
* Unit tests.

#### Things To Avoid At All Costs

* Throwing general exception,
* Magic strings,
* Methods that do everything,
* No testing.

my-chat
-------

### Essential Features

* A user can export a conversation from a given file path stored in the following file format into a JSON file at the given output path:
```
<conversation_name><new_line>
(<unix_timestamp><space><username><space><message><new_line>)*
```
* Messages can be filtered by a specific user
    * The user can be provided as a command-line argument (how the argument is specified is up to you)
    * All messages sent by the specified user are written to the JSON output
    * Messages sent by any other user are not written to the JSON output
* Messages can be filtered by a specific keyword
    * The keyword can be specified as a command-line argument
    * All messages sent containing the keyword are written to the JSON output
    * Messages sent that do not contain the keyword are not written to the JSON output
* Hide specific words
    * A blacklist can be specified as a command-line argument
    * Any blacklisted word is replaced with "\*redacted\*" in the output.

### Additional Features

Implementing any of these features well will make your submission stand-out. Features listed here are ordered from easy to hard.

* Hide credit card and phone numbers
    * A flag can be specified to hide credit card and phone numbers
    * Any identified credit card or phone numbers are replaced with "\*redacted\*" in the output.
* Obfuscate user IDs
    * A flag can be specified to obfuscate user IDs
    * All user IDs are obfuscated in the output.
    * The same original user ID in any single export is replaced with the same obfuscated user ID i.e. messages retain their relationship with the sender, only the ID that represents the sender is changed.
* A report is added to the conversation that details the most active users
    * The most active user in a conversation is the user who sent the most messages.
    * Most active users are added to the JSON output as an array ordered by activity.
    * The number of messages sent by each user is included.
