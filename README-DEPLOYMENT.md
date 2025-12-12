# Outbound Call Trainer - Deployment Guide

## ✅ What's Different from Inbound

Your **working inbound trainer** uses:
- ✅ localStorage (browser storage) - NO external database
- ✅ Password authentication
- ✅ Call history with CSV export
- ✅ Role-based access (admin/doctor/va)
- ✅ OpenAI Realtime API for voice

The **outbound trainer** I created uses the EXACT SAME approach. No Supabase needed!

---

## 🚀 Deployment Steps (Same as Your Inbound)

### Step 1: Modify the HTML File (Optional)

**Add Your Office Passwords** (Lines 167-245):

```javascript
// Add your Brighton Spine & Wellness team
"VFDA-BRIGHTON-DOC-2025": { 
    name: "Dr. Matthew", 
    office: "brightonspine",
    role: "doctor" 
},
"VFDA-BRIGHTON-VA1-2025": { 
    name: "Melle", 
    office: "brightonspine",
    role: "va" 
},
"VFDA-BRIGHTON-VA2-2025": { 
    name: "Your VA 2", 
    office: "brightonspine",
    role: "va" 
},
```

**That's it!** No Supabase configuration needed.

---

### Step 2: Deploy to Vercel

#### Option A: GitHub + Vercel (Recommended - Same as Inbound)

1. **Push to GitHub:**
   ```bash
   git add outbound-trainer.html
   git commit -m "Add outbound trainer"
   git push origin main
   ```

2. **Vercel Auto-Deploys** (if already connected)
   - Vercel sees the new file
   - Deploys automatically
   - Your URL: `https://your-project.vercel.app/outbound-trainer.html`

#### Option B: Vercel Direct Upload

1. Go to https://vercel.com
2. Drag and drop `outbound-trainer.html`  
3. Instant deployment

---

### Step 3: Test It

1. Go to: `https://your-project.vercel.app/outbound-trainer.html`
2. Enter password: `VFDA-ADMIN-2025` (or your password)
3. Enter OpenAI API key when prompted
4. Fill in:
   - Office: Brighton Spine & Wellness
   - Doctor: Jarvis (or your name)
   - Select: Easy difficulty
5. Click "Start Outbound Call"
6. Start speaking to the AI patient

---

## 📊 How Call History Works

### Data Storage

**Saved in Browser's localStorage:**
```javascript
localStorage.setItem('outbound_call_logs', JSON.stringify(callLogs));
```

**Each call saves:**
- VA name
- Office name
- Doctor name
- Difficulty level
- Score (0-100)
- Patient booked? (true/false)
- Call duration
- Timestamp
- All checkpoint scores

### Who Sees What

| Role | What They See |
|------|---------------|
| **Admin** | All calls from all offices |
| **Doctor** | Only calls from their office |
| **VA** | Only their own calls |

### Exporting Data

Click "📥 Export CSV" button to download:
- All call logs
- Formatted spreadsheet
- Opens in Excel/Google Sheets

---

## 🎯 Outbound Trainer Features

### 2 Difficulty Levels:

**Easy - Jennifer Rodriguez**
- Cooperative marketing manager
- Expecting the call
- Has basic questions
- Books if handled professionally
- Perfect for new VAs

**Challenging - Michael Chen**
- Construction supervisor
- Forgot about form submission
- Multiple objections:
  * "What form? I forgot..."
  * "How much exactly?"
  * "Had bad experience before"
  * "Hard to take time off"
  * "No insurance coverage"
- Only books if objections handled well
- Great for advanced training

### 7 Scoring Checkpoints:

1. ✅ Professional Introduction (10pts)
2. ✅ Health History Inquiry (10pts)
3. ✅ Purpose Stated Clearly (10pts)
4. ✅ Specific Appointment Options (10pts)
5. ✅ Objection Handling (10pts)
6. ✅ Payment Collection Explained (10pts)
7. ✅ Closing & Confirmation (10pts)

**Bonus:** +30pts for Communication, Professionalism, Problem Solving

**Passing Score:** 70/100

---

## 🔧 Technical Specs

### Same as Your Inbound Trainer:

✅ **No external database** - uses localStorage  
✅ **No configuration needed** - works immediately  
✅ **Password-based access** - multi-office support  
✅ **OpenAI Realtime API** - voice-to-voice AI  
✅ **CSV export** - download call history  
✅ **Role-based permissions** - admin/doctor/va  
✅ **Call history** - tracks all practice calls  
✅ **Real-time scoring** - immediate feedback

### Different from Inbound:

🔄 **Call direction:** VA calls patient (not patient calls office)  
🔄 **Scenario:** Following up on inquiry form submissions  
🔄 **Checkpoints:** Outbound-specific (introduction, health history, purpose...)  
🔄 **Color scheme:** Teal/dark (not purple)  
🔄 **Difficulty levels:** 2 levels (not 4)  
🔄 **Patient behavior:** AI-driven personalities (not scripted)

---

## 📁 File Structure

```
your-project/
├── index.html              (your working inbound trainer)
├── outbound-trainer.html   (new outbound trainer)
└── README.md
```

Both files work independently. Same deployment, same storage method.

---

## 🐛 Troubleshooting

### Issue: "Invalid access code"
**Fix:** Check password spelling. Passwords are case-sensitive.

### Issue: "OpenAI API error"
**Fix:** Verify API key is valid and has credits at https://platform.openai.com/account/billing

### Issue: Microphone not working
**Fix:** Allow microphone access in browser settings for your Vercel domain

### Issue: Can't see call history
**Fix:** Call history is stored in browser. Different browsers = different histories.

### Issue: Scores seem wrong
**Fix:** AI scoring can vary. If consistently wrong, check the evaluation prompt.

---

## 💡 Usage Tips

### Training Progression:

1. **Week 1:** Inbound Easy (master basics)
2. **Week 2:** Inbound Challenging (handle objections)
3. **Week 3:** **Outbound Easy** (learn proactive calling)
4. **Week 4:** **Outbound Challenging** (master conversion)

### Sample Outbound Opening:

```
"Hi, is this Jennifer Rodriguez? Great! This is [Your Name] 
calling from Dr. Jarvis's office at Brighton Spine & Wellness.

I'm following up on the inquiry form you submitted yesterday 
about your lower back pain. Do you have a quick minute to chat?"
```

### Key Differences:

| Inbound | Outbound |
|---------|----------|
| Patient calls you | You call patient |
| React to questions | Drive conversation |
| Answer inquiries | Build rapport + book |
| Patient is proactive | Patient may be passive |

---

## ✅ Ready to Deploy!

1. ✅ **No Supabase** needed (uses localStorage like your inbound)
2. ✅ **No configuration** required
3. ✅ **Upload to Vercel** (same as inbound process)
4. ✅ **Start training** your VAs immediately

**Your outbound trainer works exactly like your inbound trainer - just upload and use!**
