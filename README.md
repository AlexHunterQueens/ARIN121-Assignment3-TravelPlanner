# ARIN 121 Assignment 3: Travel Planner

A system prompt for an AI travel planning assistant, built for ARIN 121 (Queen's University). It runs in the Google AI Studio Playground. This version extends my Assignment 2 planner with an activity menu and a new multi-turn activity.

## Files

| File | What it is |
| --- | --- |
| `system-prompt.md` | The complete system prompt. Paste it into System instructions in the Playground. |
| `README.md` | This guide. |

The unchanged Assignment 2 prompt is the first commit of `system-prompt.md` on `main` ("Preserve Assignment 2 starting prompt").

## What the planner can do

| Activity | What happens |
| --- | --- |
| 1. Plan a trip | Collects the destination and trip length, then builds a day-by-day itinerary with morning, afternoon and evening activities. |
| 2. Estimate trip costs | Shows a per-person cost table as low to high ranges and compares the total to your budget. |
| 3. Choose between destinations (new) | Compares two or three places against your priorities, recommends one, and refines the recommendation using your concerns. |

Carried over from Assignment 2: confirmation of itinerary changes with a Highest-Impact Improvement tip, day trips, a check for ambiguous destination names (for example Kingston, Ontario or Kingston, Jamaica), and guardrails that keep the planner on travel topics.

## How to use the menu

Start with a general message such as "Hi, I need help with a trip." The planner replies with the menu and waits. Choose an activity in any of three ways:

- A number: `3`
- The activity name: `Choose between destinations`
- Your own words: `I can't decide between Lisbon and Porto`

If your first message already makes the activity clear, the planner skips the menu and starts that activity. Type `menu` at any time to see the menu again.

## How to use Choose between destinations

1. Select activity 3.
2. Give two or three destinations and one to three priorities, such as cost, food or less walking. Trip length, month, budget and group size are optional. The planner asks only for what is missing.
3. The planner shows a comparison table, recommends one destination, and asks whether any concern remains.
4. Raise a concern (for example "my friend has a bad knee") and the planner addresses it and says whether the recommendation changes. It handles up to three concerns.
5. When you accept, the planner gives a final recommendation and offers to plan the trip or estimate its costs.

## Switching activities

Ask for another activity at any point, by number, name or in your own words. The planner stops the current activity, says which one it is switching to, lists the details it is carrying forward (destination, trip length, month, group size, budget, priorities), and does not ask for them again. Say `stop` or `cancel` to end an activity and return to the menu.

## Testing

Tested in the Google AI Studio Playground with Gemini 4 Hydrogen, thinking level High, all tools off, a fresh conversation for each test.

| Test | Result |
| --- | --- |
| 1. General request, select the new activity, complete it | Menu shown, activity 3 ran to a final recommendation. |
| 2. Start an activity, give details, switch in own words | Switched to Plan a trip and kept all four details. |

## Limitations

- Costs and travel facts come from the model's general knowledge, not live data.
- The planner does not book anything.
- The two tests did not cover the three-concern limit or the stop and cancel path.
- Tested on one model only. Other models may follow the menu rules less strictly.
