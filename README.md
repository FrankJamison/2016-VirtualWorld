# Java Virtual World (Console App)

SNHU IT-511 — Object-Oriented Application Development (Final Project)

This project is a **command-line “virtual world”** application written in Java. It walks the user through creating a simple “clone” profile, optionally creating a dog profile, and then interacting with a **ShoutBox** that can output either **canned** or **randomly generated** messages.

The code is intentionally object-oriented and interactive (uses `Scanner` on `System.in`), showcasing:

- constructors and method overloading
- encapsulation via getters/setters
- input validation (regex + bounded numeric ranges)
- collection usage (`HashMap`, `ArrayList`)

---

## Features

### 1) Create a person “clone” (`MyClone`)

- Prompts for first name, last name, age, gender, height, weight, hair color, and eye color
- Validates inputs (e.g., numeric ranges, word validation)
- Prints a confirmation summary

The app also introduces a **preset clone** (“Frank”) before prompting the user.

### 2) Optional dog profile (`MyDog`)

- Asks whether you own a dog
- If yes, prompts for dog name, breed, age, gender, size, weight, hair color, eye color
- Prints a confirmation summary

The app also introduces a **preset dog** (“Baby”) before prompting the user.

### 3) ShoutBox (`ShoutBox`)

The ShoutBox supports two modes:

- **Preset mode**: includes pre-filled canned messages and word lists
- **Custom mode**: lets the user enter:
	- a chosen number of canned messages
	- a chosen number of words per list (subject/verb/adjective/object/adverb)

During interaction you can choose:

- **Canned Message**: select from the list
- **Random Message**: generated from the word lists (Subject + Verb + Adjective + Object + Adverb)

You can continue shouting messages until you answer “N”.

---

## Project Layout

This repository is intentionally small and is made up of these source files:

- `VirtualWorld.java` — program entry point (`main`), overall flow, and shared Y/N prompt helper
- `MyClone.java` — the user “clone” model + input gathering/validation + introduction/confirmation printing
- `MyDog.java` — the dog model + input gathering/validation + introduction/confirmation printing
- `ShoutBox.java` — shoutbox creation/customization and message generation

All source files declare the package:

```java
package VirtualWorld;
```

---

## Requirements

- Java JDK (a `javac` compiler)
- A terminal capable of interactive input

No third-party libraries are required.

---

## How to Build & Run (Windows)

Open a terminal in the project folder and run:

### Option A: Compile to an `out` directory (recommended)

```bat
cd /d d:\Programming\Java\2016-VirtualWorld

rem Compile (creates the package folder structure under out\)
javac -d out *.java

rem Run
java -cp out VirtualWorld.VirtualWorld
```

### Option B: Compile into the current directory

```bat
cd /d d:\Programming\Java\2016-VirtualWorld

rem Compile (creates .\VirtualWorld\*.class)
javac -d . *.java

rem Run
java VirtualWorld.VirtualWorld
```

### Clean build artifacts

If you used Option A:

```bat
rmdir /s /q out
```

If you used Option B:

```bat
rmdir /s /q VirtualWorld
```

---

## What to Expect When Running

The app is **interactive**. It will:

1. Introduce a preset clone
2. Ask for your personal details and confirm them
3. Introduce a preset dog
4. Ask whether you own a dog; if yes, collect dog details and confirm them
5. Ask whether you want a custom ShoutBox or a preset one
6. Let you shout messages (canned or random) until you stop

For Y/N prompts, enter `Y`/`y` or `N`/`n`.

---

## Notes / Known Quirks

- The code compares some strings using `==` (e.g., checking presets and message types). In Java, string equality should typically use `.equals(...)`. Depending on the JVM and how strings are created, this may cause certain checks to behave unexpectedly.
- Several methods create new `Scanner(System.in)` instances instead of reusing one shared scanner. This is fine for a small console app, but it’s generally cleaner to share a single scanner.

---

## License

Educational project (coursework). If you want an explicit open-source license added (MIT/Apache-2.0/etc.), say which one and I can add it.
