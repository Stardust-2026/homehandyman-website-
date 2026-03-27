# HomeHandyman WhatsApp Bot Flow

## Overview
The HomeHandyman WhatsApp bot provides a conversational booking experience for customers who prefer messaging over web forms. The bot guides users through a simple, step-by-step process to book a handyman.

---

## Bot Configuration

### Bot Name
HomeHandyman Assistant

### Bot Number
+65 XXXX XXXX (to be configured)

### Welcome Message (Auto-reply)
```
👋 Welcome to HomeHandyman!

Quality handymen, on demand. 

Reply with what you need help with, or type:
• BOOK - Start a new booking
• STATUS - Check existing booking
• HELP - Get assistance
```

---

## Conversation Flow

### Entry Point: Customer Initiates

**Customer:** "Hi, I need plumbing help"

**Bot:** 
```
Hi! I'm here to help. What's the issue?

1. Leak
2. Clog/Blockage  
3. Installation
4. Repair
5. Other

Reply with the number (1-5).
```

---

### Step 1: Issue Type Selection

**Customer:** "1" (or "Leak")

**Bot:**
```
Got it - Leak. 

When do you need this?

1. Today (urgent)
2. Tomorrow
3. This week
4. Next week
5. Specific date

Reply with the number (1-5).
```

---

### Step 2: Timing Selection

**Customer:** "2" (or "Tomorrow")

**Bot:**
```
Perfect! Tomorrow works.

What's your address? Please include:
• Block/Street
• Unit number
• Postal code

Example: Block 123 Tampines St 11, #05-123, S520123
```

---

### Step 3: Address Collection

**Customer:** "Block 456 Ang Mo Kio Ave 10, #12-345, S560456"

**Bot:**
```
Thanks! Address saved:
📍 Block 456 Ang Mo Kio Ave 10, #12-345, S560456

Would you like to send a photo of the problem? 
(This helps us match you with the right handyman)

1. Send photo
2. Skip

Reply with 1 or 2.
```

---

### Step 4: Photo Upload (Optional)

**Customer:** "1" → [uploads photo]

**Bot:**
```
✓ Photo received! 

What's your contact number? 
(We'll use this to confirm your booking)

Example: +65 9123 4567
```

**Alternative - Customer skips:**

**Customer:** "2"

**Bot:**
```
No problem! 

What's your contact number? 
(We'll use this to confirm your booking)

Example: +65 9123 4567
```

---

### Step 5: Contact Collection

**Customer:** "+65 9123 4567"

**Bot:**
```
Perfect! Here's your booking summary:

📋 BOOKING SUMMARY
━━━━━━━━━━━━━━━━━━━━
🔧 Service: Plumbing - Leak
📅 When: Tomorrow
📍 Address: Block 456 Ang Mo Kio Ave 10, #12-345, S560456
📷 Photo: Attached
📱 Contact: +65 9123 4567

Reply CONFIRM to submit, or CANCEL to start over.
```

---

### Step 6: Confirmation

**Customer:** "CONFIRM"

**Bot:**
```
✅ BOOKING CONFIRMED!

Your request has been submitted. 

⏱️ We'll match you with a vetted handyman and confirm within 30 minutes.

You'll receive:
• Handyman's name & photo
• Contact number
• Estimated arrival time
• Price estimate

Booking ID: #HH12345

Questions? Reply HELP anytime.
```

---

## Alternative Flows

### Direct Service Booking

**Customer:** "I need an electrician"

**Bot:**
```
Sure! I can help with electrical work.

What do you need?

1. Wiring/Power issues
2. Light fixture installation
3. Fan installation/repair
4. Switch/socket repair
5. Other

Reply with the number (1-5).
```

---

### Status Check

**Customer:** "STATUS" or "Check my booking"

**Bot:**
```
Please provide your booking ID or the phone number used for the booking.
```

**Customer:** "#HH12345"

**Bot:**
```
📋 BOOKING STATUS: #HH12345
━━━━━━━━━━━━━━━━━━━━
Status: ✅ MATCHED

👤 Your Handyman:
Name: Ahmad
Rating: ⭐ 4.9 (127 reviews)
Phone: +65 8234 5678

⏰ Arrival: Today, 2:00 PM - 3:00 PM
💰 Estimated: $80 - $120

Need to make changes? Reply CANCEL or RESCHEDULE.
```

---

### Help Flow

**Customer:** "HELP"

**Bot:**
```
🆘 HOMEHANDYMAN HELP
━━━━━━━━━━━━━━━━━━━━

📞 Call us: +65 XXXX XXXX
💬 WhatsApp: This number
📧 Email: hello@homehandyman.sg

Quick options:
• Type BOOK - New booking
• Type STATUS - Check booking
• Type PRICE - Pricing info
• Type SERVICES - What we offer

Or describe your issue and we'll help!
```

---

## Quick Reply Keywords

| Keyword | Action |
|---------|--------|
| BOOK / START / NEW | Start new booking |
| STATUS / CHECK | Check existing booking |
| CANCEL | Cancel current booking/flow |
| HELP / SUPPORT | Show help menu |
| PRICE / COST | Show pricing info |
| SERVICES | List available services |
| EMERGENCY / URGENT | Fast-track booking |

---

## Service Categories

When user mentions a service, map to:

| User Says | Category |
|-----------|----------|
| plumber, plumbing, leak, pipe, water, toilet, sink, bathroom | Plumbing |
| electrician, electrical, wiring, power, light, fan, socket, switch | Electrical |
| carpenter, carpentry, wood, cabinet, door, furniture | Carpentry |
| painter, painting, paint, wall, color | Painting |
| handyman, repair, fix, general | General Repairs |
| aircon, ac, air conditioning, cooling | Aircon |
| tile, cement, concrete, floor | Masonry |
| clean, cleaning, wash | Cleaning |

---

## Error Handling

### Unrecognized Input

**Bot:**
```
Sorry, I didn't understand that. 

Type:
• BOOK - to start a new booking
• STATUS - to check your booking
• HELP - for assistance

Or tell me what service you need (plumbing, electrical, etc.)
```

### Timeout (24h no response)

**Bot:**
```
👋 Still there? Your booking session has expired.

Reply BOOK to start fresh, or let us know if you need help!
```

---

## Backend Integration Notes

1. **Session Management**: Store user state (step, data collected) per phone number
2. **Media Handling**: Save photos to cloud storage, link to booking
3. **Matching Logic**: Trigger handyman matching on CONFIRM
4. **Notifications**: Send SMS/WhatsApp to matched handyman
5. **Analytics**: Track conversion rates, popular services, response times

---

## Future Enhancements

- [ ] Multi-language support (English, Mandarin, Malay, Tamil)
- [ ] Voice message support
- [ ] Live chat handoff for complex issues
- [ ] Automated follow-up after job completion
- [ ] Rating/review collection via WhatsApp
- [ ] Promotional broadcasts (with opt-in)
