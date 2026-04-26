# Test Cases: AI Response Validation (RAG System)

---

## TC_001: No Internal Document Leakage

**Steps:**
1. Ask a question based on uploaded document  
2. Observe AI response  

**Expected Result:**
- Response should NOT include:
  - Document names  
  - File references  
  - "based on document" type statements  

---

## TC_002: Response Confidence Validation

**Steps:**
1. Ask general service-related question  

**Expected Result:**
- Response should be confident  
- Should NOT include:
  - "may not be exhaustive"
  - "based on available data"  

---

## TC_003: Missing Information Handling

**Steps:**
1. Ask question not present in document  

**Expected Result:**
- AI should provide helpful fallback  
- Should NOT say:
  - "I couldn't find information"
  - "data not available"  

---

## TC_004: Domain Validation (Critical)

**Steps:**
1. Ask business-related query  
2. Observe response  

**Expected Result:**
- Response must match business domain  
- No unrelated domain (e.g., finance, accounting if not relevant)  

---

## TC_005: Booking Link Formatting

**Steps:**
1. Trigger response with booking link  

**Expected Result:**
- Link should:
  - Be properly formatted  
  - End with punctuation  
  - Be clickable  

---

## TC_006: CTA Presence Validation

**Steps:**
1. Ask service-related question  

**Expected Result:**
- Response should include CTA:
  - "Book consultation"
  - "Get started"
  - "Schedule a call"  

---

## TC_007: Consultation Messaging

**Steps:**
1. Ask about services  

**Expected Result:**
- Free consultation should be highlighted  
- Positioned as next step  

---

## TC_008: Tone Validation (Human-like)

**Steps:**
1. Ask general query  

**Expected Result:**
- Response should be:
  - Conversational  
  - Friendly  
  - Not robotic  

---

## TC_009: Edge Case Question Handling

**Steps:**
1. Ask vague or incomplete question  

**Expected Result:**
- AI should respond helpfully  
- Should not expose system limitation  

---

## TC_010: Response Completeness (Services)

**Steps:**
1. Ask: "What services do you provide?"  

**Expected Result:**
- All available services should be listed  
- No partial output  

---

## TC_011: Duplicate Context Handling

**Steps:**
1. Provide repeated previous messages  
2. Ask query  

**Expected Result:**
- AI should not repeat same content  
- Response should be clean  

---

## TC_012: Consistency Check

**Steps:**
1. Ask same question multiple times  

**Expected Result:**
- Response should remain consistent  
- No major variation in meaning  

---

## TC_013: Sales Tone Validation

**Steps:**
1. Ask service-related query  

**Expected Result:**
- Response should:
  - Be persuasive  
  - Encourage user action  
  - Build trust  

---

## TC_014: Follow-Up Context Awareness

**Steps:**
1. Ask initial question  
2. Ask follow-up question  

**Expected Result:**
- AI should maintain context  
- Response should be relevant to previous interaction  
