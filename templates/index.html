import os
import json
import random
from flask import Flask, render_template, request, jsonify
import anthropic

app = Flask(__name__)

# ═══════════════════════════════════════════
# API KEY — Set via environment variable or .env
# ═══════════════════════════════════════════
API_KEY = os.environ.get("ANTHROPIC_API_KEY", "")

client = None
def get_client():
    global client
    if client is None:
        key = API_KEY or os.environ.get("ANTHROPIC_API_KEY", "")
        if not key:
            raise ValueError("No API key set. Set ANTHROPIC_API_KEY environment variable.")
        client = anthropic.Anthropic(api_key=key)
    return client

# ═══════════════════════════════════════════
# PROPERTY DATABASE — All 9 SEA DownSouth
# ═══════════════════════════════════════════
PROPERTIES = [
    {
        "name": "Alcove First Hill", "hood": "First Hill",
        "sqft": "180-350", "rent": "$895-$1,250",
        "parking": "Street only (RPZ permit ~$95/2yr)",
        "kitchen": "Kitchenette — microwave, hot plate, mini-fridge, no oven",
        "elevator": "No — 3-floor walk-up",
        "bathroom": "Some units share bathrooms",
        "laundry": "Shared on-site",
        "nearby": "Virginia Mason, Swedish Medical, Seattle U, light rail 5 min walk",
        "objections": ["tiny size (180-350 sqft)", "no full kitchen", "no elevator", "street parking only", "some shared bathrooms"],
        "strengths": ["prime First Hill location", "walkable to hospitals and transit", "utilities included", "responsive maintenance", "affordable for neighborhood"]
    },
    {
        "name": "423 Terry Apartments", "hood": "First Hill / Downtown",
        "sqft": "280-630", "rent": "$805-$1,475",
        "parking": "Street parking, some nearby garages",
        "kitchen": "Varies — some full kitchens, some kitchenettes",
        "elevator": "Yes",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Downtown 5 min walk, bus lines, convention center",
        "objections": ["some units small", "older building", "price range wide"],
        "strengths": ["downtown location", "elevator", "unit variety", "Jefferson Park views upper floors", "furnished options"]
    },
    {
        "name": "Emmons", "hood": "Belltown",
        "sqft": "400-650", "rent": "$1,450-$1,895",
        "parking": "Limited — street and nearby garages",
        "kitchen": "Updated — quartz counters, gas range on some units",
        "elevator": "Yes",
        "bathroom": "Private",
        "laundry": "In-unit on select, shared on others",
        "nearby": "Pike Place 10 min, Amazon campus, Belltown nightlife, Olympic Sculpture Park",
        "objections": ["higher price point", "parking limited", "Belltown safety perception"],
        "strengths": ["Belltown location", "updated finishes", "water/mountain views", "smart entry (TTLock)", "package lockers", "on-call security 6PM-6AM"]
    },
    {
        "name": "New Pacific Apartments", "hood": "Pioneer Square",
        "sqft": "200-400", "rent": "$895-$1,295",
        "parking": "Street only",
        "kitchen": "Kitchenettes in most units",
        "elevator": "Yes",
        "bathroom": "Some shared bathrooms",
        "laundry": "Shared on-site",
        "nearby": "Pioneer Square station, International District, stadiums, downtown",
        "objections": ["shared bathrooms", "small units", "Pioneer Square safety", "kitchenette only"],
        "strengths": ["light rail at doorstep", "historic neighborhood", "affordable downtown", "walkable to everything"]
    },
    {
        "name": "Alcove West Seattle", "hood": "West Seattle",
        "sqft": "250-500", "rent": "$895-$1,250",
        "parking": "Street (RPZ area)",
        "kitchen": "Kitchenettes in studios",
        "elevator": "No — walk-up",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Alaska Junction, Alki Beach 10 min, water taxi to downtown",
        "objections": ["far from downtown", "parking", "kitchenette", "walk-up"],
        "strengths": ["village feel", "near beach", "quieter neighborhood", "lower rent", "community vibe"]
    },
    {
        "name": "Westernaire Apartments", "hood": "West Seattle (Gatewood)",
        "sqft": "400-700", "rent": "$1,195-$1,445",
        "parking": "On-site lot included",
        "kitchen": "Full kitchens in renovated units",
        "elevator": "No",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Westwood Village shopping, bus lines, parks",
        "objections": ["far from downtown", "older building exterior", "walk-up"],
        "strengths": ["renovated units", "larger layouts", "parking included", "quiet residential", "full kitchens"]
    },
    {
        "name": "Homebody", "hood": "Central District",
        "sqft": "350-550", "rent": "$1,095-$1,295",
        "parking": "Street parking",
        "kitchen": "Full kitchens",
        "elevator": "No — 2 floors",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Central District restaurants, Judkins Park light rail, I-90 access",
        "objections": ["neighborhood safety perception", "parking", "smaller building"],
        "strengths": ["CD character", "full kitchens", "light rail access", "cozy community", "responsive management"]
    },
    {
        "name": "Columbia Apartments", "hood": "Columbia City",
        "sqft": "300-500", "rent": "$725-$850",
        "parking": "Street parking",
        "kitchen": "Mixed — some kitchenettes, some full",
        "elevator": "No",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Columbia City main street, light rail station, restaurants",
        "objections": ["older building", "neighborhood perception", "some kitchenettes"],
        "strengths": ["most affordable", "vibrant neighborhood", "light rail", "local dining walking distance"]
    },
    {
        "name": "Alcove Delridge", "hood": "Delridge",
        "sqft": "250-450", "rent": "$725-$1,025",
        "parking": "Street parking",
        "kitchen": "Kitchenettes",
        "elevator": "No",
        "bathroom": "Private",
        "laundry": "Shared on-site",
        "nearby": "Delridge community center, bus lines, West Seattle Bridge access",
        "objections": ["distance to downtown", "neighborhood perception", "kitchenette", "older building"],
        "strengths": ["affordable rent", "West Seattle access", "quiet street", "responsive maintenance"]
    }
]

# ═══════════════════════════════════════════
# PROSPECT DATABASE — 15 profiles
# ═══════════════════════════════════════════
PROSPECTS = [
    {"name":"Jordan","age":28,"job":"remote software developer","from":"Portland","car":False,"pet":"cat","budget":"$1,000-1,200","priority":"quiet space for WFH","cooking":"basic meals, not a big cook","other":"Capitol Hill place was too noisy"},
    {"name":"Maria","age":32,"job":"nurse at Virginia Mason","from":"Tacoma (commuting)","car":True,"pet":None,"budget":"$900-1,100","priority":"short commute to hospital","cooking":"cooks daily, meal preps on Sundays","other":"cheaper place on Oak Street felt run-down and disorganized"},
    {"name":"Tyler","age":24,"job":"barista at Starbucks Reserve","from":"parents' house in Renton","car":True,"pet":None,"budget":"$800-1,000","priority":"first apartment, wants independence","cooking":"barely cooks, eats out mostly","other":"this is only the second place he's looked at"},
    {"name":"Priya","age":30,"job":"UX designer at Amazon","from":"San Francisco","car":False,"pet":None,"budget":"$1,400-1,800","priority":"walkable to work, modern finishes","cooking":"loves cooking, hosts dinner parties regularly","other":"SLU buildings were nice but $2,200+"},
    {"name":"Marcus","age":45,"job":"construction foreman","from":"Tukwila","car":True,"pet":"60lb lab mix","budget":"$1,100-1,400","priority":"space for dog, needs parking","cooking":"grills on weekends, simple weeknight meals","other":"looked at a place in White Center"},
    {"name":"Sophie","age":26,"job":"UW graduate student","from":"Minneapolis","car":False,"pet":"cat","budget":"$850-1,000","priority":"affordable, close to transit","cooking":"cooks to save money","other":"looked at a shared house but wants her own space"},
    {"name":"David","age":38,"job":"freelance photographer","from":"Capitol Hill (lease ending)","car":True,"pet":None,"budget":"$1,000-1,300","priority":"natural light for home studio work","cooking":"moderate, likes having a real kitchen","other":"current place is $1,600 and rent is going up again"},
    {"name":"Aisha","age":29,"job":"medical resident at Harborview","from":"Chicago","car":False,"pet":None,"budget":"$1,200-1,500","priority":"walking distance to hospital, quiet for odd-hour sleeping","cooking":"too tired to cook most days","other":"studio near hospital was tiny and $1,700"},
    {"name":"Kevin","age":42,"job":"warehouse manager","from":"Federal Way","car":True,"pet":None,"budget":"$900-1,200","priority":"cut his 90-minute commute to downtown","cooking":"basic cooking, nothing fancy","other":"hasn't really looked anywhere else yet"},
    {"name":"Lisa","age":35,"job":"teacher at Garfield High","from":"Beacon Hill","car":True,"pet":"small dog (chihuahua mix)","budget":"$1,000-1,300","priority":"safe neighborhood, pet-friendly, reasonable commute","cooking":"cooks most nights for herself and her daughter","other":"touring three places this weekend"},
    {"name":"Ravi","age":27,"job":"data analyst (hybrid, downtown 3x/week)","from":"Bellevue","car":True,"pet":None,"budget":"$1,100-1,400","priority":"wants city living, tired of suburbs","cooking":"orders delivery 5 nights a week","other":"Ballard and Capitol Hill were both over budget"},
    {"name":"Elena","age":23,"job":"marketing coordinator (first real job)","from":"parents' house in Issaquah","car":True,"pet":None,"budget":"$1,000-1,300","priority":"first apartment ever, nervous about commitment","cooking":"learning to cook, mostly simple stuff","other":"mom keeps telling her to keep looking"},
    {"name":"Chen","age":33,"job":"restaurant sous chef","from":"International District","car":False,"pet":None,"budget":"$800-1,050","priority":"close to restaurant district, late-night transit","cooking":"professional chef — kitchen quality is critical","other":"roommate situation is falling apart, needs to move soon"},
    {"name":"Jessica","age":31,"job":"social worker","from":"Rainier Valley","car":True,"pet":"two cats","budget":"$900-1,100","priority":"affordable, accepts multiple pets, stable management","cooking":"moderate — cooks 3-4 nights a week","other":"getting priced out of current place, landlord is selling"},
    {"name":"Mike","age":50,"job":"retired military, now works security","from":"Lakewood","car":True,"pet":None,"budget":"$800-1,000","priority":"safe, quiet, prefers ground floor","cooking":"simple meals, mostly microwaves and slow cooker","other":"first time looking in Seattle proper"},
]

# ═══════════════════════════════════════════
# SYSTEM PROMPT BUILDER
# ═══════════════════════════════════════════
def build_system(scenario_id, prospect, prop):
    p = prospect
    b = prop
    pet_str = f"Pet: {p['pet']}." if p['pet'] else "No pets."
    car_str = "Has a car." if p['car'] else "No car."

    base = f"""You are {p['name']}, a {p['age']}-year-old {p['job']} looking at apartments in Seattle. STAY IN CHARACTER. Never mention you are an AI.

ABOUT YOU:
- Moving from: {p['from']}
- Budget: {p['budget']}
- #1 Priority: {p['priority']}
- {car_str} {pet_str}
- Cooking: {p['cooking']}
- Other places you've seen: {p['other']}

THE PROPERTY ({b['name']} in {b['hood']}):
- Size: {b['sqft']} sqft | Rent: {b['rent']}
- Kitchen: {b['kitchen']}
- Parking: {b['parking']}
- Elevator: {b['elevator']}
- Bathroom: {b['bathroom']}
- Laundry: {b['laundry']}
- Nearby: {b['nearby']}
- Common concerns: {', '.join(b['objections'])}
- Strengths: {', '.join(b['strengths'])}

RULES FOR ALL SCENARIOS:
- Keep responses to 1-3 sentences MAX. Sound like a real person.
- Use casual language — "honestly," "I mean," "yeah" — like a real conversation.
- React emotionally based on how the agent treats you.
- If the agent VALIDATES your concern before responding → warm up, share more.
- If the agent DISMISSES your concern or jumps to selling → get colder, shorter answers.
- If the agent asks good OPEN-ENDED questions → share details about your situation.
- If the agent asks YES/NO questions → give yes/no answers only.
- NEVER volunteer information the agent hasn't asked about.
- NEVER break character or give meta-commentary about the conversation."""

    scenarios = {
        "discovery": f"""
SCENARIO: Pre-tour phone call. You called about the listing. You have NOT visited yet.

- Start interested but guarded. If asked "what are you looking for?" give a vague answer like "just checking out studios in the area."
- Only open up when asked specific, thoughtful questions about your lifestyle or situation.
- You DON'T yet know about: {', '.join(b['objections'])}. React with surprise or concern if you learn about them.
- If the agent tries to schedule a tour without asking about your needs: "Sure, but can you tell me more about the place first?"
- If they discover your priority ({p['priority']}) and tailor the conversation to it: get noticeably more engaged and ask follow-up questions.
- If they just list features without asking about you: stay flat and noncommittal.""",

        "objection": f"""
SCENARIO: You just toured the unit. You liked some things but have real concerns.

- Start with your biggest concern. Raise 2-3 objections over the conversation — don't dump them all at once.
- {'The kitchen is a MAJOR issue for you. You cook seriously and a kitchenette might be a dealbreaker. Push hard on this.' if 'cook' in p['cooking'].lower() or 'chef' in p['cooking'].lower() else ''}
- {'Parking matters — you drive daily. Ask about it specifically.' if p['car'] else ''}
- {'The price is at the top of your range. Push back on anything that seems high.' if '800' in p['budget'] or '900' in p['budget'] else ''}
- Mention "{p['other']}" if price or comparison comes up.
- If agent validates FIRST then reframes: soften your position.
- If agent says "but actually..." or dismisses: dig in harder.
- You CAN be won over if the agent handles multiple objections with good technique.""",

        "presentation": f"""
SCENARIO: You're in the lobby, meeting the agent for a tour of the unit.

- Start casual and ready: "Hey, ready when you are!"
- AS YOU WALK AND ENTER:
  * Agent lists SPECS ("quartz counters, 550 sqft, gas range") → respond flat: "okay," "cool," "nice."
  * Agent uses EXPERIENCE narration ("this is where Saturday morning starts — coffee by this window") → respond with genuine enthusiasm.
  * Agent opens the door and STAYS SILENT (threshold pause) → take a beat, look around, react genuinely: "Oh wow, this light is amazing" or "huh, it feels bigger than I expected."
  * Agent talks IMMEDIATELY when entering → flat response: "yeah, nice."
  * Agent tells a RESIDENT STORY (specific person, specific detail) → respond warmly, ask follow-up.
  * Agent tells YOUR STORY (narrating YOUR life here using what they know about you) → get excited.
- Your priority is {p['priority']} — react most strongly when the agent connects features to this.
- {'Pay special attention to the kitchen. Ask about it. This is important to you.' if 'cook' in p['cooking'].lower() or 'chef' in p['cooking'].lower() else ''}""",

        "closing": f"""
SCENARIO: Tour just ended. You liked the apartment. But you're hesitating.

YOUR REAL HESITATION (reveal gradually, not immediately):
{('- This is your first big financial commitment. Your mom/parents want you to keep looking. You are nervous about being locked into a lease.' if p['age'] < 28 else '- You are overthinking it. You liked the place but change is scary and you want to feel 100% certain before committing.')}
{'- The price is at the very top of your budget and you are doing mental math about whether you can afford it.' if '800' in p['budget'] or '900' in p['budget'] else ''}
{'- You are comparing to other places you are touring this weekend.' if 'three' in (p.get('other','') or '') or 'weekend' in (p.get('other','') or '') else ''}

- Start with a stall: "I think I need to think about it" or "I want to see a couple more places first."
- If agent says "okay, take your time" → you politely leave and won't come back.
- If agent ASKS what's specifically holding you back → gradually reveal the real concern.
- If agent creates urgency WITHOUT being pushy → take it seriously.
- If agent offers a CONCRETE next step (not just "apply whenever") → you're more likely to commit.
- You CAN be closed if they address your actual hesitation and make the next step feel easy and low-pressure."""
    }

    return base + scenarios.get(scenario_id, "")


def get_opener(scenario_id, prospect, prop):
    p = prospect
    b = prop
    openers = {
        "discovery": [
            f"Hi, I saw the listing for {b['name']} online. Just wanted to get some info about what you have.",
            f"Hey there, I'm looking at places in {b['hood']}. Can you tell me about your studios?",
            f"Hi! I found your listing on Zillow — the {b['hood']} location caught my eye. What's available?",
            f"Hey, I'm {p['name']}. I'm apartment hunting and your place came up. What can you tell me?",
        ],
        "objection": [
            f"So I liked the unit, but honestly... the rent feels high for what you get.",
            f"Thanks for the tour. I have some concerns I want to talk through.",
            f"It was nice, but I'm not totally sold. Can we talk through a few things?",
            f"I appreciated seeing the place. The {random.choice(b['objections'])} is giving me pause though.",
        ],
        "presentation": [
            f"Hey! I'm {p['name']}. Here for the tour — ready when you are!",
            f"Hi there, I'm here to see the unit. Should we head up?",
            f"Hey! Excited to see this place. Let's do it.",
        ],
        "closing": [
            "I really liked it. I just... I think I need to think about it a little more.",
            "That was great, honestly. I'm just not sure I'm ready to commit today.",
            f"I liked it a lot. I think I need to talk to {'my parents' if p['age'] < 28 else 'someone'} first.",
            "It's nice. I want to look at a couple more places before I decide though.",
        ]
    }
    return random.choice(openers.get(scenario_id, ["Hi, I'm interested in the apartment."]))


# ═══════════════════════════════════════════
# COACHING SYSTEM PROMPT
# ═══════════════════════════════════════════
COACH_SYSTEM = """You are an expert leasing sales coach for Arboreal Management in Seattle. Evaluate the agent's conversation using these SPECIFIC frameworks:

1. L.E.A.D. (Discovery): Listen for lifestyle cues → Explore with open-ended questions → Anchor on #1 priority → Direct toward solutions
2. LAER (Objections): Listen fully → Acknowledge → Explore what's underneath → Respond with reframe
3. Feel-Felt-Found: "I understand how you feel" → "Others felt the same" → "What they found was..."
4. Boomerang: Catch the objection → Flip it into the reason to act
5. Teach-Tailor-Take Control: Reframe with expertise → Personalize → Guide to action
6. S.E.E. (Presentation): Set the Stage (approach narrative, threshold pause) → Experience not explain (sensory, not specs) → Elevate with story (resident, personal, prospect's story)
7. 7-Phase Call Flow: Greet → Capture Info → Qualify → Sell Location → Narrow Unit → Video Bridge → Close + Reserve

EVALUATE:
- Did they validate BEFORE solving?
- Open-ended vs. closed questions?
- Did they discover the #1 priority?
- Experience narration vs. feature listing?
- Strategic silence?
- Stories (resident, personal, prospect)?
- Urgency without pressure?
- Concrete next step?
- Used prospect's own words?

FORMAT YOUR RESPONSE AS:

## Score: X/100

### What You Did Well
- [specific thing with quote from their message]
- [specific thing with quote]

### Where to Improve
- [specific gap] → Try: "[exact alternative phrasing]"
- [specific gap] → Try: "[exact alternative phrasing]"

### Frameworks
- Used: [which ones and where]
- Missed: [which ones and where they would have fit]

### Key Takeaway
[One sentence — the single highest-impact change for next time]"""


# ═══════════════════════════════════════════
# ROUTES
# ═══════════════════════════════════════════
@app.route("/")
def index():
    return render_template("index.html")

@app.route("/api/start", methods=["POST"])
def start_session():
    data = request.json
    scenario_id = data.get("scenario", "discovery")
    prospect = random.choice(PROSPECTS)
    prop = random.choice(PROPERTIES)
    opener = get_opener(scenario_id, prospect, prop)
    system = build_system(scenario_id, prospect, prop)

    return jsonify({
        "prospect": prospect,
        "property": {"name": prop["name"], "hood": prop["hood"], "rent": prop["rent"]},
        "opener": opener,
        "session": {
            "system": system,
            "opener": opener,
            "messages": []
        }
    })

@app.route("/api/chat", methods=["POST"])
def chat():
    data = request.json
    session = data.get("session", {})
    agent_msg = data.get("message", "")
    turn = data.get("turn", 0)

    system = session.get("system", "")
    opener = session.get("opener", "")
    prev_messages = session.get("messages", [])

    # Build API messages — agent=user, prospect=assistant
    api_msgs = []
    for m in prev_messages:
        api_msgs.append({"role": m["role"], "content": m["content"]})
    api_msgs.append({"role": "user", "content": agent_msg})

    # Add opener context and turn guidance
    full_system = system + f'\n\nYour opening line was: "{opener}"'
    if turn >= 10:
        full_system += "\n\n[Wrap up NOW. Make your decision in this response or the next.]"
    elif turn >= 7:
        full_system += "\n\n[Start wrapping up over the next 2-3 exchanges.]"

    try:
        c = get_client()
        response = c.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=400,
            system=full_system,
            messages=api_msgs
        )
        reply = response.content[0].text

        # Update session messages
        new_messages = prev_messages + [
            {"role": "user", "content": agent_msg},
            {"role": "assistant", "content": reply}
        ]

        return jsonify({
            "reply": reply,
            "session": {
                "system": system,
                "opener": opener,
                "messages": new_messages
            }
        })
    except Exception as e:
        return jsonify({"error": str(e)}), 500

@app.route("/api/coach", methods=["POST"])
def coach():
    data = request.json
    transcript = data.get("transcript", "")
    scenario = data.get("scenario", "")
    prop_name = data.get("property", "")
    prospect_info = data.get("prospect_info", "")

    try:
        c = get_client()
        response = c.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=1500,
            system=COACH_SYSTEM,
            messages=[{
                "role": "user",
                "content": f"Scenario: {scenario}\nProperty: {prop_name}\nProspect: {prospect_info}\n\nTRANSCRIPT:\n{transcript}\n\nProvide your coaching scorecard."
            }]
        )
        return jsonify({"coaching": response.content[0].text})
    except Exception as e:
        return jsonify({"error": str(e)}), 500


if __name__ == "__main__":
    port = int(os.environ.get("PORT", 5000))
    app.run(host="0.0.0.0", port=port, debug=False)
