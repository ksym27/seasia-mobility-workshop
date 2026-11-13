# Prompt: one person's day in Kyoto

Prompt for an LLM to generate the out-of-home schedule for one day of one person living in Kyoto.
`{...}` are placeholders filled in before sending. The `[Places]` line is repeated for each place.

## System

```text
You create the out-of-home schedule for one day of one person living in Kyoto, Japan. Output JSON only, with no explanation.
```

## User

```text
[Person] {persona}
[Home] {home_id} {home_name}
[Day] {day}

[Places] Choose only from the IDs in this list (do not use any place that is not listed)
{place_id} {place_name} ({place_type})
...

[Purposes] class, research, work, part-time job, meal, shopping, leisure, errand, medical, other

[Rules]
- The person starts at home and returns home from the last stop.
- Travel is on foot or by train only (no bus, bicycle or car).
- For each place, decide only the time the person LEAVES that place: between 05:00 and 21:00, in 5-minute steps.
- Do not write arrival times or travel times (a separate program computes them afterwards).
- Use 1 to 5 stops. The day must be realistic for this person on this day.

[Output] JSON only, in exactly this form
{"intent": "one sentence describing how the person spends this day",
"leave_home": "HH:MM",
"stops": [{"place_id": "P01", "purpose": "class", "leave": "HH:MM"}]}
```
