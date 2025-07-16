# 100 Days of Cybersecurity: Day 5
*Process Monitoring with `ps` and `top` - A Student's Journey*

## Hey Fellow Cybersecurity Student! 👋

So, I'm on Day 5 of my 100 Days of Cybersecurity challenge, and today we're diving into process monitoring! I was super confused about this at first, but after playing around with it, I think I've got some cool stuff to share with you.

### What I Learned About Process Monitoring 💡

Remember when we first started learning about computers, and everything seemed like magic? Well, process monitoring is like getting a backstage pass to see how everything really works! Here's what I discovered:

1. **It's Like Being a Detective**: You can see exactly what's running on your system
2. **Super Useful for Security**: You can spot when something's not supposed to be there
3. **Great for Troubleshooting**: When your computer acts weird, this helps figure out why
4. **Really Cool for Learning**: You get to see how everything connects

## The Tools I'm Learning to Use 🛠️

### The `ps` Command - My New Best Friend 📸

I used to think `ps` was just for showing processes (duh, right?), but it's actually super powerful! Here's what I use most:

```bash
# This is my go-to command now - shows everything!
ps aux

# When I need to find something specific
ps -ef | grep what_im_looking_for

# This one's cool - shows how processes are related
ps -ejH
```

The output looks like this:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root       123  0.0  0.1  12345  6789 ?        Ss   10:00   0:00 /usr/sbin/sshd
```

I'm still learning what all these columns mean, but here's what I've figured out so far:
- **USER**: Who's running it (I always check this first)
- **PID**: The process ID (super useful when you need to stop something)
- **%CPU**: How much CPU it's using (red flag if it's high!)
- **%MEM**: Memory usage (another thing to watch)
- **STAT**: Process state (still learning all the states, but 'Z' means zombie!)

### The `top` Command - My Live Dashboard 📊

`top` is like having a live feed of your system - it's pretty cool! Here's how I use it:

```bash
# Basic view - I use this most
top

# When I'm writing scripts (just learned this!)
top -b -n 1

# When I'm tracking a specific user
top -u username
```

Pro tip I learned: Watch the load average in `top`. If it's higher than your CPU cores, something's up!

## Real Stuff I've Tried 🚀

### 1. The CPU Mystery
Last week, my system was super slow. Here's what I did:

```bash
# First, I checked what was using CPU
ps aux --sort=-%cpu | head -10

# Then I looked for weird stuff
ps aux | grep -i "/tmp\|/var/tmp"

# Finally, I watched it live
watch -n 1 'ps aux --sort=-%cpu | head -5'
```

Turns out I had a backup running in the background - mystery solved! 

### 2. The Memory Adventure
My computer was running out of memory (not fun!). Here's what I tried:

```bash
# Checked memory usage
free -h

# Looked for memory-hungry processes
ps aux --sort=-%mem | head -10

# Monitored memory in real-time
top -b -n 1 | grep "Mem"
```

Found out my browser was eating all the memory - time to close some tabs! 

## My Daily Practice Routine 📋

Here's what I'm trying to do every day:

1. **Morning Check**
   - Quick `ps aux` scan
   - Check system load with `top`
   - Look for anything weird

2. **During the Day**
   - Watch high-traffic times
   - Keep an eye on important stuff
   - Take notes of anything unusual

3. **End of Day**
   - Review what I found
   - Check if anything's still weird
   - Update my notes

## Mistakes I've Made (So You Don't Have To!) 🔧

### 1. The CPU Confusion
I spent hours chasing a CPU issue, only to find it was a scheduled task. Now I:
- Check `crontab` first
- Look at when processes started
- Think about scheduled stuff

### 2. The Memory Mix-up
I learned that high memory usage isn't always bad. Now I:
- Check if it's cached memory
- Look at swap usage
- Think about what the app needs

### 3. The Zombie Process Panic
I had a server full of zombie processes once - scary! Now I:
- Clean up processes regularly
- Watch parent processes
- Keep track of process families

## My Study Plan 📝

1. **Start Small**
   - Practice `ps` and `top` on my laptop
   - Get comfortable with the output
   - Try different options

2. **Build My Toolkit**
   - Write scripts to monitor stuff
   - Document what's normal on my system
   - Make a cheat sheet

3. **Think Like a Detective**
   - Look for patterns
   - Question weird stuff
   - Write everything down

## Why I'm Loving These Tools 🤔

### Why Both `ps` and `top`?
I use them like different camera angles:
- `ps` for detailed pictures
- `top` for live action
- Together, they show the whole story

### Why Process Monitoring?
It's like having superpowers:
- Catches security issues early
- Stops performance problems
- Helps fix stuff
- Makes you look smart to your friends!

## My Go-To Resource 📚

### The One Documentation I Actually Use
- [Linux Process Management Guide](https://www.kernel.org/doc/html/latest/admin-guide/process-management.html) - It's got everything I need!

### The One Learning Platform That Helped
- [TryHackMe - Linux Fundamentals](https://tryhackme.com/room/linuxfundamentals) - Where I started learning this stuff

### The One News Source I Check
- [The Hacker News](https://thehackernews.com/) - For staying updated

## Final Thoughts 💭

Process monitoring seemed super complicated at first, but it's actually pretty fun once you get the hang of it! I'm still learning new things every day, and that's what makes this journey exciting.

*Pro Tip: I'm keeping a personal wiki of everything I learn. You should try it too!* 📝

---
*Day 6 is about network monitoring - can't wait to share what I learn!* 🔐

let's connect and share our learning journey! 🚀
