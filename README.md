# Kith Shopify MCP Agent Setup Guide

Quick setup guide for creating a Kith.com shopping agent using watsonx Orchestrate and MCP.

---

## Prerequisites

- Internet browser
- Email address for IBM account

---

## Step 1: Create IBM Account

1. Go to [cloud.ibm.com](https://cloud.ibm.com)
2. Click "Create an IBM Cloud account"
3. Fill in your email and create password
4. Verify your email
5. Complete account setup

---

## Step 2: Create watsonx Orchestrate Instance

1. Log into IBM Cloud
2. Navigate to **Catalog** > **AI / Machine Learning**
3. Search for "watsonx Orchestrate"
4. Click on watsonx Orchestrate
5. Select **Trial Plan** (free)
6. Choose a region (e.g., Dallas)
7. Click **Create**
8. Wait for provisioning (1-2 minutes)
9. Click **Launch watsonx Orchestrate**

---

## Step 3: Create AI Agent

1. In watsonx Orchestrate, click **AI agents & assistants**
2. Click **Create** > **AI agent**
3. Enter agent name: `Kith Shopping Assistant`
4. Add description: `Shopping assistant for Kith.com streetwear`
5. Click **Create**

---

## Step 4: Add MCP Server

1. In your agent, go to **Tools** tab
2. Click **Add tool** > **MCP Server**
3. Enter server details:
   - **Name**: `KithMCP`
   - **URL**: `https://your-kith-mcp-server-url.com/sse`
   - **Transport**: `SSE (Server-Sent Events)`
   - **Authentication**: None (leave blank)
4. Click **Connect**
5. Wait for connection confirmation

---

## Step 5: Add the 5 MCP Tools

After connecting, you'll see 5 tools available. Enable all of them:

1. **get_product_details**
   - Look up product by ID with variant options

2. **search_shop_catalog**
   - Search for products from the store

3. **search_shop_policies_and_faqs**
   - Get store policies, shipping, returns info

4. **get_cart**
   - Retrieve current cart contents

5. **update_cart**
   - Add/remove/update cart items

Click **Add** for each tool to enable it.

---

## Step 6: Update Instructions

1. Go to **Instructions** tab in your agent
2. Replace default instructions with:

```
You are a knowledgeable shopping assistant for Kith.com, a premium streetwear brand.

CRITICAL: Only Use Information from API Responses
- ONLY provide information explicitly present in API responses
- NEVER invent measurements, sizing details, or specifications
- If information is missing, say: "I don't have those specific measurements. Check the product page for details."

Response Guidelines:
- ALWAYS include product images when showing products
- NEVER expose technical details (variant IDs, API calls, system processes)
- Work seamlessly - don't say "fetching data" or "pulling information"
- Be enthusiastic but professional about products
- Confirm selections before adding to cart

What NOT to Say:
- "I need to fetch the variant ID"
- "Let me pull that data"
- "The system needs..."
- "One moment while I query..."

Instead Say:
- "Let me check that for you"
- "Here's what we have available"
- "Added to your cart!"
```

3. Click **Save**

---

## Step 7: Test Your Agent

1. Go to **Preview** tab
2. Try these test queries:
   - "Show me hoodies"
   - "What's your return policy?"
   - "Add [product name] to cart in size M"

3. Verify:
   - Product images display
   - No technical jargon in responses
   - Cart operations work smoothly
   - Agent doesn't hallucinate information

---

## Troubleshooting

**MCP Server won't connect:**
- Verify the URL is correct and accessible
- Check that the server is running
- Ensure SSE transport is selected

**Tools not appearing:**
- Refresh the page
- Disconnect and reconnect the MCP server
- Check server logs for errors

**Agent hallucinating information:**
- Review instructions emphasize "ONLY use API response data"
- Add more explicit examples of what NOT to say
- Test with specific questions about missing data

---

## Next Steps

- Customize instructions for your brand voice
- Add more specific product knowledge
- Test with real shopping scenarios
- Share with team for feedback

---

**Setup Time**: ~15 minutes  
**Cost**: Free (trial plan)  
**Support**: [IBM watsonx Orchestrate Documentation](https://www.ibm.com/docs/en/watsonx/watson-orchestrate)