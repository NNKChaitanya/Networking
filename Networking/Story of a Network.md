
# Before Network :

Imagine the Year is 1980.

You buy a computer.

It has:

CPU
RAM
Keyboard
Monitor

Everything works.

But...

It is completely alone.

It cannot:

❌ Send files

❌ Print to another printer

❌ Send email

❌ Access Internet

Why?

Because it isn't connected to anything.

Now imagine another computer.

Computer A

Computer B

Can they communicate?

No.

They don't know each other exists.

Now connect them.

Computer A
     │
 Ethernet Cable
     │
Computer B

Now they can exchange information.

This connection is called:

A Network

# Definition

A network is:

Two or more devices connected together to exchange information.

Notice something.

It never says:

Switch
Router
Firewall
Cisco

Because networking is much bigger than it.

Cisco only builds devices that implement networking.

What Is Information?

Suppose you send:

Hello

to another computer.

Your computer doesn't send the word "Hello."

It converts it into:

01001000
01100101
01101100
01101100
01101111

Everything in networking eventually becomes:

Bits

0

1

Networking is simply moving billions of 0s and 1s from one device to another.

The Biggest Question

Imagine your laptop wants to open:

www.microsoft.com

How does Microsoft know where to send the reply?

Think about that.

There are millions of computers on Earth.

How does Microsoft know:

"This response belongs to Chaitanya."

This single question gave birth to:

1. IP Address
2. MAC Address
3. Routing
4. DNS

Everything starts from this question.

Communication Requires Three Things

Imagine you're sending a courier.

The courier company needs three things.

1. Sender Address

Who sent this?

In networking:

Source IP

Example

192.168.1.10

2. Destination Address

Where should it go?

Example

142.250.183.78

(Google)

3. Path

How should it reach there?

This is routing.

Without these three things:

Communication is impossible.

What Devices Help Communication?

Let's say you have:

10 Computers

Should every computer connect directly to every other computer?

Imagine just 5 computers:

A ----- B
|\     /|
| \   / |
|  \ /  |
|  / \  |
| /   \ |
|/     \|
C ----- D
 \     /
   \ /
    E

The number of cables grows very quickly.

With 100 computers, you'd need thousands of cables.

Clearly impossible.

Solution?

Someone invented the Switch.

Now it becomes:

      Switch
   /  |  |  \
 A   B  C   D
        |
        E

One central device.

Simple.

Cheap.

Easy.

Then another problem appeared.

What if another office has its own switch?

Office A

Switch

↓

Office B

Switch

Now the switches need to communicate.

This led to routers and routing.

Everything Evolves Like This

Problem

↓

Solution

↓

New Problem

↓

New Solution

Networking is just a chain of engineering solutions.
