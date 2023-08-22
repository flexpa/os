# 👥 Pairing

Pairing is a common software development practice where two developers work together on the same problem synchronously.

At Flexpa, sometimes we write code solo and sometimes in pairs.
We commit ourselves to the following guidelines when pairing.

## Why

The purpose of pairing, ultimately, is to go farther, faster, together.
There are some secondary reasons though:

1. **Context sharing / anti-siloing**. By working through a problem together we can guarantee that two people understand it versus just one.
2. **Distraction reduction**. Pairing forces your attention to be immediately accountable to another person. Checking your phone? Bad form.
3. **Team building / skill development.** Pairing promotes the exchange of ideas and skills. One developer may be more experienced or have a different area of expertise than the other, and pairing allows for continuous, hands-on learning. 

## What

If pairing means working together, what does the work look like?

We have found three axes helpful in answering this question:

* Driver vs. Navigator
* Scheduled vs. ad hoc
* Unblocking a problem vs. exploring a problem space

It is typical of pair programming to have two roles: a **driver** (the person with control of the editor) and a **navigator** (the person keeping track of where we are, giving immediate feedback and information to the driver). 

It is good practice to be explicit about declaring which role each person is taking at the start of a pair.
It is similarly good practice to switch roles during the pair. 

Conversely, it is extremely poor practice to be disengaged during a pair regardless of role.
This is a trap that is easy to fall into as a navigator and must be consciously avoided.

**Scheduled** pairs are straightforward: you agree to a time in advance.
**Ad hoc** pairs happen immediately.
You must actively communicate personal preferences and performance factors when being asked to pair. 
Do not accept invites or requests to pair if you _know_ you are not going to be an active, great communicator.
Consider asking “is now still a good time to pair?” when you begin.

Finally, deciding whether you are **unblocking a problem** vs. **exploring a problem space** can have big impact on the work of a pair.
Unblocking requires extreme clarity about what exactly the problem is.
If you bring a problem to your pair you should strongly consider providing details in advance.
Lack of preparation and clarity of thought signals disengagement from the very start.
If you post about being blocked by a problem in your standup, consider asking for a pair.

Exploring a problem space, to the contrary, sometimes means learning what exactly the problem is during the pair.
This type of pairing can be especially useful during the earliest phases of feature development. 

Along all three axes, personal preferences and performance factors should be communicated.
If you prefer unblocking problems as a navigator in ad hoc pairs, you should make sure to say it. 

## How

Pairing requires active engagement by both people.
There is no passive role.

Typically, at least when in person, pairing means sharing one computer to do the work together.
Working on separate machines is considered bad etiquette at best and at worst missing the point entirely. 

For remote, obviously two computers are necessary.
There is a strong temptation to default to sharing your screen because this action has become ubiquitous in remote work. However, the screen sharing built into popular meeting tools like Zoom encourages passive engagement and easily turns a driver / navigator pair into a driver / passenger. 

You should strongly prefer tools that enable **multiplayer mode**; tools that allow multiple developers to share and work on the same codebase in real-time.
VS Code Live Share is one such tool and is used as a default at Flexpa.
A pair can agree to whichever tools they prefer but every individual contributor needs to maintain a VS Code Live Share install.
Screen sharing can work well with _good_ meeting tools (such as [Multi](https://multi.app/) and [CoScreen](https://www.coscreen.co/)) that enable multi-cursor control, easy screen drawing, and sharing individual windows.

Tooling alone cannot overcome the problem of passive participation, but defaults encourage and nudge us in the right direction.

### Etiquette

* **Be clear and communicate your preferences for pairing.** Use the 3 axes as a communication tool.
* **Start the session by writing down a clear goal.** This is especially important when a pair is working on a problem where only one party has knowledge of the problem at the start.
* **Use a multiplayer setup and avoid problematic screen sharing.** Screen sharing in popular meeting tools encourages passive mode. 
* **If you need to shift your focus from the pair, announce it explicitly**. Obviously, there are times when a pair will need to temporarily pause or one person will need to take care of some urgent matter. That’s okay, but you should always announce that your attention has shifted. Be explicit.
* **Turn on focus mode in MacOS to prevent notifications.** You can allow priority notifications from applications like Slack, but you should disable everything that isn’t urgent.
* **Put your pair in a calendar invite (even if it’s ad hoc) and update your Slack status**. If you use the Google Calendar extension, you can configure it to automatically update your status based on meeting presence. This helps to announce to other people that you won’t see their notifications immediately.
* **Assume that people currently pairing have 100% of their attention dedicated to the pair.** If you notice a Slack status or a calendar event for pairing, assume that you will not receive a reply until the pair is finished.
* **Don’t pair for more than 90 minutes continuously.** Pairing is a cognitively expensive process. Doing it well requires concentration and attention that many people may not have. Take breaks frequently, and be comfortable with going on and off camera and mute to excuse yourself as you would normally. Breaks for a short stretch or walk will make you more effective. Pairing is **not** just a long meeting but a continuous flow.

## See also

* [Tuple’s Pair Programming Guide](https://tuple.app/pair-programming-guide/)
* [On Pair Programming](https://martinfowler.com/articles/on-pair-programming.html)