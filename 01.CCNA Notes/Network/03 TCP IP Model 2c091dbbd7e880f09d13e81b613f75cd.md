# 03. TCP/IP Model

# The Complete Beginner’s Guide to the TCP/IP Model: How the Internet REALLY Works

![image.png](03%20TCP%20IP%20Model/image.png)

## What Is the TCP/IP Model?

Remember the OSI Model we learned about? That was the **theory** - the textbook explanation. The **TCP/IP Model** is what the internet **actually uses** in real life!

**Think of it this way:**
- **OSI Model** = The blueprint architects use to design a house
- **TCP/IP Model** = The actual house you live in

The TCP/IP Model tells us which **protocols** (sets of rules) are used to make everything work behind the scenes.

### Quick Comparison: OSI vs TCP/IP

| OSI Model | TCP/IP Model |
| --- | --- |
| **7 Layers** | **4 Layers** |
| Layer 7, 6, 5: Application, Presentation, Session | **Application Layer** (combines all 3) |
| Layer 4: Transport | **Transport Layer** (same) |
| Layer 3: Network | **Internet Layer** (same idea, different name) |
| Layer 2, 1: Data Link, Physical | **Network Access Layer** (combines both) |

**Why fewer layers?** TCP/IP is more practical - it combines layers that work closely together.

---

## The 4 Layers of TCP/IP Model

### **Layer 4: Application Layer** 📱

**What it is:** All the protocols that make your apps work

This layer combines the OSI Model’s Application, Presentation, and Session layers. It contains all the protocols (rules) that run the services you use every day.

---

## Application Layer Protocols (What Makes the Internet Work)

### **1. HTTP and HTTPS** 🌐

**What they do:** Open websites

- **HTTP** = HyperText Transfer Protocol (the basic version, **unsecure**)
- **HTTPS** = HyperText Transfer Protocol Secure (the **encrypted** version with a padlock 🔒)

**Real-world example:** Every time you visit a website, you’re using HTTP or HTTPS. Look at your browser’s address bar right now - you’ll see “https://” at the beginning of the URL (web address).

**Which one to use?**
- Old websites might use HTTP
- Modern websites (99% of them) use HTTPS because it encrypts your data
- Never enter credit card info on HTTP sites - only on HTTPS!

**Fun fact:** When you type “www.google.com” in your browser, HTTPS is the protocol that actually loads the page for you.

---

### **2. FTP and TFTP** 📁

**What they do:** Upload and download files

- **FTP** = File Transfer Protocol (**slow but secure**)
- **TFTP** = Trivial File Transfer Protocol (**fast but unsecure**)

**Real-world example:**
- When companies back up their website files to servers, they use FTP
- When network engineers update router software, they might use TFTP because speed matters more than security in a controlled environment

**The trade-off:** You can have it secure or fast, but not both!

---

### **3. SMTP and POP** 📧

**What they do:** Send and receive emails

Let’s use Gmail as an example:

1. **HTTPS** opens the Gmail website (www.gmail.com)
2. **SMTP** (Simple Mail Transfer Protocol) **sends** your email when you hit “send”
3. **POP** (Post Office Protocol) **receives** emails into your inbox

**Think of it like postal mail:**
- HTTPS = Walking into the post office building
- SMTP = Mailing a letter (sending)
- POP = Checking your mailbox (receiving)

**Port numbers they use:**
- SMTP: Port 25 or 587
- POP: Port 110

---

### **4. DNS (Domain Name System)** 🗺️

**What it does:** Translates website names into IP addresses

This is one of the MOST important protocols on the internet!

**The problem DNS solves:**
Computers don’t understand “www.google.com” - they only understand numbers (IP addresses like 142.250.185.78).

**How it works:**

1. You type “www.groundtograde.com” in your browser
2. Your computer asks your **ISP** (Internet Service Provider - your internet company like Comcast or Verizon): “What’s the IP address for this website?”
3. Your ISP asks the **DNS Server**: “Hey DNS, what IP address goes with groundtograde.com?”
4. DNS Server responds: “That website is hosted at IP address 123.234.56.78”
5. Your ISP tells your computer: “Send your request to 123.234.56.78”
6. Your computer sends the request to that IP address
7. The website loads!

**This happens in milliseconds** - you never even notice!

**Real-world analogy:**
- **Website name** = A person’s name (“John Smith”)
- **IP address** = Their phone number (555-1234)
- **DNS** = Your phone’s contacts app (looks up the name and gives you the number)

You remember “John Smith” easier than “555-1234”, right? Same with websites!

**DNS Records:**
DNS maintains a giant database that looks like this:

| Website Name | IP Address |
| --- | --- |
| google.com | 142.250.185.78 |
| facebook.com | 157.240.241.35 |
| groundtograde.com | 123.234.56.78 |

**Port number:** DNS uses Port 53

**Pro tip:** Try this experiment:
1. Open Command Prompt (CMD)
2. Type: `ping google.com`
3. You’ll see Google’s IP address appear!
4. Type: `ping 8.8.8.8` (works fine - this is Google’s DNS server IP)
5. Type: `ping www.google.com` (also works - DNS translated it!)

If `ping 8.8.8.8` works but `ping www.google.com` doesn’t, your DNS is broken!

---

### **5. NTP (Network Time Protocol)** ⏰

**What it does:** Automatically updates your device’s time and date

**Remember old phones?** If the battery died, you had to manually reset the time. Now your phone’s time updates automatically - that’s NTP!

**How it works:**
- Your device connects to an **NTP Server** (a computer dedicated to telling accurate time)
- The NTP server syncs your device’s clock with atomic clocks around the world
- Your time stays accurate automatically

**Port number:** NTP uses Port 123

---

### **6. NNTP (Network News Transfer Protocol)** 📰

**What it does:** Delivers online news and updates

All online news platforms use this protocol:
- NDTV, CNN, BBC News websites
- Instagram news/reels
- Reddit posts
- Any news feed on apps

**Port number:** NNTP uses Port 119

---

## Summary of Application Layer Protocols

| Protocol | Purpose | Port Number | Example |
| --- | --- | --- | --- |
| **HTTP** | Load websites (unsecure) | 80 | Old websites |
| **HTTPS** | Load websites (secure) | 443 | Modern websites |
| **FTP** | File transfer (slow, secure) | 20, 21 | Website backups |
| **TFTP** | File transfer (fast, unsecure) | 69 | Router updates |
| **SMTP** | Send emails | 25, 587 | Sending Gmail |
| **POP** | Receive emails | 110 | Receiving Gmail |
| **DNS** | Translate names to IPs | 53 | Finding websites |
| **NTP** | Sync time/date | 123 | Phone clock update |
| **NNTP** | News delivery | 119 | News websites |

**Remember:** These are all protocols used by the apps you interact with daily!

---

## **Layer 3: Transport Layer** 🚚

This layer has only **TWO protocols**: TCP and UDP. We covered these in the OSI Model guide, but let’s go DEEPER into how they actually work.

### The Two Transport Protocols

| Feature | TCP | UDP |
| --- | --- | --- |
| **Full Name** | Transmission Control Protocol | User Datagram Protocol |
| **Connection** | Connection-Oriented | Connectionless |
| **Reliability** | Reliable (guarantees delivery) | Unreliable (no guarantee) |
| **Speed** | Slower | Faster |
| **Error Checking** | Yes (with retransmission) | No |
| **Window Size** | Adjustable | Fixed |
| **Use Cases** | Emails, file downloads, web browsing | Video calls, gaming, live streaming |

---

### TCP: The Reliable But Slow Protocol

**Think of TCP like registered mail:**
- You get a tracking number
- The post office confirms delivery
- If it gets lost, they resend it
- Takes longer but you’re guaranteed delivery

### The TCP 3-Way Handshake 🤝

![image.png](03%20TCP%20IP%20Model/image%201.png)

Before sending ANY data, TCP performs a “handshake” - a three-step confirmation process.

**Real-world analogy - Playing Catch:**

**Step 1 - SYN (Synchronize):**
- You: “Hey, ready to catch? I’m about to throw!”
- (Sender says: “I want to send data”)

**Step 2 - SYN-ACK (Synchronize-Acknowledge):**
- Friend: “Yes, I’m ready! Go ahead and throw!”
- (Receiver says: “I’m ready to receive”)

**Step 3 - ACK (Acknowledge):**
- You: “Okay, I’m throwing it now!”
- (Sender confirms: “Starting to send data”)

Only AFTER these three steps does the actual data transfer begin!

**Why so slow?** All this back-and-forth confirmation takes time. But it ensures:
- Both sides are ready
- Data arrives in the correct order
- Lost data gets resent
- Nothing gets corrupted

**Sequence Numbers:**
TCP breaks data into segments and numbers them (Segment 1, Segment 2, Segment 3…). If Segment 2 gets lost, the receiver says “Hey, I’m missing #2, resend it!” and TCP will resend just that segment.

---

### UDP: The Fast But Unreliable Protocol

**Think of UDP like shouting across a room:**
- You just shout and hope they hear
- No confirmation
- If they miss something, oh well
- But it’s INSTANT

**Why use UDP if it’s unreliable?**

Because **SPEED** matters more than perfection in:

1. **Video calls (Zoom, FaceTime):**
    - If a few milliseconds of audio drop, the call continues
    - Better to have a tiny glitch than pause the entire call
2. **Online gaming:**
    - If one frame of data is lost, the game moves on
    - You can’t wait for retransmission - the game would lag
3. **Live streaming:**
    - Missing one frame out of 30 frames per second isn’t noticeable
    - Pausing to resend would ruin the experience

**No handshake:** UDP just starts blasting data. No “Are you ready?” - it just sends!

---

### Window Size: The Traffic Control System

**Window Size** = How many packets can be sent per second

**Think of it like a highway:**
- **Small window size** = 2-lane highway (slow but controlled)
- **Large window size** = 10-lane highway (fast but can get congested)

**TCP’s Advantage:**
- Adjusts window size automatically
- If the receiver is slow, TCP reduces the window size
- If the connection is fast, TCP increases the window size

**Example:**
- Sender can send 1000 packets per second
- But receiver can only process 700 packets per second
- **TCP** adjusts down to 700 - no data lost
- **UDP** keeps sending 1000 - 300 packets get dropped

**Flow Control:** TCP prevents fast senders from overwhelming slow receivers.

---

## Port Numbers: How One IP Address Handles Multiple Tasks

### The Apartment Building Analogy

Imagine your IP address is an **apartment building address**: “123 Main Street”

**Problem:** How does the mailman know which apartment to deliver to?

**Solution:** Apartment numbers! “123 Main Street, Apartment 5B”

In networking:
- **IP Address** = Building address
- **Port Number** = Apartment number
- **Socket** = Complete address (IP + Port)

### Port Number Ranges

Port numbers are **16-bit numbers**, which means:
- Range: 0 to 65,535 (that’s 65,536 possible ports!)

**The three ranges:**

| Range | Name | Purpose | Example |
| --- | --- | --- | --- |
| **0 - 1023** | Well-Known Ports | Reserved for common services | HTTP (80), HTTPS (443), SMTP (25) |
| **1024 - 64,511** | Dynamic/Private Ports | Used by clients/browsers | Your browser tabs use these |
| **64,512 - 65,535** | Reserved Ports | Special applications | Custom apps, games |

### How Port Numbers Work in Real Life

Let’s say you open **5 tabs** in your browser:

**Your computer’s IP:** 192.168.1.100

**What the computer does:**

| Tab | Website | Your Socket | Server Socket |
| --- | --- | --- | --- |
| Tab 1 | google.com | 192.168.1.100:54231 | 142.250.185.78:443 |
| Tab 2 | facebook.com | 192.168.1.100:54232 | 157.240.241.35:443 |
| Tab 3 | youtube.com | 192.168.1.100:54233 | 172.217.16.206:443 |
| Tab 4 | twitter.com | 192.168.1.100:54234 | 104.244.42.193:443 |
| Tab 5 | reddit.com | 192.168.1.100:54235 | 151.101.65.140:443 |

**Notice:**
- Your IP (192.168.1.100) is the same for all tabs
- But each tab gets a **different port number** (54231, 54232, 54233…)
- The server always uses port **443** (standard HTTPS port)

**This is how one computer can handle multiple connections at once!**

### See Your Port Numbers Right Now!

**Try this on Windows:**

1. Open Command Prompt (press Windows key + R, type “cmd”, press Enter)
2. Type: `netstat`
3. Press Enter

**You’ll see something like:**

```
Proto  Local Address          Foreign Address        State
TCP    192.168.1.100:54231   142.250.185.78:443     ESTABLISHED
TCP    192.168.1.100:54232   157.240.241.35:443     ESTABLISHED
TCP    192.168.1.100:54233   172.217.16.206:443     ESTABLISHED
```

**Translation:**
- **Proto:** Protocol (TCP or UDP)
- **Local Address:** Your computer’s IP:Port
- **Foreign Address:** The server’s IP:Port (where you’re connected)
- **State:** Connection status
- **ESTABLISHED:** Connected right now
- **TIME_WAIT:** Connection just closed, waiting for cleanup
- **LISTENING:** Waiting for incoming connections

**Experiment:**
1. Open 3-4 different websites in separate tabs
2. Run `netstat` again
3. Notice each tab has a different port number!
4. Close all tabs
5. Run `netstat` one more time
6. Watch as connections change to “TIME_WAIT” then disappear

---

### Common Well-Known Port Numbers (You Should Memorize These!)

| Port | Protocol | What It Does |
| --- | --- | --- |
| **20, 21** | FTP | File transfers |
| **22** | SSH | Secure remote access |
| **23** | Telnet | Unsecure remote access (outdated) |
| **25** | SMTP | Sending emails |
| **53** | DNS | Domain name lookups |
| **67, 68** | DHCP | Automatic IP assignment |
| **80** | HTTP | Unsecure websites |
| **110** | POP3 | Receiving emails |
| **143** | IMAP | Email management |
| **443** | HTTPS | Secure websites |
| **3389** | RDP | Remote Desktop (Windows) |

**Pro tip for job interviews:** Memorize at least ports 80, 443, 22, 25, and 53!

---

## **Layer 2: Internet Layer** 🗺️

In the OSI Model, this was called the **Network Layer**. In TCP/IP, it’s called the **Internet Layer**. Same concept, different name!

**Protocols at this layer:**
- **IP** (Internet Protocol) - IPv4 and IPv6
- **ICMP** (Internet Control Message Protocol) - used for ping and error messages
- **IGMP** (Internet Group Message Protocol) - used for streaming to multiple devices
- **IPsec** - used for VPN security

**Main job:** Routing packets across the internet using IP addresses

**We already covered IP extensively in the OSI guide**, so we won’t repeat it here. The key thing to remember: IP provides the logical addressing and routing to get data from source to destination.

---

## **Layer 1: Network Access Layer** 🔌

This layer combines the OSI Model’s **Data Link Layer** and **Physical Layer**.

**Main job:**
- Physical addressing (MAC addresses)
- Handling the actual physical transmission (cables, WiFi)

---

## MAC Addresses: The Permanent Hardware ID

### What Is a MAC Address?

**MAC** = Media Access Control

Think of it like a **serial number** burned into your device’s network card (NIC - Network Interface Card) at the factory.

**Key differences: IP Address vs MAC Address**

| IP Address | MAC Address |
| --- | --- |
| **Logical address** (can change) | **Physical address** (permanent) |
| 32-bit (IPv4) or 128-bit (IPv6) | 48-bit |
| Decimal notation (192.168.1.1) | Hexadecimal notation (00:1A:2B:3C:4D:5E) |
| Assigned by network/router | Assigned by manufacturer |
| Changes when you change networks | Never changes (stays with device) |
| Layer 3 (Network/Internet Layer) | Layer 2 (Data Link/Network Access Layer) |

### MAC Address Format

**Example:** `00:1A:2B:3C:4D:5E`

**Breaking it down:**

- **48 bits total** = 12 hexadecimal digits
- **Separated by colons** (:) or hyphens (-)
- Can be uppercase or lowercase (no difference)

**What is hexadecimal?**
A number system that uses 16 digits instead of 10:
- **Decimal:** 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 (10 digits)
- **Hexadecimal:** 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F (16 digits)

**Why use hexadecimal?**
- More compact than binary (101010 vs A)
- Easier than decimal for computers
- Standard in networking

**Conversion examples:**
- 10 in decimal = A in hexadecimal
- 11 in decimal = B in hexadecimal
- 15 in decimal = F in hexadecimal
- 16 in decimal = 10 in hexadecimal

---

### MAC Address Structure: OUI and NIC

Every MAC address has two parts:

**Format:** `XX:XX:XX:YY:YY:YY`

1. **First 6 digits (XX:XX:XX):** OUI - Organizationally Unique Identifier
    - Identifies the **manufacturer**
    - Assigned by IEEE (Institute of Electrical and Electronics Engineers)
2. **Last 6 digits (YY:YY:YY):** NIC - Network Interface Controller specific
    - The device’s unique **serial number**
    - Assigned by the manufacturer

**Example:** `00:1A:2B:3C:4D:5E`

- **00:1A:2B** = OUI (tells you who made the device)
    - This might be Dell, HP, Apple, Samsung, etc.
- **3C:4D:5E** = NIC-specific (serial number for this specific device)

**Real-world analogy:**
- **OUI** = Car manufacturer badge (Ford, Toyota, Honda)
- **NIC-specific** = Vehicle Identification Number (VIN)

**Why this matters:**
Every network card in the world has a **unique** MAC address. No two devices should ever have the same MAC address!

---

### How to Check Your MAC Address

**On Windows:**

**Method 1:**
1. Open Command Prompt (CMD)
2. Type: `ipconfig /all`
3. Press Enter
4. Look for “Physical Address” - that’s your MAC address!

**Method 2:**
1. Open Command Prompt
2. Type: `getmac`
3. Press Enter
4. Your MAC address(es) appear!

**You might see multiple MAC addresses because:**
- WiFi adapter has one
- Ethernet port has another
- Bluetooth has another
- Virtual network adapters have their own

**Each network interface gets its own MAC address!**

---

### Why We Need BOTH IP and MAC Addresses

**You might wonder:** If MAC addresses are unique, why do we need IP addresses?

**Here’s why we need both:**

**MAC Address:**
- Works only on **local networks** (same building/WiFi)
- Never changes
- Hardware-level identification
- Used by switches

**IP Address:**
- Works **across the internet** (worldwide)
- Can change
- Software-level identification

- Used by routers

**Real-world analogy:**

Imagine sending a package from New York to Los Angeles:

1. **IP Address** = The destination city and street address (Los Angeles, 123 Main St)
    - Gets the package across the country (through routers)
2. **MAC Address** = The apartment/house number (Apartment 5B)
    - Gets the package to the exact door (through switches)

**The delivery process:**
1. You send a package from NYC to LA (uses **IP addresses** for routing across the country)
2. Package arrives in LA at a local post office
3. Local delivery person uses the **house number** (like MAC address) to find the exact house on Main Street

**In networking:**
1. Data travels across the internet using **IP addresses** (through multiple routers)
2. Data arrives at the destination network
3. The local switch uses **MAC addresses** to deliver to the exact device

**You need BOTH for internet communication to work!**

---

## How TCP/IP Actually Works: Complete Example

Let’s watch a Gmail email travel from your computer to Google’s servers:

**Setup:**
- Your computer IP: 192.168.1.100
- Your computer MAC: 00:1A:2B:3C:4D:5E
- Gmail server IP: 142.250.185.78
- Gmail server MAC: AB:CD:EF:12:34:56

**Step-by-step:**

### 1. Application Layer

- You type an email in Gmail
- Click “Send”
- **HTTPS** loads the Gmail interface
- **SMTP** protocol prepares to send the email

### 2. Transport Layer

- **TCP** breaks the email into segments
- Adds port numbers:
    - **Source port:** 54231 (your browser)
    - **Destination port:** 443 (Gmail’s HTTPS port)
- Performs 3-way handshake with Gmail server
- Creates segments with sequence numbers

**Data now looks like:**

```
[TCP Header with Ports] + [Email Data Segment 1]
[TCP Header with Ports] + [Email Data Segment 2]
[TCP Header with Ports] + [Email Data Segment 3]
```

### 3. Internet Layer

- **IP** adds IP addresses:
    - **Source IP:** 192.168.1.100
    - **Destination IP:** 142.250.185.78
- **DNS** was already used to convert “gmail.com” to 142.250.185.78
- Routers use these IP addresses to route packets across the internet

**Data now looks like:**

```
[IP Header with IPs] + [TCP Header] + [Email Data]
```

### 4. Network Access Layer

- **Ethernet** adds MAC addresses:
    - **Source MAC:** 00:1A:2B:3C:4D:5E
    - **Destination MAC:** Your router’s MAC (first hop)
- Converts everything to bits (1s and 0s)
- Sends through WiFi or ethernet cable

**Data now looks like:**

```
[Ethernet Header with MACs] + [IP Header] + [TCP Header] + [Email Data] + [Ethernet Trailer]
```

**The data travels:**
- Through your router (which changes the MAC addresses for each hop)
- Through your ISP’s network
- Through multiple internet routers (using IP addresses)
- Until it reaches Google’s data center
- Finally to Gmail’s server

**On the receiving end, the process reverses:**
1. Network Access Layer removes Ethernet header/trailer
2. Internet Layer removes IP header
3. Transport Layer removes TCP header and reassembles segments
4. Application Layer delivers the email to Gmail

**The recipient sees your email in their inbox!**

---

## Why TCP/IP Is Called “TCP/IP”

**Fun fact:** This model could’ve been called the “HTTP/IP Model” or “SMTP/UDP Model” or any combination!

**Why TCP/IP?**
Because **TCP** and **IP** are the **two most important protocols**:
- **TCP** handles reliable delivery (Transport Layer)
- **IP** handles addressing and routing (Internet Layer)

Together, they form the backbone of internet communication!

---

## Key Differences: OSI vs TCP/IP (Summary)

| Aspect | OSI Model | TCP/IP Model |
| --- | --- | --- |
| **Layers** | 7 | 4 |
| **Purpose** | Theoretical framework | Practical implementation |
| **Created by** | ISO | DARPA (US Department of Defense) |
| **Used for** | Teaching & troubleshooting | Actual internet |
| **Protocol specific** | No (just concepts) | Yes (actual protocols) |
| **Flexibility** | Very structured | More flexible |

**Both are important:**
- **OSI Model** = Great for learning concepts and troubleshooting
- **TCP/IP Model** = What actually runs the internet

---

## TCP/IP Model Cheat Sheet

### Layer 4: Application

**Purpose:** User-facing protocols
**Protocols:** HTTP, HTTPS, FTP, SMTP, POP, DNS, NTP, NNTP
**Devices:** None (software only)
**PDU:** Data

### Layer 3: Transport

**Purpose:** End-to-end delivery
**Protocols:** TCP, UDP
**Devices:** None (software only)
**PDU:** Segment
**Uses:** Port numbers (0-65,535)

### Layer 2: Internet

**Purpose:** Routing across networks
**Protocols:** IP (IPv4/IPv6), ICMP, IGMP
**Devices:** Routers
**PDU:** Packet
**Uses:** IP addresses

### Layer 1: Network Access

**Purpose:** Physical transmission
**Protocols:** Ethernet, WiFi, PPP
**Devices:** Switches, NICs, cables
**PDU:** Frame (then bits)
**Uses:** MAC addresses (48-bit)

---

## Important Formulas to Remember

**Socket** = IP Address + Port Number
- Example: 192.168.1.100:443

**MAC Address** = OUI (6 hex digits) + NIC-specific (6 hex digits)
- Example: 00:1A:2B:3C:4D:5E

**Port Number Range** = 0 to 65,535 (2^16 - 1)

**MAC Address Bits** = 48 bits = 12 hex digits

**IP Address Bits** = 32 bits (IPv4) or 128 bits (IPv6)

---

## Commands You Should Know

| Command | What It Does | Example |
| --- | --- | --- |
| `ipconfig` | Shows your IP address | `ipconfig` |
| `ipconfig /all` | Shows detailed network info including MAC | `ipconfig /all` |
| `getmac` | Shows just your MAC address | `getmac` |
| `netstat` | Shows active connections and ports | `netstat` |
| `ping [address]` | Tests connection to an address | `ping google.com` |
| `ping [IP]` | Tests connection to an IP | `ping 8.8.8.8` |

**Try them all right now in Command Prompt (CMD) on Windows!**

---

## Real-World Troubleshooting with TCP/IP

When things go wrong, use the TCP/IP model to troubleshoot:

**Problem:** “I can’t load any websites!”

**Troubleshooting steps:**

1. **Check Network Access Layer:**
    - Is your ethernet cable plugged in?
    - Is WiFi connected?
    - Do you have a MAC address? (Run `getmac`)
2. **Check Internet Layer:**
    - Do you have an IP address? (Run `ipconfig`)
    - Can you ping your router? (Run `ping 192.168.1.1`)
    - Can you ping an external IP? (Run `ping 8.8.8.8`)
3. **Check Transport Layer:**
    - Are your connections working? (Run `netstat`)
    - Try a different port (use HTTP instead of HTTPS)
4. **Check Application Layer:**
    - Does DNS work? (Run `ping google.com`)
    - Try a different browser
    - Clear browser cache

**If Step 2 fails but Step 1 works:** Your router or ISP has a problem

**If Step 3 works but Step 4 fails:** DNS is broken (try using 8.8.8.8 as DNS server)

---

![image.png](03%20TCP%20IP%20Model/image%202.png)