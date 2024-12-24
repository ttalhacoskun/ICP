# ICP

# PhoneBook and Messaging System

This project is a basic implementation of a **PhoneBook and Messaging System** written in Motoko. It provides functionalities to manage a phonebook and send messages, storing them for later retrieval.

---

## Features

- **PhoneBook Management**:
  - Add new contacts with their details.
  - Retrieve contact details using the contact's name.

- **Messaging System**:
  - Send messages to contacts.
  - Store and retrieve the history of messages by sender's phone number.

---

## Code Overview

### Data Structures

1. **PhoneBook**:
   - A `HashMap` where the contact name (`Name`) is used as the key, and the contact details (`Entry`) are stored as values.
   - Each `Entry` includes:
     - `desc`: A brief description of the contact.
     - `phone`: The phone number of the contact.

2. **MessageHistory**:
   - A `HashMap` where the sender's phone number (`Phone`) is the key, and the sent message (`Message`) is the value.
   - Each `Message` includes:
     - `receiver`: The recipient of the message.
     - `mess`: The content of the message.

### Key Functions

1. **insert(name: Name, entry: Entry): async ()**
   - Adds a new contact to the phonebook.

2. **sendMessage(senderPhone: Phone, message: Message): async ()**
   - Sends a message and stores it in the message history.

3. **getPhone(name: Name): async ?Entry**
   - Retrieves the contact details for a given name.

4. **getMessage(senderPhone: Phone): async ?Message**
   - Retrieves the last message sent by a given phone number.

---

## Installation and Usage

### Prerequisites

- Install the [Motoko Playground](https://m7sm4-2iaaa-aaaab-qabra-cai.raw.ic0.app/) or set up the [DFINITY SDK](https://dfinity.org/) on your local machine.

Example Usage

Run the following commands to interact with the actor:

# Add a new contact to the PhoneBook
> await Actor.insert("Alice", {desc = "Friend", phone = "123-456-7890"})

# Retrieve a contact's details by name
> let alice = await Actor.getPhone("Alice")
> alice
{ desc = "Friend"; phone = "123-456-7890" }

# Send a message from a sender to a receiver
> await Actor.sendMessage("123-456-7890", {receiver = "Bob", mess = "Hello, Bob!"})

# Retrieve message history for a sender's phone number
> let messageHistory = await Actor.getMessage("123-456-7890")
> messageHistory
{ receiver = "Bob"; mess = "Hello, Bob!" }

Motivation

This project was created to demonstrate the basic usage of Motoko's HashMap data structure and to showcase actor-based programming in Motoko.
