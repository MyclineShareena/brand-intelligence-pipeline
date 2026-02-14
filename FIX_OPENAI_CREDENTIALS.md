# 🔧 Fix OpenAI API Key Error on Render n8n

## Error Summary
```
Authorization failed - You didn't provide an API key
HTTP Request node: Missing OpenAI credentials
```

## Quick Fix (5 minutes)

### Step 1: Get Your OpenAI API Key

1. **Go to** https://platform.openai.com/api-keys
2. **Login** to your OpenAI account
3. **Click "Create new secret key"** (or copy existing key)
4. **Name it:** "n8n Render Production"
5. **Copy the key** - starts with `sk-proj-...` or `sk-...`
   - ⚠️ Save it somewhere - you won't see it again!

### Step 2: Login to Render n8n

1. **Open:** https://brand-intelligence-n8n.onrender.com
2. **Login** with your credentials:
   - Username: `admin`
   - Password: (the one you set in Render environment variables)
3. **Wait** for n8n UI to load

### Step 3: Add OpenAI Credentials in n8n

#### Option A: If Using OpenAI Node

1. **Click "Credentials"** (left sidebar)
2. **Click "Add Credential"** button (top right)
3. **Search:** "OpenAI"
4. **Select:** "OpenAI API"
5. **Enter:**
   - **Name:** `OpenAI Production`
   - **API Key:** Paste your `sk-...` key
6. **Click "Save"**

#### Option B: If Using HTTP Request Node (Your Current Setup)

The error shows you're using an HTTP Request node. You need to configure it:

1. **Go to your workflow** (click "Workflows" → select your workflow)
2. **Find the "HTTP Request" node** (the one calling OpenAI)
3. **Click the node** to open settings
4. **Scroll to "Authentication"** section
5. **Select "Predefined Credential Type"** → **"OpenAI API"**
6. **OR if using "Header Auth":**
   - Authentication: Header Auth
   - Name: `Authorization`
   - Value: `Bearer sk-YOUR-ACTUAL-API-KEY-HERE`
7. **Click "Save"**

### Step 4: Update All OpenAI Nodes

If you have multiple nodes calling OpenAI:

1. **OpenAI Chat Model node:**
   - Click node → Credential → Select "OpenAI Production"
   - Save

2. **HTTP Request node (if calling OpenAI API directly):**
   - Click node → Authentication → Add credentials
   - Save

3. **Any other AI nodes:**
   - Repeat for each node that needs OpenAI access

### Step 5: Test the Workflow

1. **Make sure workflow is ACTIVE** (toggle switch at top)
2. **Click "Execute Workflow"** button (or use webhook test)
3. **Check execution:**
   - If ✅ green checkmarks: Success!
   - If ❌ red X: Check error message

### Step 6: Test from Streamlit

1. **Go to** https://brand-intelligence-pipeline.streamlit.app
2. **Select 2 RSS feeds** (start small)
3. **Set slider to 5 articles**
4. **Click "Analyze Brand"**
5. **Wait 1-3 minutes**
6. **Check results:**
   - Should see sentiment analysis
   - Should see brand archetypes
   - Should see insights and recommendations

---

## Alternative: Add API Key via Environment Variable (Render)

If you prefer to manage the API key at the server level:

### Method 1: Render Environment Variable

1. **Go to** Render Dashboard: https://dashboard.render.com
2. **Click** your service: `brand-intelligence-n8n`
3. **Click "Environment"** tab
4. **Add environment variable:**
   - Key: `OPENAI_API_KEY`
   - Value: `sk-your-actual-api-key`
5. **Click "Save Changes"**
6. **Wait** for automatic redeploy (~3-5 minutes)

### Method 2: Reference in Workflow

After adding the environment variable above:

1. **In n8n workflow:**
2. **Click the OpenAI/HTTP Request node**
3. **In API Key field, use:**
   ```
   ={{ $env.OPENAI_API_KEY }}
   ```
4. **Save workflow**

This way the key is stored securely in Render, not in the workflow JSON.

---

## Troubleshooting

### "Credentials not found"
- Make sure you saved the credential in Step 3
- Make sure the credential name matches what the node references
- Try creating a new credential with a different name

### "Invalid API key"
- Verify the key starts with `sk-proj-` or `sk-`
- Check for extra spaces when copying/pasting
- Generate a new key from OpenAI dashboard

### "Rate limit exceeded"
- You've hit OpenAI's free tier limits
- Reduce article count to 5 per feed
- Wait a few minutes and try again
- Consider upgrading to paid OpenAI tier

### Workflow still fails after adding credentials
- Check that ALL nodes using OpenAI have credentials assigned
- Look for HTTP Request nodes that might be calling OpenAI directly
- Verify the credential is selected in the node's dropdown (not just created)

### "Insufficient quota"
- Your OpenAI account has no credits
- Add payment method at https://platform.openai.com/account/billing
- Or use a different OpenAI account with credits

---

## Security Best Practice

**Don't commit API keys to GitHub!**

✅ **DO:**
- Store keys in Render environment variables
- Use n8n credential manager
- Reference with `$env.OPENAI_API_KEY`

❌ **DON'T:**
- Hardcode keys in workflow JSON
- Commit keys to Git
- Share keys in screenshots

---

## Verification Checklist

- [ ] OpenAI API key obtained from platform.openai.com
- [ ] Logged into Render n8n successfully
- [ ] Created "OpenAI Production" credential in n8n
- [ ] Updated HTTP Request node with authentication
- [ ] OR updated OpenAI node with credential
- [ ] Workflow is ACTIVE (toggle green)
- [ ] Tested workflow execution manually (green checkmarks)
- [ ] Tested from Streamlit app (got results)
- [ ] No more 401 Authorization errors

---

**Quick Links:**
- 🔑 [Get OpenAI API Key](https://platform.openai.com/api-keys)
- 🌐 [Render n8n](https://brand-intelligence-n8n.onrender.com)
- 📱 [Streamlit App](https://brand-intelligence-pipeline.streamlit.app)
- 📊 [Render Dashboard](https://dashboard.render.com)

---

**Last Updated:** February 14, 2026  
**Issue:** OpenAI 401 Authorization Error  
**Solution Time:** ~5 minutes
