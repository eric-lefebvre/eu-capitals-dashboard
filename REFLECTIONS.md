## The decision this dashboard supports
> **Reflection — before you build anything:** if you personally had to choose a
> destination, how would you weigh good weather against low CO₂? Would you ignore
> one of them entirely? Write 1-2 sentences now — you'll compare this to what the
> dashboard actually computes later in this TD.

I would ignore low C02 completly. Good weather is important because I would probably walk around the city a lot.

## Stage 1 — Acquisition: a static reference table and a live weather API
> **Reflection — acquisition reliability:** before reading the docstring above a
> second time: why would making 26 separate API connections from the same script,
> in a loop, be *more* likely to fail than making 1 connection for all 26 capitals
> at once — not just slower, but more likely to actually fail? Write your guess,
> then check it against the comment in `fetch_weather_batch`.

26 API connections would be more likely to fail than 1 because API calls are rate limited, so the more calls you make the more likely they are to be ignored because you are not allowed to make any other.

> **Reflection — provenance (CM3):** the CO₂ figure (0.15 kg CO₂e/km) is a rounded
> value from a real, cited range (0.12-0.15, DEFRA-style short-haul factors) that
> the script's own comment says to "verify/update." If this dashboard were going to
> be used by real travelers next year instead of graded once, what would you
> actually do about this number before publishing it?

I would update it, or automate its update so I don't have to do it anymore.

## Stage 2 — Cleaning & transformation: turning raw numbers into comparable scores
> **Reflection — relative vs. absolute:** `normalize()` finds the best and worst
> value *within this list of 26 capitals* and stretches everything between them to
> 0-1. If a 27th, unusually cold and rainy capital were added to the list, would a
> mediocre capital's real temperature change? Would its *score* change? What does
> that tell you about the difference between a measurement and a KPI built on top of
> it (CM2)?

The real temperature of the city obviously would not change but its score would because there is now a new 0 value on that normalize vector that is lower than the previous. Let's say a mediocre capital had a score of 0.1, if I add a 27th that is particularly cold and rainy, that score could now become something like 0.2. That means the KPI which helps us choose is accurate because the city is less rainy and cold than the worst one, but its real temperature is still the same.

## Stage 3 — KPI definition: combining weather and CO₂ into one number
> **Reflection — predict, then check:** based on the personal weighting you wrote
> down at the very start of this TD, which capital do you *predict* will come out
> on top once you run this script for real? Write the city name and one sentence of
> reasoning now, before you run anything.

Madrid ? Because it's often sunny and hot there ?

## Stage 5 — Visualization for decision support