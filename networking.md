# 1 – What Happens When You Type a URL?

---

# 🎯 Objectives

- Explain what the Internet really is.
- Understand the roles of clients and servers.
- Describe what happens when you type a URL into a browser.
- Understand requests and responses.
- Recognize where DNS, IP addresses, TCP, and HTTP fit into the picture.
- Build a mental model for the rest of the networking module.

---

# Introduction

Suppose you open your browser and type

```text
https://github.com
```

Then press **Enter**.

Within a second, GitHub appears.

It feels almost magical.

But underneath, dozens of things happen.

Instead of memorizing networking terms, we're going to follow that single request from your keyboard to GitHub and back.

---

# The Big Picture

Everything starts here:

```text
You

↓

Browser

↓

Internet

↓

GitHub Server

↓

Internet

↓

Browser

↓

You
```

Every website works using this basic pattern.

---

# Step 1 — You Enter a URL

You type

```text
https://github.com
```

Your browser now knows:

"I need to retrieve the GitHub homepage."

But it still doesn't know:

- Where GitHub is
- Which computer hosts GitHub
- How to reach it

It only knows a name:

```text
github.com
```

---

# Step 2 — Browser Starts Working

The browser begins asking questions.

```
Question 1

What is github.com's IP address?
```

```
Question 2

Which protocol should I use?

HTTPS
```

```
Question 3

Which port?

443
```

```
Question 4

How do I send the request?
```

We'll answer each of these in later lessons.

---

# Step 3 — The Internet

Many beginners think:

> "The Internet is one huge computer."

It isn't.

The Internet is simply millions of computers connected together.

Think of it like this.

```text
Computer

↓

Router

↓

Internet

↓

Router

↓

Server
```

Every message travels from one computer to another.

---

# Step 4 — Client and Server

Networking revolves around two roles.

## Client

A client requests something.

Examples:

- Chrome
- Firefox
- Edge
- React application
- Mobile app

A client asks.

---

## Server

A server provides something.

Examples:

- GitHub
- Google
- Amazon
- FastAPI application
- PostgreSQL database

A server answers.

---

# Analogy

Imagine a restaurant.

```
Customer

↓

Waiter

↓

Kitchen

↓

Waiter

↓

Customer
```

Customer = Client

Kitchen = Server

Food = Response

Order = Request

The customer always initiates the conversation.

---

# Step 5 — Request

Your browser sends a request.

Example:

```text
GET /
Host: github.com
```

Think of it as asking:

> "Please send me your home page."

---

# Step 6 — Server Processes the Request

GitHub receives the request.

Its server:

- authenticates users
- checks permissions
- reads databases
- builds HTML
- prepares CSS
- prepares JavaScript

Then creates a response.

---

# Step 7 — Response

The server sends back:

```text
HTML

CSS

JavaScript

Images

Fonts
```

The browser receives everything.

---

# Step 8 — Browser Renders the Page

The browser:

- parses HTML
- downloads CSS
- executes JavaScript
- renders images
- builds the page

You finally see GitHub.

---

# Complete Journey

```text
You

↓

Browser

↓

DNS Lookup

↓

IP Address Found

↓

TCP Connection

↓

HTTPS Connection

↓

HTTP Request

↓

GitHub Server

↓

HTTP Response

↓

Browser Renders Page
```

This single diagram summarizes almost the entire networking module.

Each box will become one or more lessons.

---

# Another Example

Suppose your React app calls your FastAPI backend.

```text
React App

↓

http://localhost:8000/api/chat

↓

FastAPI

↓

OpenAI API

↓

FastAPI

↓

React
```

This is exactly the same pattern.

Client

↓

Server

↓

Client

---

# Everything is Client–Server

When using Git:

```text
Git

↓

GitHub
```

When using SSH:

```text
SSH Client

↓

Linux Server
```

When using PostgreSQL:

```text
Python

↓

Database Server
```

When using ChatGPT:

```text
Browser

↓

OpenAI Server
```

Almost everything you do as a developer follows the client–server model.

---

# Is Your Computer Always a Client?

No.

Your computer can also act as a server.

Example:

Run

```bash
uvicorn main:app
```

Now your computer becomes a server.

Another browser can connect to it.

Likewise:

```bash
python -m http.server
```

also turns your computer into a web server.

Computers are not permanently clients or servers.

The role depends on what they're doing.

---

# Common Misconceptions

❌ The Internet is one big computer.

✔ The Internet is a network of millions of computers.

---

❌ Servers are special machines.

✔ A server is simply software that provides a service.

---

❌ A laptop is always a client.

✔ A laptop can also be a server.

---

# Real Examples

| Client | Server |
|---------|---------|
| Chrome | GitHub |
| React | FastAPI |
| FastAPI | PostgreSQL |
| VS Code | SSH Server |
| Git | GitHub |
| Mobile App | REST API |

---

# Exercise

Open your browser.

Visit:

```text
https://github.com
```

Now answer:

1. Who is the client?
2. Who is the server?
3. Who sent the first request?
4. Who generated the response?
5. Could your laptop become the server?

---

# Key Takeaways

- The Internet is a network of connected computers.
- Communication follows the client–server model.
- Clients initiate requests.
- Servers process requests and return responses.
- A computer can act as either a client or a server.
- Every web application follows the same communication pattern.

---

# Summary

Typing a URL into a browser begins a sequence of networking events.

Your browser acts as a client, discovers the server, sends a request, receives a response, and renders the result.

Understanding this journey provides the foundation for everything else in networking, from DNS and IP addresses to HTTP, HTTPS, APIs, Docker, and cloud deployment.

---

# Lesson 2 – IP Addresses and Localhost

---

# 🎯 Objectives

- Explain what an IP address is.
- Understand why every device on a network needs one.
- Distinguish between IPv4 and IPv6.
- Explain Public vs Private IP addresses.
- Understand localhost and 127.0.0.1.
- Find your computer's IP addresses.
- Explain why localhost is used during development.

---

# Introduction

Suppose you type

```text
https://github.com
```

Your browser wants to contact GitHub.

But computers don't understand names like

```text
github.com
```

Computers communicate using numbers.

Those numbers are called **IP Addresses**.

---

# A Simple Analogy

Imagine writing a letter.

To send it, you need an address.

Example:

```text
Utpal Das

Odisha

India
```

Without an address,

the post office has no idea where to deliver it.

Computers work the same way.

Every computer connected to a network has an address.

That address is called an **IP Address**.

---

# What is an IP Address?

An IP Address is a unique identifier for a device on a network.

Think of it as:

```text
Computer Address
```

Without an IP address,

one computer cannot communicate with another.

---

# Example

Your laptop

```text
192.168.1.20
```

Router

```text
192.168.1.1
```

Another laptop

```text
192.168.1.35
```

Every device has a different address.

---

# Why Do We Need IP Addresses?

Suppose there are one million computers connected together.

When your browser sends:

```text
Open github.com
```

How does the Internet know which computer should receive the request?

It needs a destination.

That destination is the IP address.

---

# IPv4

The most common IP address format is IPv4.

Example:

```text
192.168.1.20
```

Another:

```text
142.250.183.46
```

Structure:

```text
192 . 168 . 1 . 20
```

Four numbers.

Each ranges from

```text
0

to

255
```

---

# Why Four Numbers?

Each number represents **8 bits (1 byte)**.

Therefore:

```text
8 + 8 + 8 + 8

=

32 bits
```

A 32-bit address can represent about

```text
4.3 Billion
```

unique addresses.

Years ago, people thought this would be enough forever.

It wasn't.

---

# IPv6

Because IPv4 addresses became scarce, IPv6 was introduced.

Example:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

It looks much longer.

Reason:

```text
128 bits
```

instead of

```text
32 bits
```

This provides an unimaginably large number of addresses.

---

# Should You Memorize IPv6?

No.

As developers,

you should simply know:

- IPv4 is still very common.
- IPv6 exists because IPv4 addresses were running out.
- Most development examples still use IPv4.

---

# Public IP Address

A Public IP is visible on the Internet.

Example:

```text
34.126.88.201
```

Websites,

cloud servers,

and AWS instances

usually have public IP addresses.

---

# Private IP Address

Inside your home,

your router gives every device a private address.

Examples:

```text
192.168.x.x

10.x.x.x

172.16.x.x
```

These addresses work only inside your local network.

---

# Example Home Network

```text
                 Internet
                     │
                     │
             Public IP
           103.xx.xx.xx
                     │
                Home Router
                     │
        ┌────────────┼─────────────┐
        │            │             │
        │            │             │
Laptop      Phone      Smart TV

192.168.1.20
192.168.1.21
192.168.1.22
```

Notice

Only the router has the Public IP.

Everything else uses Private IPs.

---

# Localhost

Now the most important concept for developers.

Suppose you run

```bash
uvicorn main:app
```

Your FastAPI server starts.

How do you connect?

Usually:

```text
http://localhost:8000
```

What is

```text
localhost
```

---

# Localhost

Localhost simply means

> **This computer itself**

It always points back to your own machine.

---

# 127.0.0.1

The IPv4 loopback address is

```text
127.0.0.1
```

This always means

```text
My own computer
```

Therefore

```text
http://localhost:8000
```

and

```text
http://127.0.0.1:8000
```

are usually equivalent.

---

# Why Is Localhost Useful?

Suppose you're developing:

- React
- FastAPI
- PostgreSQL

Everything runs on your own laptop.

Instead of using your actual network IP,

you use

```text
localhost
```

This is simpler and safer.

---

# Example

React

```text
http://localhost:5173
```

FastAPI

```text
http://localhost:8000
```

PostgreSQL

```text
localhost:5432
```

Notice

All three use

```text
localhost
```

but different ports.

We'll study ports next.

---

# Find Your IP Address (Linux)

Private IP:

```bash
hostname -I
```

or

```bash
ip addr
```

---

# Find Your Public IP

Run:

```bash
curl ifconfig.me
```

or visit:

```text
https://ifconfig.me
```

Notice:

Your public IP is usually different from your private IP.

---

# Why Can't Others Use My Localhost?

Suppose your FastAPI app runs here:

```text
localhost:8000
```

Your friend cannot access it.

Why?

Because

```text
localhost
```

always refers to

**their own computer**, not yours.

---

# Client and Server on the Same Machine

When developing,

both client and server can run on the same laptop.

```text
React

↓

localhost:5173

↓

FastAPI

↓

localhost:8000
```

The network still exists,

even though everything stays inside one computer.

---

# Common Misconceptions

❌ localhost means "the Internet"

✔ localhost means "this computer"

---

❌ Every computer has one IP address.

✔ A computer can have multiple IP addresses.

Example:

- Wi-Fi
- Ethernet
- VPN
- Docker network

Each can have its own IP.

---

❌ localhost and Public IP are the same.

✔ They are completely different.

---

# Real Example

You deploy FastAPI to AWS.

Development:

```text
http://localhost:8000
```

Production:

```text
http://54.218.xx.xx
```

Same application.

Different server.

Different IP.

---

# Exercise

Using WSL, run:

```bash
hostname -I
```

Observe your private IP.

Now run:

```bash
ip addr
```

Identify the network interface that has the IP address.

If you have Internet access:

```bash
curl ifconfig.me
```

Compare your public IP and private IP.

Finally, start a simple web server:

```bash
python3 -m http.server 8000
```

Open your browser:

```text
http://localhost:8000
```

Observe that your browser is talking to a server running on your own computer.

---

# Key Takeaways

- Every device on a network needs an IP address.
- IPv4 uses 32-bit addresses.
- IPv6 uses 128-bit addresses.
- Public IPs identify devices on the Internet.
- Private IPs identify devices within a local network.
- `localhost` and `127.0.0.1` refer to your own computer.
- Modern web development relies heavily on localhost during development.

---

# Summary

IP addresses are the foundation of networking.

Before one computer can communicate with another, it must know the destination's IP address.

During development, we usually communicate with services running on our own computer using `localhost`.

Understanding IP addresses prepares us for the next lesson, where we'll answer another important question:

> If one computer has only one IP address, how can it run React, FastAPI, PostgreSQL, SSH, and Docker all at the same time?

The answer lies in **Ports**.

---

# 3 – Ports: How One Computer Runs Hundreds of Applications

---

# 🎯 Objectives

- Explain what a port is.
- Understand why ports are needed.
- Distinguish between IP addresses and ports.
- Understand well-known ports.
- Explain client ports and server ports.
- Detect port conflicts.
- Inspect listening ports on Linux.
- Understand how React, FastAPI, PostgreSQL, Docker, and SSH coexist on one computer.

---

# Introduction

Last lesson we learned:

An IP address identifies a computer.

Example:

```text
192.168.1.20
```

But here's the problem.

Your laptop runs:

- Chrome
- VS Code
- FastAPI
- React
- PostgreSQL
- Docker
- SSH

They all share the same IP address.

So...

How does the operating system know which application should receive incoming network traffic?

The answer is:

**Ports.**

---

# Think of an Apartment Building

Imagine an apartment building.

The building address is:

```text
21 Park Street
```

But hundreds of families live there.

How does the postman know where to deliver a letter?

Because every apartment has a number.

```text
21 Park Street

Apartment 101

Apartment 102

Apartment 205

Apartment 501
```

The building address is like an IP address.

The apartment number is like a Port.

---

# IP Address vs Port

```text
IP Address

↓

Computer
```

```text
Port

↓

Application
```

Together they uniquely identify a service.

Example:

```text
192.168.1.20:8000
```

Means

```text
Computer

↓

192.168.1.20

Application

↓

Port 8000
```

---

# Real Examples

React

```text
localhost:5173
```

FastAPI

```text
localhost:8000
```

PostgreSQL

```text
localhost:5432
```

SSH

```text
localhost:22
```

Notice

The IP is the same.

Only the ports are different.

---

# Port Numbers

Ports range from

```text
0

↓

65535
```

There are

```text
65,536
```

possible ports.

---

# Port Categories

## Well-Known Ports

```text
0 – 1023
```

Reserved for standard services.

Examples:

```text
22    SSH

25    SMTP

53    DNS

80    HTTP

443   HTTPS
```

---

## Registered Ports

```text
1024 – 49151
```

Used by applications.

Examples:

```text
3306    MySQL

5432    PostgreSQL

6379    Redis

8000    FastAPI

8080    Development servers
```

---

## Dynamic (Ephemeral) Ports

```text
49152 – 65535
```

Temporary ports chosen automatically by the operating system for client connections.

We'll see these shortly.

---

# Client and Server Ports

Suppose your browser opens:

```text
https://github.com
```

Browser:

```text
localhost:53241
```

↓

GitHub:

```text
140.82.xx.xx:443
```

Notice:

The browser chooses a temporary port.

GitHub listens permanently on port 443.

---

# Visual

```text
Chrome

Port 53241

↓

Internet

↓

GitHub

Port 443
```

One client.

One server.

Two ports.

---

# Why Temporary Ports?

Suppose Chrome opens:

- GitHub
- Google
- YouTube

all at once.

It needs different ports.

Example:

```text
Chrome

↓

52341

↓

GitHub

443
```

```text
Chrome

↓

52342

↓

Google

443
```

```text
Chrome

↓

52343

↓

YouTube

443
```

The operating system automatically assigns these temporary ports.

---

# Listening Ports

Servers wait for incoming connections.

This is called

```text
Listening
```

Example:

FastAPI

```bash
uvicorn main:app
```

Listens on

```text
8000
```

React

```bash
npm run dev
```

Listens on

```text
5173
```

PostgreSQL

Listens on

```text
5432
```

SSH

Listens on

```text
22
```

---

# Why Can't Two Applications Use the Same Port?

Suppose FastAPI is already running:

```text
localhost:8000
```

Now start another FastAPI application on port 8000.

Result:

```text
Address already in use
```

The operating system refuses.

Only one application can listen on a particular IP/Port combination.

---

# Port Conflict Example

Terminal 1

```bash
python3 -m http.server 8000
```

Success.

Terminal 2

```bash
python3 -m http.server 8000
```

Output:

```text
OSError:

Address already in use
```

Use a different port:

```bash
python3 -m http.server 8001
```

Now it works.

---

# Viewing Open Ports

Linux provides several commands.

## ss

```bash
ss -tuln
```

Meaning

```text
-t

TCP

-u

UDP

-l

Listening

-n

Numeric
```

---

# lsof

```bash
lsof -i
```

Shows

Which process owns which port.

Example:

```text
Python

↓

8000
```

---

# netstat

Older command.

```bash
netstat -tuln
```

Still seen on some systems.

---

# Example Development Environment

Suppose you're building ResearchMind AI.

```text
React

↓

5173
```

```text
FastAPI

↓

8000
```

```text
PostgreSQL

↓

5432
```

```text
Redis

↓

6379
```

```text
Ollama

↓

11434
```

All running simultaneously.

How?

Different ports.

---

# Docker Example

Docker containers expose ports.

Example:

```bash
docker run -p 8080:80 nginx
```

Meaning:

```text
Computer

↓

8080

↓

Container

↓

80
```

We'll revisit this in the Docker module.

---

# AWS Example

Suppose your FastAPI application is deployed.

Development:

```text
http://localhost:8000
```

Production:

```text
http://54.201.xx.xx:8000
```

Same application.

Different IP.

Same port.

---

# Common Ports Every Developer Should Know

| Port | Service |
|------:|---------|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 6379 | Redis |
| 8000 | FastAPI (common) |
| 8080 | Web servers / proxies |
| 5173 | Vite React Development Server |
| 3000 | React / Node.js (common) |

Don't memorize all of them.

You'll naturally remember the ones you use often.

---

# Exercise

Run a simple web server:

```bash
python3 -m http.server 8000
```

Open:

```text
http://localhost:8000
```

Now open another terminal.

Inspect listening ports:

```bash
ss -tuln
```

Can you find port 8000?

Now stop the server.

Run:

```bash
python3 -m http.server 8001
```

Visit:

```text
http://localhost:8001
```

Observe the difference.

---

# Common Mistakes

❌ Thinking ports belong to applications.

✔ Ports belong to the operating system's networking stack and are assigned to processes.

---

❌ Thinking every application has a fixed port.

✔ Many applications allow their listening port to be changed.

---

❌ Thinking localhost and port identify different computers.

✔ The IP identifies the computer.

✔ The port identifies the application on that computer.

---


# Key Takeaways

- An IP address identifies a computer.
- A port identifies an application running on that computer.
- Multiple applications can share the same IP because they use different ports.
- Servers listen on well-known or configured ports.
- Clients use temporary (ephemeral) ports.
- Port conflicts occur when two processes attempt to listen on the same IP/port combination.

---

# Summary

Ports allow multiple networked applications to coexist on a single computer.

Every network connection is identified by both an IP address and a port number.

Understanding ports is essential for developing web applications, configuring databases, using Docker, deploying to the cloud, and debugging networking issues.

---

# 4 – DNS: How Does `github.com` Become an IP Address?

---

# 🎯 Objectives

- Explain what DNS is.
- Understand why DNS exists.
- Explain how a DNS lookup works.
- Understand DNS caching.
- Use `nslookup`, `dig`, and `host`.
- Explain why DNS failures occur.
- Understand where DNS fits into the networking process.

---

# Recap

From previous lessons, we know:

Every computer has an IP address.

Example:

```text
140.82.114.4
```

Browsers communicate using IP addresses.

But...

You never type

```text
https://140.82.114.4
```

Instead, you type

```text
https://github.com
```

How does that become an IP address?

DNS.

---

# What is DNS?

DNS stands for

```text
Domain Name System
```

Think of DNS as

```text
The Internet's Phone Book
```

It translates

```text
github.com
```

into

```text
140.82.xx.xx
```

Without DNS,

you would need to remember the IP address of every website.

---

# Real-Life Analogy

Imagine your phone.

You call:

```text
Mom
```

You don't remember

```text
+91-9876543210
```

Your phone looks up the number.

DNS works exactly the same way.

```text
github.com

↓

140.82.xx.xx
```

---

# The Journey Begins

You type

```text
https://github.com
```

Browser asks:

```text
Do I already know the IP?
```

If yes,

use it.

If no,

ask DNS.

---

# DNS Lookup

Simplified process:

```text
Browser

↓

DNS Resolver

↓

DNS Server

↓

IP Address

↓

Browser
```

The browser now knows where GitHub lives.

---

# Complete Flow

```text
You

↓

Browser

↓

DNS Lookup

↓

IP Address

↓

TCP Connection

↓

HTTPS

↓

HTTP Request

↓

GitHub Server
```

DNS is just one step in the journey.

---

# What is a Domain Name?

Examples:

```text
github.com

google.com

openai.com

python.org
```

Humans prefer names.

Computers prefer numbers.

DNS connects the two.

---

# DNS Records

A domain can contain different types of records.

Common ones:

| Record | Purpose |
|---------|----------|
| A | Maps a domain to an IPv4 address |
| AAAA | Maps a domain to an IPv6 address |
| CNAME | Alias for another domain |
| MX | Mail server |
| TXT | Additional information (verification, SPF, etc.) |

For web developers,

A and CNAME are the most common.

---

# Example

Suppose

```text
api.example.com
```

might point to

```text
203.0.113.10
```

while

```text
www.example.com
```

could simply be an alias:

```text
www.example.com

↓

example.com
```

---

# DNS Caching

Imagine opening GitHub.

One minute later,

you open GitHub again.

Should your computer ask DNS again?

No.

It remembers.

This is called

```text
DNS Cache
```

---

# Why Cache?

Without caching,

every website visit would require another DNS lookup.

Caching makes browsing much faster.

---

# Where is DNS Cached?

Several places.

```text
Browser

↓

Operating System

↓

Router

↓

ISP

↓

DNS Server
```

Each layer may already know the answer.

---

# Public DNS Servers

Some popular public DNS services:

| Provider | DNS Address |
|----------|-------------|
| Google | 8.8.8.8 |
| Google | 8.8.4.4 |
| Cloudflare | 1.1.1.1 |
| Cloudflare | 1.0.0.1 |

Your computer may use:

- your ISP's DNS
- Google's DNS
- Cloudflare's DNS

depending on your configuration.

---

# Why Can DNS Fail?

Sometimes you see:

```text
DNS_PROBE_FINISHED_NXDOMAIN
```

or

```text
Server not found
```

Possible reasons:

- Typo in the domain
- DNS server unavailable
- No Internet connection
- Domain doesn't exist

Notice:

The web server may be perfectly healthy.

Your computer simply couldn't find its IP address.

---

# Useful Commands

## nslookup

```bash
nslookup github.com
```

Example output:

```text
Name: github.com

Address: 140.82.xx.xx
```

---

## dig

```bash
dig github.com
```

Provides much more detail:

- IP address
- DNS server used
- Record type
- Time to live (TTL)

---

## host

```bash
host github.com
```

Simple output:

```text
github.com has address 140.82.xx.xx
```

---

# What Happens Next?

Once DNS returns the IP:

```text
github.com

↓

140.82.xx.xx
```

The browser now knows

which computer to contact.

Next step:

Open a TCP connection.

---

# Real Example

Suppose you're developing ResearchMind.

Frontend:

```text
researchmind.ai
```

DNS might point to

```text
203.0.113.45
```

API:

```text
api.researchmind.ai
```

could point to

```text
203.0.113.46
```

Both are easy for humans to remember,

even though the computers communicate using IP addresses.

---

# Development vs Production

Development:

```text
localhost
```

No DNS needed.

Production:

```text
app.example.com
```

DNS lookup is required.

---

# Common Misconceptions

❌ Browsers use domain names directly.

✔ Browsers first resolve the domain name into an IP address.

---

❌ Every website has one fixed IP forever.

✔ Large websites often use multiple IP addresses that can change over time.

---

❌ DNS belongs to the browser.

✔ DNS is a distributed Internet service used by many applications.

---

# Exercise

Using WSL, run:

```bash
nslookup github.com
```

Now run:

```bash
host github.com
```

Finally:

```bash
dig github.com
```

Compare the outputs.

Observe:

- IP address
- Record type
- DNS server

---

# Key Takeaways

- DNS stands for Domain Name System.
- DNS translates domain names into IP addresses.
- Browsers cannot contact a website until they know its IP address.
- DNS caching improves performance.
- Public DNS servers include Google (8.8.8.8) and Cloudflare (1.1.1.1).
- Commands like `nslookup`, `dig`, and `host` help inspect DNS.

---

# Summary

DNS is the Internet's naming system.

It allows humans to use memorable names like `github.com` while computers continue communicating using IP addresses.

Without DNS, every web request would require users to remember numerical IP addresses.

Understanding DNS brings us one step closer to completing the entire networking journey from typing a URL to loading a webpage.

---

# The Story So Far

```text
You
   │
   ▼
Browser
   │
   ▼
DNS Lookup
   │
   ▼
IP Address Found
   │
   ▼
???
```

We still have one unanswered question.

Now that we know the server's IP address...

**How does the browser actually establish a reliable connection to that server?**

That is the job of **TCP**, which we'll study next.

---

# 5 – TCP: How Two Computers Establish a Reliable Connection

---

# 🎯 Objectives

- Explain what TCP is.
- Understand why TCP exists.
- Explain the Three-Way Handshake.
- Understand packets.
- Understand acknowledgements.
- Explain why TCP is called reliable.
- Understand where TCP fits in web applications.

---

# Recap

We now know:

```text
github.com

↓

DNS

↓

140.82.xx.xx
```

Great.

Now your browser knows the destination.

But can it simply start sending data?

No.

First, both computers must agree to communicate.

---

# Real-Life Analogy

Imagine making a phone call.

You don't immediately start talking.

Instead:

```
You:

Hello?

↓

Friend:

Hello!

↓

You:

Can you hear me?

↓

Friend:

Yes.
```

Only then does the conversation begin.

TCP works similarly.

---

# What is TCP?

TCP stands for

```text
Transmission Control Protocol
```

Think of TCP as

> A reliable conversation between two computers.

It ensures that:

- data arrives
- data arrives in order
- missing data is retransmitted
- duplicate data is ignored

---

# Why Not Simply Send Data?

Suppose your browser sends

```
Hello GitHub
```

What if

- the network drops part of it?
- packets arrive out of order?
- packets arrive twice?

Without TCP,

the receiver wouldn't know.

---

# TCP Solves These Problems

TCP guarantees:

✔ Reliable delivery

✔ Correct order

✔ Error detection

✔ Retransmission

---

# The Three-Way Handshake

Before sending any web request,

TCP creates a connection.

This process is called the

```text
Three-Way Handshake
```

---

# Step 1

Browser says

```text
SYN
```

Meaning:

> I'd like to communicate.

---

# Step 2

Server replies

```text
SYN + ACK
```

Meaning:

> I received your request.

> I'm ready.

---

# Step 3

Browser responds

```text
ACK
```

Meaning:

> Great.

Let's begin.

---

# Visual

```text
Browser                    Server

   SYN  -------------------->

        <----------------  SYN + ACK

   ACK  -------------------->
```

Connection established.

Only now can HTTP begin.

---

# Why Three Steps?

Imagine only one step.

Browser:

```
Hello
```

What if the message never arrived?

Neither side knows.

The handshake ensures that 
both computers agree that communication is ready.

---

# Packets

Computers do not send huge files as one block.

Suppose you're downloading a

```
500 MB video
```

It is divided into many small pieces called

```text
Packets
```

Example:

```text
Packet 1

Packet 2

Packet 3

Packet 4

Packet 5
```

---

# Why Packets?

Imagine mailing a library.

Instead of one gigantic box, 
you send many smaller boxes.

If one box is lost, you resend only that box.

Networking works the same way.

---

# Packet Journey

Suppose GitHub sends

```text
HTML
```

The HTML may be split into

```text
Packet 1

Packet 2

Packet 3
```

Each packet travels independently across the Internet.

---

# Packets Can Arrive Out of Order

Suppose

Packet 3

arrives first.

Then

Packet 1.

Then

Packet 2.

TCP rearranges them correctly.

Result:

```text
Packet 1

↓

Packet 2

↓

Packet 3
```

Application receives the correct order.

---

# Acknowledgements (ACK)

After receiving data,

the receiver replies

```text
ACK
```

Meaning

> I received it.

If ACK never arrives,

the sender assumes the packet was lost.

It sends it again.

---

# Lost Packet Example
```
Sender


Packet 1


↓

Receiver

Received


↓

ACK

---

Sender

Packet 2


↓

Lost

↓

No ACK

↓

Resend Packet 2
```

TCP automatically handles this.

---

# Why TCP is Reliable

TCP keeps track of:

- packet numbers
- acknowledgements
- missing packets
- duplicate packets

Applications don't need to worry.

TCP does it for them.

---

# Where Does HTTP Fit?

Many beginners think:

```
Browser

↓

HTTP

↓

Server
```

Actually,

TCP comes first.

The real order is

```text
Browser

↓

DNS

↓

TCP Connection

↓

HTTP Request

↓

HTTP Response
```

HTTP rides on top of TCP.

---

# Real Example

Suppose React calls

```text
http://localhost:8000/api/chat
```

Sequence:

```text
React

↓

DNS (localhost)

↓

TCP

↓

FastAPI

↓

HTTP Request

↓

HTTP Response
```

Exactly the same.

---

# Git Example

Clone repository

```bash
git clone
```

Git uses

```text
TCP

↓

HTTPS
```

or

```text
TCP

↓

SSH
```

Both depend on TCP.

---

# SSH Example

```bash
ssh ubuntu@server
```

TCP first.

Then

SSH protocol.

---

# PostgreSQL Example

Python

↓

TCP

↓

Port 5432

↓

PostgreSQL

Even databases communicate using TCP.

---

# Common Misconceptions

❌ HTTP creates the connection.

✔ TCP creates the connection.

---

❌ TCP sends files.

✔ TCP sends packets.

---

❌ Applications must reorder packets.

✔ TCP does it automatically.

---

# Exercise

Open two terminals.

Start a simple web server:

```bash
python3 -m http.server 8000
```

In another terminal:

```bash
curl http://localhost:8000
```

Observe that the request succeeds.

Later, when we study HTTP,

we'll inspect the actual HTTP request.

---

# Key Takeaways

- TCP establishes a reliable connection between two computers.
- Before data is exchanged, TCP performs a Three-Way Handshake.
- Large data is divided into packets.
- TCP guarantees ordered and reliable delivery.
- HTTP, HTTPS, SSH, Git, and PostgreSQL all rely on TCP.

---

# Summary

TCP is the foundation of reliable communication on the Internet.

Before a browser sends an HTTP request, it establishes a TCP connection with the server using the Three-Way Handshake.

TCP then ensures that packets arrive correctly, in order, and without loss, allowing higher-level protocols such as HTTP and HTTPS to function reliably.

---

# Story So Far

```text
You
   │
   ▼
Browser
   │
   ▼
DNS Lookup
   │
   ▼
IP Address Found
   │
   ▼
TCP Three-Way Handshake
   │
   ▼
???
```

One mystery remains.

Now that the connection exists...

> **What exactly does the browser send to ask for a webpage?**

That question introduces **HTTP**, the language spoken between browsers and web servers.

---

# 6 – HTTP: The Language of the Web

---

# 🎯 Objectives

- Explain what HTTP is.
- Understand the Request–Response model.
- Understand HTTP methods.
- Read HTTP requests.
- Read HTTP responses.
- Understand status codes.
- Explain why REST APIs use HTTP.

---

# Our Story So Far

We have already completed these steps.

```text
You

↓

Browser

↓

DNS

↓

IP Address

↓

TCP Connection
```

Now the browser finally sends:

```text
HTTP Request
```

The server replies:

```text
HTTP Response
```

---

# What is HTTP?

HTTP stands for

```text
HyperText Transfer Protocol
```

Think of HTTP as

> The language spoken between clients and servers.

The browser speaks HTTP.

The server understands HTTP.

---

# Real-Life Analogy

Imagine you're in a restaurant.

Customer:

> I'd like one coffee.

Waiter:

> Certainly.

Kitchen prepares the coffee.

Waiter returns with the coffee.

This is exactly HTTP.

Customer

↓

Request

↓

Kitchen

↓

Response

---

# HTTP is Stateless

This is one of HTTP's most important properties.

Every request is independent.

Example

Request 1

```
GET /login
```

finished.

Later

Request 2

```
GET /profile
```

The server does **not automatically remember** Request 1.

Each request starts fresh.

We'll later see how cookies, sessions, and JWT solve this.

---

# HTTP Request

A browser sends a request.

Example

```http
GET / HTTP/1.1
Host: github.com
User-Agent: Chrome
Accept: text/html
```

Let's understand each line.

---

# Line 1

```http
GET / HTTP/1.1
```

Means

```
Method

↓

GET

```

```
Path

↓

/

```

```
Protocol

↓

HTTP/1.1
```

---

# Host Header

```http
Host: github.com
```

Tells the server

> I want github.com

One server can host many websites.

---

# User-Agent

```http
User-Agent: Chrome
```

Tells the server

which browser sent the request.

---

# Accept

```http
Accept: text/html
```

Means

> I would like HTML.

---

# HTTP Response

Server replies.

Example

```http
HTTP/1.1 200 OK

Content-Type: text/html

Content-Length: 2345

<html>

...

</html>
```

---

# Response Structure

Status Line

↓

Headers

↓

Blank Line

↓

Body

---

# Status Codes

Every HTTP response begins with a status code.

Example

```text
200
```

Meaning

Success.

---

# Most Important Status Codes

## 200 OK

Everything worked.

---

## 201 Created

A new resource was created.

Example

New user registered.

---

## 204 No Content

Success.

Nothing to return.

---

## 301 Moved Permanently

Resource moved.

Browser automatically redirects.

---

## 304 Not Modified

Browser already has the latest copy.

No need to download again.

---

## 400 Bad Request

Client sent invalid data.

---

## 401 Unauthorized

Login required.

---

## 403 Forbidden

You are authenticated,

but not allowed.

---

## 404 Not Found

Resource doesn't exist.

---

## 500 Internal Server Error

Server crashed.

---

## 503 Service Unavailable

Server temporarily unavailable.

---

# Status Code Categories

```text
1xx

Information
```

```text
2xx

Success
```

```text
3xx

Redirection
```

```text
4xx

Client Errors
```

```text
5xx

Server Errors
```

You don't need to memorize every code.

Just understand the categories.

---

# HTTP Methods

HTTP methods describe

what the client wants to do.

---

## GET

Retrieve data.

Example

```http
GET /users
```

Meaning Return users.

---

## POST

Create something.

```http
POST /users
```

Meaning

Create a new user.

---

## PUT

Replace an existing resource.

Example

```http
PUT /users/10
```

Replace user 10.

---

## PATCH

Update only part of a resource.

Example

```http
PATCH /users/10
```

Change only the email address.

---

## DELETE

Delete something.

```http
DELETE /users/10
```

Delete user 10.

---

# REST API Example

Suppose FastAPI exposes

```text
/users
```

Operations

```text
GET

↓

Read users
```

```text
POST

↓

Create user
```

```text
PUT

↓

Replace user
```

```text
PATCH

↓

Update user
```

```text
DELETE

↓

Delete user
```

Exactly the same URL.

Different methods.

---

# Example Request

```http
POST /users

Content-Type: application/json

{
  "name":"Utpal"
}
```

---

# Example Response

```http
HTTP/1.1 201 Created

{
  "id":25,
  "name":"Utpal"
}
```

---

# Browser Example

You open

```text
https://github.com
```

Browser sends

```http
GET /
```

GitHub responds

```http
200 OK
```

with HTML.

---

# React Example

React sends

```http
GET /api/chat
```

FastAPI replies

```json
{
  "answer":"Hello!"
}
```

React updates the page.

---

# Why APIs Use HTTP

Because every browser already understands HTTP.

Every programming language supports HTTP.

Every cloud provider supports HTTP.

HTTP became the universal language of the web.

---

# Is HTTP Only for Browsers?

No.

Git

↓

HTTP

Python

↓

HTTP

React

↓

HTTP

Mobile Apps

↓

HTTP

FastAPI

↓

HTTP

Almost everything uses HTTP.

---

# Common Misconceptions

❌ HTTP and HTML are the same.

✔ HTML is content.

✔ HTTP transports the content.

---

❌ GET changes data.

✔ GET should only retrieve data.

---

❌ HTTP only works for browsers.

✔ Any application can use HTTP.

---

# Exercise

Run your FastAPI application:

```bash
uvicorn main:app --reload
```

Open:

```text
http://localhost:8000/docs
```

Open Developer Tools → Network.

Refresh the page.

Observe:

- Request Method
- Status Code
- Headers
- Response

Now run:

```bash
curl http://localhost:8000
```

Observe the HTTP response.

---

# Key Takeaways

- HTTP is the communication protocol used by web clients and servers.
- Communication follows the Request–Response model.
- Every request contains a method, path, headers, and optionally a body.
- Every response contains a status code, headers, and optionally a body.
- REST APIs are built on top of HTTP.
- HTTP itself is stateless.

---

# Summary

HTTP is the language of the web.

After DNS identifies the server and TCP establishes a reliable connection, HTTP defines how clients request resources and how servers respond.

Every modern web framework—including FastAPI, Express, Spring Boot, Django, and ASP.NET—uses HTTP as its primary communication protocol.

Understanding HTTP is essential for building APIs, debugging applications, and designing scalable web services.

---

# Story So Far

```text
You
   │
   ▼
Browser
   │
   ▼
DNS Lookup
   │
   ▼
IP Address Found
   │
   ▼
TCP Connection
   │
   ▼
HTTP Request
   │
   ▼
HTTP Response
   │
   ▼
Browser Renders the Page
```

We've almost completed the journey from typing a URL to seeing a webpage.

One final question remains:

> **If HTTP sends everything as plain text, how can we safely send passwords, credit card numbers, and authentication tokens over the Internet?**

That is solved by **HTTPS**, which we'll study in the next lesson.

---

# 7 – HTTPS: Securing Communication on the Internet

---

# 🎯 Learning Objectives

- Explain why HTTP is insecure.
- Understand encryption.
- Explain HTTPS.
- Understand SSL and TLS.
- Understand Digital Certificates.
- Understand Certificate Authorities (CA).
- Explain the TLS Handshake.
- Understand how HTTPS protects passwords and API keys.

---

# The Problem with HTTP

Suppose you log in to GitHub.

Your browser sends:

```http
POST /login

username=utpal

password=secret123
```

If this travels using plain HTTP,

anyone who can observe the network can read it.

```text
Browser

↓

Internet

↓

GitHub
```

Everything is plain text.

---

# Imagine Sending a Postcard

Think about sending a postcard.

```
Dear Friend,

Meet me tomorrow.

- Utpal
```

Anyone handling the postcard can read it.

HTTP is like a postcard.

---

# HTTPS is Like a Locked Envelope

Instead of a postcard, put the letter inside a sealed envelope.

Now the post office still delivers it, but cannot read it.

HTTPS works exactly this way.

---

# What is HTTPS?

HTTPS stands for

```text
HyperText Transfer Protocol Secure
```

It is simply:

```text
HTTP

+

TLS Encryption
```

Notice carefully.

HTTPS is **not** a completely different protocol.

It is HTTP running over an encrypted connection.

---

# HTTP vs HTTPS

HTTP

```text
Browser

↓

Plain Text

↓

Server
```

HTTPS

```text
Browser

↓

Encrypted Data

↓

Server
```

The messages are still HTTP.

Only the transport is encrypted.

---

# What is Encryption?

Encryption converts readable information into unreadable data.

Example

Original

```text
password123
```

Encrypted

```text
7f91d8aab41e0c4...
```

Without the correct key, the encrypted data is useless.

---

# Why Encryption Matters

Suppose someone intercepts your traffic.

With HTTP:

```text
username = utpal

password = secret123
```

They can read everything.

With HTTPS:

```text
A91FC8C7E4B98D...
```

They see meaningless encrypted bytes.

---

# SSL vs TLS

You will hear both names.

Historically:

```text
SSL

↓

Older protocol
```

Today:

```text
TLS

↓

Modern protocol
```

People still say:

```
SSL Certificate
```

even though almost all websites actually use TLS.

---

# Digital Certificate

How do you know you're talking to GitHub and not an attacker pretending to be GitHub?

The server presents a

```text
Digital Certificate
```

Think of it like an ID card.

It proves:

> "I really am github.com."

---

# Certificate Contains

A certificate includes:

- Domain name
- Public key
- Issuing Certificate Authority
- Expiration date
- Digital signature

---

# Certificate Authority (CA)

Who issues these certificates?

Trusted organizations called

```text
Certificate Authorities
```

Examples:

- Let's Encrypt
- DigiCert
- GlobalSign
- Sectigo

Browsers trust these organizations.

---

# Browser Verification

When you visit:

```text
https://github.com
```

Your browser checks:

✔ Is the certificate valid?

✔ Has it expired?

✔ Was it issued by a trusted CA?

✔ Does it belong to github.com?

Only then does it continue.

---

# The TLS Handshake

Before HTTP begins,

HTTPS performs another handshake.

Simplified process:

```text
Browser

↓

Hello

↓

Server

↓

Certificate

↓

Verify Certificate

↓

Create Encryption Keys

↓

Secure Connection
```

Only after this

does HTTP begin.

---

# Complete HTTPS Journey

```text
You

↓

Browser

↓

DNS

↓

IP Address

↓

TCP Handshake

↓

TLS Handshake

↓

Encrypted HTTP Request

↓

Encrypted HTTP Response

↓

Browser
```

Notice

HTTPS adds

```text
TLS Handshake
```

between TCP and HTTP.

---

# The Lock Icon

Browsers display

🔒

This does **not** mean the website is trustworthy.

It only means the connection is encrypted.

A phishing website can also have HTTPS.

Always check the domain name.

---

# Real Example

When React calls:

```text
https://api.openai.com
```

Sequence:

```text
DNS

↓

TCP

↓

TLS

↓

HTTP
```

Every API request to OpenAI is encrypted.

---

# FastAPI Example

Development:

```text
http://localhost:8000
```

Usually HTTP.

Production:

```text
https://api.example.com
```

Almost always HTTPS.

---

# Why Localhost Often Uses HTTP

During development, everything stays on your own machine.

Traffic never leaves your computer.

Using HTTPS locally adds complexity, so many development servers use HTTP.

Production is different.

Always use HTTPS.

---

# Mixed Content

Suppose your website loads using HTTPS:

```text
https://example.com
```

But tries to load:

```text
http://image.com/logo.png
```

Most browsers block this.

Reason:

Mixing secure and insecure resources weakens security.

---

# Common Misconceptions

❌ HTTPS encrypts only passwords.

✔ HTTPS encrypts the entire HTTP request and response (except some metadata like IP addresses).

---

❌ HTTPS makes a website trustworthy.

✔ HTTPS only secures the communication.

It does not prove the website is legitimate.

---

❌ SSL and TLS are different technologies today.

✔ Modern HTTPS uses TLS, although "SSL" is still commonly used in conversation.

---

# Exercise

Open:

```text
https://github.com
```

Click the lock icon in your browser.

View:

- Certificate
- Issuer
- Expiration date

Now visit:

```text
http://neverssl.com
```

Notice there is no lock icon.

Observe the difference.

---
# Key Takeaways

- HTTP sends data as plain text.
- HTTPS encrypts HTTP traffic using TLS.
- TLS protects data from eavesdropping and tampering.
- Digital Certificates verify the server's identity.
- Browsers trust certificates issued by recognized Certificate Authorities.
- Modern websites should always use HTTPS in production.

---

# Summary

HTTPS is HTTP running over an encrypted TLS connection.

Before any HTTP request is exchanged, the browser and server establish a secure connection using the TLS handshake and verify the server's digital certificate.

This ensures that sensitive information such as passwords, authentication tokens, and personal data can travel securely across the Internet.

---

# The Complete Journey

You can now explain almost everything that happens after typing a URL:

```text
You
   │
   ▼
Browser
   │
   ▼
DNS Lookup
   │
   ▼
IP Address Found
   │
   ▼
TCP Three-Way Handshake
   │
   ▼
TLS Handshake
   │
   ▼
Encrypted HTTP Request
   │
   ▼
Server
   │
   ▼
Encrypted HTTP Response
   │
   ▼
Browser Renders the Page
```

This is one of the most important diagrams in networking.

---

# 8 – Browser Developer Tools & curl: Seeing Networking in Action

---

# 🎯 Objectives

- Use the Network tab in Browser Developer Tools.
- Inspect HTTP Requests.
- Inspect HTTP Responses.
- Read Request Headers.
- Read Response Headers.
- Observe Status Codes.
- Use `curl`.
- Compare browser requests with API requests.
- Debug FastAPI APIs using networking tools.

---

# Why This Lesson?

Until now we've learned the theory.

Today we'll actually watch the network.

Professional developers use the Network tab almost every day.

If an API fails...

↓

Network Tab

If authentication fails...

↓

Network Tab

If a website is slow...

↓

Network Tab

If CORS fails...

↓

Network Tab

Learning this tool is one of the highest ROI skills for a web developer.

---

# Opening Developer Tools

Chrome. Edge. Brave.

All support Developer Tools.

Shortcut:

Windows

```text
F12
```

or

```text
Ctrl + Shift + I
```

Mac

```text
Cmd + Option + I
```

---

# Network Tab

Open

```
Developer Tools

↓

Network
```

Initially you'll probably see nothing.

---

# Recording Requests

Open

```
https://github.com
```

Press

```
Ctrl + R
```

or refresh the page.

Suddenly you'll see dozens of requests.

Example

```text
document

style.css

app.js

logo.svg

font.woff

api request

images
```

A single webpage is actually many HTTP requests.

---

# The First Request

Click

```
document
```

This is usually

```text
GET /
```

This request downloads the HTML page.

Everything else depends on it.

---

# Inspecting the Request

Click

```
Headers
```

You'll see something like

```http
GET /

Host: github.com

User-Agent: Chrome

Accept: text/html
```

These are the Request Headers.

---

# Inspecting the Response

Now scroll lower.

You'll see

```text
Status Code

200 OK
```

Response Headers

```http
Content-Type: text/html

Cache-Control

Server

Date

Content-Length
```

Everything we've studied is now visible.

---

# Preview Tab

Click

```
Preview
```

Browser renders the response.

---

# Response Tab

Click

```
Response
```

You'll see the actual HTML returned by GitHub.

Exactly what the server sent.

---

# Timing Tab

Click

```
Timing
```

You'll see

```text
DNS

TCP

TLS

Waiting

Downloading
```

Amazing!

Everything we studied appears here.

---

# Size Column

Notice

```text
5 KB

200 KB

3 MB
```

These are downloaded resources.

Large files take longer.

---

# Waterfall

One of the most useful visualizations.

Example

```text
HTML

██████

CSS

     █████

JS

          ██████

Images

               ███████
```

You can immediately see which request is slow.

---

# Filter Requests

Network tab allows filtering.

Examples

```
Fetch/XHR
```

Shows API calls.

```
JS
```

Only JavaScript.

```
CSS
```

Only stylesheets.

```
Img
```

Only images.

Very useful.

---

# Watching a React App

Open

```
localhost:5173
```

Open Developer Tools.

Click buttons.

Watch API requests appear.

You'll later use this constantly.

---

# FastAPI Example

Suppose

React calls

```text
GET

/api/chat
```

Network shows

Request

↓

Headers

↓

Response

↓

JSON

↓

Status Code

Everything becomes visible.

---

# Introducing curl

Browsers aren't the only HTTP clients.

Terminal can also send HTTP requests.

The simplest tool is

```bash
curl
```

Think of it as

```
Chrome

without

the graphical interface.
```

---

# First Request

Run

```bash
curl https://example.com
```

Terminal prints HTML.

Exactly what the browser receives.

---

# Request Headers

Show headers only

```bash
curl -I https://github.com
```

Example

```http
HTTP/2 200

content-type:

text/html

server:

GitHub
```

---

# Verbose Mode

Run

```bash
curl -v https://github.com
```

Now you'll actually see

DNS

↓

TCP

↓

TLS

↓

HTTP

This is incredibly educational.

---

# GET Request

```bash
curl http://localhost:8000/users
```

Equivalent to

Browser

↓

GET /users

---

# POST Request

```bash
curl \
-X POST \
-H "Content-Type: application/json" \
-d '{"name":"Utpal"}' \
http://localhost:8000/users
```

Meaning

Method

↓

POST

Headers

↓

JSON

Body

↓

{"name":"Utpal"}

---

# Pretty JSON

If you have jq installed

```bash
curl http://localhost:8000/users | jq
```

Beautiful formatting.

---

# Testing FastAPI

Suppose FastAPI runs on

```
localhost:8000
```

Test

```bash
curl http://localhost:8000
```

Test another endpoint

```bash
curl http://localhost:8000/docs
```

No browser needed.

---

# Why Developers Love curl

Works

- SSH
- Docker
- CI/CD
- Servers
- Linux
- AWS

Many production servers don't even have browsers.

---

# Browser vs curl

Browser

✔ HTML

✔ CSS

✔ Images

✔ JavaScript

✔ Rendering

curl

✔ HTTP only

Perfect for APIs.

---

# Common Developer Workflow

Build FastAPI

↓

Run

```bash
uvicorn main:app --reload
```

↓

Test with

```bash
curl
```

↓

Open Browser

↓

Developer Tools

↓

Inspect Request

↓

Fix Bug

Repeat.

---

# Common Mistakes

❌ Looking only at the webpage.

✔ Look at the Network tab.

---

❌ Guessing API errors.

✔ Read the HTTP response.

---

❌ Ignoring Status Codes.

✔ Status Codes explain most problems.

---

# Exercise

Visit

```text
https://github.com
```

Open

Developer Tools

↓

Network

Refresh.

Observe

- Request Method
- Status Code
- Timing
- Headers
- Response

Now

Open Terminal

Run

```bash
curl -I https://github.com
```

Compare

Browser

↓

Headers

curl

↓

Headers

They are almost identical.

---



# Key Takeaways

- Browser Developer Tools reveal real network traffic.
- The Network tab shows every HTTP request and response.
- curl is a command-line HTTP client.
- Browser and curl both use HTTP.
- Professional developers constantly use these tools to debug applications.

---

# Summary

Understanding HTTP conceptually is important, but seeing HTTP requests in real time is what turns theory into practical skill.

Browser Developer Tools and curl allow developers to inspect requests, responses, headers, timing, status codes, and payloads, making them indispensable tools for debugging modern web applications.

---

# 9 – Authentication on the Web: Cookies, Sessions & JWT

---

# 🎯 Objectives

- Explain why HTTP is stateless.
- Understand why authentication is needed.
- Explain Cookies.
- Explain Sessions.
- Explain JWTs.
- Compare Session Authentication vs JWT Authentication.
- Understand how modern web applications stay logged in.

---

# Our Story So Far

We already know:

```text
Browser

↓

DNS

↓

TCP

↓

TLS

↓

HTTP Request

↓

HTTP Response
```

Now imagine you log in to GitHub.

---

# Problem

You enter:

```text
Username

↓

Password
```

GitHub verifies them.

Now what?

Suppose you click another page.

Browser sends another request.

```text
GET /repositories
```

How does GitHub know

this request came from you?

HTTP doesn't remember previous requests.

---

# HTTP is Stateless

Every request is independent.

Example

Request 1

```http
POST /login
```

Finished.

Request 2

```http
GET /profile
```

Starts fresh.

The server does NOT automatically remember

Request 1.

---

# Real-Life Analogy

Imagine going to a restaurant.

Every five minutes the waiter forgets who you are.

You must introduce yourself again.

That would be annoying.

HTTP behaves exactly like that.

---

# We Need Memory

The server needs a way to remember:

> This request belongs to Utpal.

There are two common approaches.

1. Sessions

2. JWT

Before both, we need Cookies.

---

# What is a Cookie?

A Cookie is a small piece of data stored by the browser.

Think of it as a small note.

Example

```text
sessionid=ABC123XYZ
```

The browser stores it automatically.

---

# First Login

Browser sends

```http
POST /login
```

Server verifies password.

Then replies

```http
Set-Cookie:

sessionid=ABC123XYZ
```

Notice

The browser stores it automatically.

---

# Next Request

Browser now sends

```http
GET /profile

Cookie:

sessionid=ABC123XYZ
```

GitHub reads

```
ABC123XYZ
```

and immediately knows

who you are.

---

# Visual

```text
Browser

↓

POST /login

↓

GitHub

↓

Set-Cookie

↓

Browser stores Cookie

↓

GET /profile

↓

Cookie automatically included

↓

GitHub recognizes user
```

---

# What is a Session?

The Cookie contains only an identifier.

Example

```text
ABC123XYZ
```

The actual user information lives on the server.

Example

```text
Session Table

ABC123XYZ

↓

Utpal

↓

Logged In

↓

Expires 8 PM
```

---

# Session Authentication

Browser

↓

Cookie

↓

Session ID

↓

Server

↓

Session Database

↓

User

The browser knows only the Session ID.

The server stores everything else.

---

# Advantages

✔ Very secure

✔ Easy to invalidate

✔ Widely used

---

# Disadvantages

Server must store every active session.

Large websites may have millions of sessions.

---

# JWT

JWT stands for

```text
JSON Web Token
```

Instead of storing data on the server,

JWT stores information inside the token itself.

Example

```text
eyJhbGciOi...
```

Looks random,

but actually contains

```json
{
  "user":"Utpal",
  "role":"admin"
}
```

plus a digital signature.

---

# Login Using JWT

Browser

↓

POST /login

↓

Server

↓

JWT Token

↓

Browser stores Token

Usually in:

- Local Storage
- Session Storage
- Cookie

---

# Next Request

Browser sends

```http
Authorization:

Bearer eyJhbGc...
```

Server verifies the signature.

No database lookup required.

---

# Session vs JWT

## Session

```text
Browser

↓

Session ID

↓

Server Database

↓

User
```

---

## JWT

```text
Browser

↓

JWT

↓

Server verifies signature

↓

User
```

No session database.

---

# Why JWT is Popular

Microservices

Mobile Apps

React

FastAPI

REST APIs

Cloud

All love JWT

because servers remain stateless.

---

# Which One Does GitHub Use?

GitHub primarily uses secure cookies with server-side sessions 
for its web interface.

Its APIs also support token-based authentication such as Personal Access Tokens (PATs).

Different parts of the same application can use different authentication methods.

---

# Which One Does ChatGPT Use?

Modern web applications often combine Cookies JWT Refresh Tokens Server-side sessions depending on the architecture.

There isn't one universal approach.

---

# FastAPI Example

Login

```http
POST /login
```

Response

```json
{
 "access_token":"eyJ..."
}
```

React stores it.

Next request

```http
Authorization:

Bearer eyJ...
```

Exactly what you'll build later.

---

# Cookie Example

Open Developer Tools.

Application

↓

Cookies

You'll see many cookies for websites you're logged into.

---

# Authorization Header

JWT usually travels in

```http
Authorization:

Bearer TOKEN
```

Notice

Cookies and JWT travel differently.

---

# Logout

Session

↓

Delete Session

Done.

JWT

↓

Cannot simply delete already issued tokens.

Instead use expiration times or token revocation mechanisms.

---

# Comparison

| Feature | Session | JWT |
|----------|----------|------|
| Data Stored | Server | Client Token |
| Server Database | Yes | Usually No |
| Easy Logout | Yes | More complex |
| Stateless | No | Yes |
| Good for Web Apps | Excellent | Good |
| Good for APIs | Good | Excellent |

---

# Common Misconceptions

❌ Cookies are always insecure.

✔ Secure cookies sent over HTTPS can be very safe.

---

❌ JWT is always better.

✔ It depends on the application.

---

❌ Sessions are outdated.

✔ Many large companies still use session-based authentication.

---

# Exercise

Open Chrome Developer Tools.

Visit

```text
https://github.com
```

If logged in:

Developer Tools

↓

Application

↓

Cookies

Observe:

- Cookie names
- Expiration
- Secure flag
- HttpOnly flag

Do not modify them.

Just observe.

---

# Key Takeaways

- HTTP does not remember previous requests.
- Cookies allow browsers to send small pieces of data automatically.
- Sessions store user state on the server.
- JWT stores signed user information inside the token.
- Modern web applications choose authentication strategies based on their architecture and security requirements.

---

# Summary

Authentication allows web applications to recognize users across multiple HTTP requests.

Cookies provide a mechanism for browsers to persist small pieces of data.

Sessions use cookies to reference server-side user state, while JWTs carry signed authentication information that can be verified without maintaining server-side session storage.

Understanding these concepts prepares you for implementing authentication in FastAPI, React, and cloud applications.

---

# Story So Far

```text
You
      │
      ▼
Browser
      │
      ▼
DNS
      │
      ▼
TCP
      │
      ▼
TLS
      │
      ▼
HTTP
      │
      ▼
Authentication
      │
      ▼
Application Logic
```

You now understand almost everything that happens between opening a browser and accessing a protected web application.

---
# 10 – CORS: Why Does the Browser Block My API?

---

# 🎯 Objectives

By the end of this lesson, you will be able to:

- Explain Same-Origin Policy.
- Understand what an Origin is.
- Explain CORS.
- Understand Preflight Requests.
- Explain the OPTIONS method.
- Configure CORS in FastAPI.
- Debug CORS errors like a professional developer.

---

# A Real Scenario

Suppose you're building ResearchMind AI.

React runs on

```text
http://localhost:5173
```

FastAPI runs on

```text
http://localhost:8000
```

React calls

```javascript
fetch("http://localhost:8000/chat")
```

Instead of getting data,

the browser says

```text
Blocked by CORS Policy
```

Why?

---

# Is FastAPI Broken?

No.

If you test the API using

```bash
curl http://localhost:8000/chat
```

It works.

The server is fine.

Only the browser blocks it.

---

# Why Does the Browser Care?

Imagine a malicious website.

```text
evil.com
```

You visit it while you're also logged into your bank.

The malicious site secretly runs:

```javascript
fetch("https://mybank.com/account")
```

If browsers allowed this,

evil.com could steal your bank information.

To prevent this,

browsers enforce the

```text
Same-Origin Policy.
```

---

# What is an Origin?

An origin has three parts:

```text
Protocol

Host

Port
```

Example:

```text
https://github.com:443
```

Protocol

↓

https

Host

↓

github.com

Port

↓

443

---

# Same Origin Examples

These two URLs:

```text
https://github.com
```

and

```text
https://github.com/settings
```

Same origin?

✔ Yes

Only the path changed.

---

# Different Protocol

```text
http://github.com
```

↓

```text
https://github.com
```

Different origin.

---

# Different Port

```text
localhost:5173
```

↓

```text
localhost:8000
```

Different origin.

---

# Different Host

```text
github.com
```

↓

```text
api.github.com
```

Different origin.

Even though both belong to GitHub.

---

# Visual

```text
Protocol

↓

Host

↓

Port
```

If any one changes,

it's a different origin.

---

# Same-Origin Policy

Browsers allow JavaScript to freely communicate only with

the same origin.

Everything else is blocked

unless permission is granted.

---

# What is CORS?

CORS stands for

```text
Cross-Origin Resource Sharing
```

Think of it as

the server saying:

> "I trust this other website."

Without CORS,

the browser blocks the request.

---

# Example

React

```text
localhost:5173
```

↓

FastAPI

```text
localhost:8000
```

Different origins.

FastAPI must explicitly allow React.

---

# How Does CORS Work?

Browser sends

```http
Origin:

http://localhost:5173
```

Server replies

```http
Access-Control-Allow-Origin:

http://localhost:5173
```

Browser sees

permission granted.

Request allowed.

---

# Without CORS Header

Browser

↓

Request

↓

Server

↓

Response

↓

Browser blocks response.

Notice

The server actually responded.

The browser simply refuses

to expose it to JavaScript.

---

# Preflight Request

Some requests are considered risky.

Before sending the real request,

the browser asks:

> "May I send this?"

This is called

```text
Preflight Request
```

---

# OPTIONS Request

Browser first sends

```http
OPTIONS /chat
```

Server replies

```http
Access-Control-Allow-Origin

Access-Control-Allow-Methods

Access-Control-Allow-Headers
```

If approved,

the browser sends

```http
POST /chat
```

---

# Visual

```text
Browser

↓

OPTIONS

↓

Server

↓

Permission Granted

↓

POST

↓

Server

↓

Response
```

---

# Which Requests Need Preflight?

Usually:

✔ PUT

✔ PATCH

✔ DELETE

✔ POST with custom headers

Simple GET requests often don't need one.

---

# FastAPI Configuration

FastAPI provides middleware.

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=[
        "http://localhost:5173"
    ],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

Now React can access FastAPI.

---

# What Does "*" Mean?

```python
allow_origins=["*"]
```

Means

Allow everyone.

Convenient for development.

Usually **not recommended** for production APIs.

In production, specify only trusted origins.

---

# Common Development Setup

```text
React

↓

localhost:5173
```

↓

HTTP

↓

```text
FastAPI

↓

localhost:8000
```

Without CORS middleware

↓

Blocked.

With middleware

↓

Works.

---

# Why curl Never Shows CORS Errors

Remember

CORS is

a browser security feature.

curl

↓

No browser

↓

No Same-Origin Policy

↓

No CORS enforcement.

This explains why

```bash
curl http://localhost:8000
```

works

even when your React app fails.

---

# Real Production Example

Frontend

```text
https://app.company.com
```

Backend

```text
https://api.company.com
```

Different origins.

Backend must allow

```text
https://app.company.com
```

using CORS.

---

# Common Misconceptions

❌ CORS is a server feature.

✔ CORS is enforced by browsers.

The server only sends permission headers.

---

❌ curl should show CORS errors.

✔ curl ignores CORS.

---

❌ Same host means same origin.

✔ Protocol, host, **and** port must all match.

---

# Hands-on Exercise

Create a simple FastAPI application.

Without CORS middleware,

call it from React.

Observe the browser error.

Now add

```python
CORSMiddleware
```

Refresh.

Observe the request succeed.

Finally,

open Developer Tools → Network.

Inspect:

```http
Origin

Access-Control-Allow-Origin
```

Notice the CORS headers.

---

# Key Takeaways

- An Origin consists of protocol, host, and port.
- Browsers enforce the Same-Origin Policy.
- CORS allows servers to grant permission for cross-origin requests.
- Preflight requests use the OPTIONS method.
- curl does not enforce CORS because it is not a browser.
- FastAPI uses CORSMiddleware to configure CORS.

---

# Summary

CORS is a browser security mechanism built on top of the Same-Origin Policy.

It prevents malicious websites from freely reading responses from other origins unless the target server explicitly grants permission through CORS headers.

Understanding CORS is essential for developing React, FastAPI, and other modern web applications because frontend and backend services often run on different origins during development and production.

---

# Complete Browser Journey

You can now explain the entire lifecycle of a web request:

```text
You
    │
    ▼
Type URL
    │
    ▼
DNS Lookup
    │
    ▼
IP Address
    │
    ▼
TCP Connection
    │
    ▼
TLS Handshake (HTTPS)
    │
    ▼
HTTP Request
    │
    ▼
Authentication
    │
    ▼
CORS Check (Browser)
    │
    ▼
Application Logic
    │
    ▼
HTTP Response
    │
    ▼
Browser Renders Page
```

---

# 11 – The Complete Journey: From Typing a URL to Rendering a React Application

---

# 🎯 Objectives

Explain, step by step:

- What happens after pressing Enter in a browser.
- How DNS, IP, TCP, TLS, HTTP, Cookies, JWT, and CORS work together.
- How React communicates with FastAPI.
- How the browser renders the page.
- Where common networking errors occur.

---

# The Scenario

Suppose you've built ResearchMind AI.

Frontend

```
https://app.researchmind.ai
```

Backend

```
https://api.researchmind.ai
```

You open your browser.

Type

```
https://app.researchmind.ai
```

and press Enter.

Let's follow everything.

---

# Step 1 — Browser Receives the URL

Browser extracts

```
Protocol

↓

https
```

```
Host

↓

app.researchmind.ai
```

```
Port

↓

443 (default)
```

---

# Step 2 — DNS Lookup

Browser asks

```
What is the IP address of

app.researchmind.ai ?
```

DNS replies

```
203.0.113.15
```

Now the browser knows

which computer to contact.

---

# Step 3 — TCP Connection

Browser opens

```
203.0.113.15:443
```

TCP performs

```
SYN

↓

SYN ACK

↓

ACK
```

Connection established.

---

# Step 4 — TLS Handshake

Browser says

```
Hello
```

Server replies

```
Certificate
```

Browser verifies

- Domain
- CA
- Expiration

Encryption keys are generated.

Secure connection established.

---

# Step 5 — HTTP Request

Browser sends

```http
GET /

Host: app.researchmind.ai
```

Server receives it.

---

# Step 6 — Web Server

The request first reaches

```
Nginx

or

Caddy

or

Apache
```

The web server decides

where to send it.

Suppose

```
/

↓

React Application
```

---

# Step 7 — Server Response

Server returns

```http
HTTP/1.1 200 OK

index.html
```

Browser downloads

```
index.html
```

---

# Step 8 — Browser Parses HTML

Browser finds

```html
<script src="main.js"></script>

<link href="style.css">
```

Browser immediately requests

```
main.js

style.css
```

These are new HTTP requests.

---

# Step 9 — JavaScript Starts

React loads.

Now React starts executing.

Initially

the page may show

```
Loading...
```

because

no API data exists yet.

---

# Step 10 — React Calls FastAPI

React executes

```javascript
fetch(
"https://api.researchmind.ai/chat"
)
```

Notice

This is

another HTTP request.

---

# Step 11 — Browser Checks CORS

Origin

```
https://app.researchmind.ai
```

Destination

```
https://api.researchmind.ai
```

Different hosts.

Browser checks

CORS.

---

# Step 12 — Authentication

Browser automatically sends

```
Cookie
```

or

```
Authorization:

Bearer JWT
```

depending on

how authentication works.

---

# Step 13 — Backend Receives Request

FastAPI receives

```
GET /chat
```

It verifies

- JWT

or

- Session

or

- Cookie

If authentication fails

↓

401 Unauthorized

Otherwise

↓

Continue.

---

# Step 14 — Business Logic

FastAPI executes

```python
answer = chatbot.ask(question)
```

Maybe it

- queries PostgreSQL
- calls Redis
- calls OpenAI
- performs RAG
- loads documents

Everything happens here.

---

# Step 15 — JSON Response

FastAPI returns

```json
{
    "answer":"Hello Utpal!"
}
```

HTTP Response

↓

200 OK

---

# Step 16 — React Receives JSON

React updates

its state.

```javascript
setAnswer(data.answer)
```

Component re-renders.

---

# Step 17 — Browser Updates Screen

Without reloading

the browser updates

only the changed component.

The user now sees

```
Hello Utpal!
```

---

# Complete Flow

```
You
 │
 ▼
Browser
 │
 ▼
DNS
 │
 ▼
IP Address
 │
 ▼
TCP
 │
 ▼
TLS
 │
 ▼
HTTP GET /
 │
 ▼
React HTML
 │
 ▼
Browser
 │
 ▼
React JavaScript
 │
 ▼
HTTP API Request
 │
 ▼
CORS
 │
 ▼
Authentication
 │
 ▼
FastAPI
 │
 ▼
Business Logic
 │
 ▼
Database / OpenAI
 │
 ▼
JSON Response
 │
 ▼
React State Update
 │
 ▼
Browser Re-renders UI
```

---

# Where Things Can Fail

## DNS

```
DNS_PROBE_FINISHED_NXDOMAIN
```

---

## TCP

```
Connection refused
```

---

## TLS

```
Certificate invalid
```

---

## HTTP

```
404

500
```

---

## Authentication

```
401 Unauthorized
```

---

## Authorization

```
403 Forbidden
```

---

## CORS

```
Blocked by CORS Policy
```

---

## React

```
Cannot read property...
```

---

# Debugging Strategy

Professional developers debug in layers.

```
DNS

↓

TCP

↓

TLS

↓

HTTP

↓

Authentication

↓

Application Logic

↓

React
```

Never jump randomly.

Start at the lowest failing layer.

---

# Real ResearchMind Architecture

```
Browser
     │
     ▼
React
     │
     ▼
HTTPS
     │
     ▼
Nginx
     │
     ▼
FastAPI
     │
     ▼
Redis
     │
     ▼
PostgreSQL
     │
     ▼
OpenAI API
```

This is very close to what you'll build later.

---

# Exercise

1.

Open

```
https://github.com
```

2.

Open Developer Tools

↓

Network

3.

Refresh.

Identify

- DNS
- TCP
- TLS
- Request Headers
- Response Headers
- Status Code

4.

Open your FastAPI project.

Call an endpoint.

Observe

- Request
- Response
- JSON
- Timing

---

# Key Takeaways

- Modern web applications are built on many networking layers working together.
- Every request follows a predictable sequence:
  DNS → TCP → TLS → HTTP → Authentication → Application Logic → Response.
- React and FastAPI communicate using standard HTTP requests.
- Most networking errors occur at one specific layer and can be debugged systematically.

---

# Summary

Networking is not a collection of unrelated topics. It is a pipeline.

By understanding how DNS, IP addressing, TCP, TLS, HTTP, authentication, and browser rendering interact, you gain a mental model that applies to every modern web application.

This understanding will make learning Docker, Kubernetes, cloud platforms, reverse proxies, and production deployments significantly easier.

---






















