---

# 🔗 Webhook Pattern — 200 IQ Explanation

## 💡 What Most People Think

```text
Webhook = API Callback
```

That's true.

But that's only the beginner explanation.

---

## 🧠 The Real Definition

> A Webhook is a mechanism where one system automatically sends an HTTP request to another system when a specific event occurs.

The keyword is:

```text
Push
```

Not polling.

Push.

---

## 🍽️ Restaurant Analogy

Imagine you're waiting for your food delivery.

### Option 1: Polling

Every minute:

```text
You
 ↓
"Is my order ready?"
```

Again.

```text
You
 ↓
"Is my order ready?"
```

Again.

```text
You
 ↓
"Is my order ready?"
```

Annoying for everyone.

---

### Option 2: Webhook

You tell the restaurant:

```text
Call me when food is ready.
```

Restaurant:

```text
Food Ready
     ↓
Call Customer
```

No unnecessary checking.

This is exactly how Webhooks work.

---

## 🚨 The Real Problem

Suppose your application integrates with:

- Stripe
- Razorpay
- GitHub
- Slack
- Zoom

Your system needs to know:

```text
Payment Completed

Repository Updated

Meeting Started

Message Received
```

How do you know when these events happen?

---

## ❌ Without Webhooks (Polling)

Your server repeatedly asks:

```http
GET /payment-status
```

Every:

```text
10 Seconds
```

Even when nothing changes.

---

Architecture:

```text
Your App
    ↓
Stripe API

Your App
    ↓
Stripe API

Your App
    ↓
Stripe API
```

Thousands of unnecessary requests.

---

## ✅ With Webhooks

You register:

```text
https://yourapp.com/webhook
```

Then Stripe automatically sends:

```http
POST /webhook
```

when:

```text
Payment Successful
```

No polling required.

---

## 🎯 The Real Goal Isn't Communication

Most people think:

```text
Webhook = Integration
```

Actually:

```text
Webhook = Event Notification
```

The goal is:

```text
Don't ask.

Be informed.
```

---

## 🔥 Problems Solved By Webhooks

### 1️⃣ Eliminates Polling

Without Webhooks:

```text
Every 10 Seconds
```

Check for updates.

---

With Webhooks:

```text
Only When Event Happens
```

Massive efficiency improvement.

---

### 2️⃣ Real-Time Updates

Without Webhooks:

```text
Payment Completed
      ↓
User Waits 10 Seconds
```

---

With Webhooks:

```text
Payment Completed
      ↓
Immediate Notification
```

---

### 3️⃣ Lower API Costs

Polling:

```text
100,000 Requests
```

Most return:

```text
No Updates
```

Wasteful.

---

Webhooks:

```text
Only Send When Needed
```

---

### 4️⃣ Better Scalability

Instead of:

```text
10,000 Clients
      ↓
Repeated Polling
```

Use:

```text
Event Occurs
      ↓
Webhook Sent
```

Far fewer requests.

---

## 🏗️ How Webhooks Work

### Step 1

Register a callback URL.

```text
https://classcrafters.com/webhook
```

---

### Step 2

External service stores it.

```text
Stripe
GitHub
Razorpay
Slack
```

---

### Step 3

Event occurs.

```text
Payment Completed
```

---

### Step 4

Webhook fires.

```http
POST /webhook
```

Payload:

```json
{
  "event": "payment.completed",
  "paymentId": "123"
}
```

---

### Step 5

Your application processes it.

```text
Update Order

Send Receipt

Unlock Course
```

---

## 🚀 ClassCrafters Example

Student buys a course.

Payment handled by:

```text
Razorpay
```

---

Without Webhook:

```text
ClassCrafters
      ↓
Check Payment Status
      ↓
Check Again
      ↓
Check Again
```

Inefficient.

---

With Webhook:

```text
Payment Success
       ↓
Razorpay
       ↓
Webhook
       ↓
ClassCrafters
```

Course unlocks immediately.

---

## 🌎 Real-World Examples

### GitHub

```text
Push Code
     ↓
Webhook
     ↓
CI/CD Pipeline
```

Automatically deploys application.

---

### Stripe

```text
Payment Completed
      ↓
Webhook
      ↓
Order Confirmed
```

---

### Slack

```text
New Message
      ↓
Webhook
      ↓
External Application
```

---

### Zoom

```text
Meeting Started
      ↓
Webhook
      ↓
Attendance System
```

---

## 🔗 Webhook vs API

### API

```text
Client
 ↓
Server
```

Client initiates communication.

---

### Webhook

```text
Server
 ↓
Client Endpoint
```

Server initiates communication.

---

### Easy Memory Trick

```text
API = Ask

Webhook = Notify
```

---

## ⚠️ Challenges

### Duplicate Deliveries

Sometimes:

```text
Webhook Sent Twice
```

Applications must handle duplicates.

---

### Security

Anyone could call:

```http
POST /webhook
```

Need:

```text
Signature Verification
```

---

### Temporary Failures

Your server might be down.

Webhook provider retries.

Applications should be:

```text
Idempotent
```

---

## 🧠 The 200 IQ Insight

People think:

```text
Webhooks move data.
```

The deeper truth:

```text
Webhooks move responsibility.
```

Instead of constantly asking:

```text
Did something happen?
```

You let the event source tell you.

This dramatically reduces:

- Network Traffic
- API Calls
- Infrastructure Cost

---

## 🎤 Interview Answer

> A Webhook is an event-driven integration pattern where one system automatically sends an HTTP request to another system when a specific event occurs. It enables real-time notifications, reduces polling, and improves scalability by pushing updates only when necessary.

---

# 🧠 Memory Trick

```text
Message Queue = Buffers Work

Publish-Subscribe = Broadcasts Events

Event-Driven Architecture = Entire System Runs On Events

Webhook = Pushes Events Across Systems
```

---

## 🎯 One Sentence You'll Never Forget

```text
APIs ask.

Webhooks notify.
```

---

## 🔥 Ultimate Difference

```text
API
 ↓
"Did something happen?"

Webhook
 ↓
"Something happened."
```