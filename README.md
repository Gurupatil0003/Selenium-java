# Hosting a Simple Web Page in Ubuntu VM (NAT Network Demo)

## Step 1: Start Ubuntu

Open Terminal and install Python (if not already installed):

```bash
sudo apt update
sudo apt install python3
```

## Step 2: Create a Web Page

- Create a file:
```python
nano index.html
```
- Write the following content:
```python
<h1>Hello from Ubuntu VM!</h1>
<h2>NAT Network Demo</h2>
```

#### Step 3: Start a Web Server
```python
Run:

python3 -m http.server 8000
```
```python
You'll see:

Serving HTTP on 0.0.0.0 port 8000 ...

This means Ubuntu is hosting a website.

```
### Step 4: Open Firefox Inside Ubuntu
```python
Go to:

http://localhost:8000

You'll see:

Hello from Ubuntu VM!
NAT Network Demo

Success! 🎉

What's Happening?
Windows 11
     |
VirtualBox
     |
Ubuntu VM
     |
Web Server (Port 8000)

The website is running inside Ubuntu.
```
#### Step 5: Try Accessing It from Windows

```python
First, find Ubuntu's IP address:

ip a

You'll see something like:

10.0.2.15

Now on Windows, open Chrome and try:

http://10.0.2.15:8000
Most Likely Result
❌ It won't open.
```
