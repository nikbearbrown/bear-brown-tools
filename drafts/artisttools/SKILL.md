---
name: artisttools
description: "artist.tools checker Use when — NEEDS TRIGGER."
---
# Forensic Playlist Audit: Auditing the Auditor
**Purpose:** Stress-test an artist.tools "Clean" or "Likely Bot-Free" verdict using Google Deep Research + Spotify for Artists (SFA) private data. Sophisticated bot networks are calibrated to stay *just below* automated scanner thresholds. These prompts force analysis of intent, not just shape.

---

## STEP 0 — INPUT FORM (Fill Before Running Any Prompt)

```
SCANNER NAME:         [e.g., artist.tools]
SCANNER VERDICT:      [e.g., "Likely Bot-Free" / "Clean" / "Risky"]
PLAYLIST NAME:        [e.g., "Late Night Vibes"]
PLAYLIST URL:         [https://open.spotify.com/playlist/...]
PLAYLIST FOLLOWER COUNT (from scanner):  [e.g., 12]
PROMOTER / SUBMISSION SERVICE NAME:     [e.g., Sassify LLC / SubmitHub curator X]
YOUR TRACK PLACED:    [Track name]
YOUR TRACK PLACEMENT DATE:              [e.g., 2025-03-01]
DAILY STREAMS FROM THIS PLAYLIST (SFA): [e.g., 400/day]
TOP CITIES FROM SFA FOR THIS PLAYLIST:  [e.g., Ashburn VA, Helsinki, Dublin]
SKIP RATE (if visible in SFA):          [e.g., High / Normal / Unknown]
SUBSCRIPTION CANCELED? (Y/N):           [If yes → date canceled, streams after cancellation]
```

---

## PROMPT 1 — Linear Drip Evasion Check
*Target: Identify "Drip Script" growth designed to fool spike-detection filters.*

**Google Deep Research Prompt:**
> "Analyze the follower growth history of the Spotify playlist [PLAYLIST NAME / URL]. I need to determine if the growth pattern is organic or programmatic. Specifically: Does the chart show perfect linear growth of a fixed number of followers per day (e.g., +3 to +5 every single day for 30+ days with no deviation)? Has the playlist ever recorded zero or negative daily growth? Cross-reference any available third-party tracking data (Chartmetric, Spotify Charts, Kworb, or web-cached versions of the playlist) to reconstruct a follower timeline. Flag any period where growth appears statistically improbable for an independent curator playlist of this genre and size. Context: [SCANNER NAME] has rated this playlist '[SCANNER VERDICT].' I am testing whether that verdict is a false positive caused by a drip-rate bot script."

**What to look for in results:** Any source showing growth variance of less than ±2 followers/day over a 30-day window is a red flag. Real curators have bad weeks.

---

## PROMPT 2 — Listener-to-Follower Gap (The SFA Test)
*Target: Expose stream injection via API or external bot-links, invisible to scanner.*

**Google Deep Research Prompt:**
> "I need to evaluate whether the stream volume associated with the Spotify playlist '[PLAYLIST NAME]' is mathematically consistent with its follower count of [FOLLOWER COUNT]. The playlist is generating approximately [DAILY STREAMS] streams per day according to my Spotify for Artists dashboard. Research the following: (1) What is the industry-standard stream-to-follower ratio for an independent playlist of this genre and follower size? (2) Are there documented cases of playlists with follower counts under 50 generating hundreds of daily streams — and what mechanism (bot injection, API farming, direct-link scripts) explains this discrepancy? (3) Has the promoter or curator associated with [PROMOTER NAME] been discussed on music industry forums (Reddit r/WeAreTheMusicMakers, Indie Music Feedback, Facebook curator groups, SoundPlate, SubmitHub community boards) in connection with inflated streams or bot complaints?"

**What to look for in results:** A playlist with 12 followers generating 400 streams/day has a 33:1 stream-to-follower ratio. Legitimate editorial playlists run 0.5:1 to 2:1. Any ratio above 5:1 warrants escalation to Section 3.

---

## PROMPT 3 — Geographic & Data Center Signature Check
*Target: Identify server-farm traffic that automated scanners categorically miss.*

**Google Deep Research Prompt:**
> "I am auditing streams generated for my track '[YOUR TRACK]' from the Spotify playlist '[PLAYLIST NAME].' My Spotify for Artists Top Cities data shows the following cities as leading sources for this playlist's streams: [TOP CITIES LIST]. Research the following: (1) Which of these cities are known AWS, Google Cloud, or Microsoft Azure data center hubs? (specifically: Ashburn VA, Council Bluffs IA, Dublin IE, Helsinki FI, Frankfurt DE, Singapore, Sydney AU — flag any match). (2) Is there documented evidence that Spotify bot farms route traffic through these data centers to simulate listener IPs? (3) Does [SCANNER NAME] specifically address data-center IP filtering in its detection methodology? If not, what does this methodological gap mean for the reliability of a '[SCANNER VERDICT]' verdict on this playlist?"

**What to look for in results:** Ashburn, VA (AWS us-east-1) appearing as a Top City for a playlist that claims to serve, say, "chill R&B fans in Chicago" is a near-definitive bot signal. The scanner seeing "Clean" under these conditions means the scanner is not checking geographic signatures.

---

## PROMPT 4 — Genre Entropy & Skip-Rate Inference
*Target: Detect "metadata poisoning" — playlists assembled to fool categorization, not serve listeners.*

**Google Deep Research Prompt:**
> "Conduct a genre coherence audit of the Spotify playlist '[PLAYLIST NAME / URL].' I need to determine whether the playlist has been assembled to serve real listeners of a specific genre or to aggregate tracks for stream farming. Research the following: (1) Retrieve or reconstruct the track listing and assess what percentage of tracks fall within the same genre/subgenre as my track '[YOUR TRACK]' (genre: [YOUR GENRE]). (2) Is there documented evidence that playlists curated by or associated with [PROMOTER NAME] show genre incoherence — mixing incompatible subgenres in a single playlist? (3) What does music industry research or journalism say about the relationship between genre mismatch, high skip rates, and algorithmic penalties from Spotify? (4) Has [SCANNER NAME] published any methodology for penalizing playlists based on genre entropy or coherence scoring?"

**What to look for in results:** A Soul track on an "Asian Acid Jazz" playlist is not curation — it is slot-filling. If 40%+ of a playlist's tracks are genre-mismatched, real human listeners will skip. High skips + "Clean" scanner verdict = the scanner is blind to this evasion layer.

---

## PROMPT 5 — Kill Switch / Post-Cancellation Decay Test
*Target: Distinguish organic listener decay from programmatic stream termination.*

**Google Deep Research Prompt:**
> "I need to determine whether streams from the Spotify playlist '[PLAYLIST NAME]' represent real listener behavior or a rented bot script. My subscription to [PROMOTER NAME] was canceled on [CANCELLATION DATE]. Research the following: (1) What does organic stream decay look like after a track is removed from or deprioritized on a legitimate playlist — how many days does it typically take for streams to taper to baseline? (2) What does programmatic decay look like — is a vertical drop to zero streams within 24–48 hours of subscription cancellation consistent with documented bot-farm behavior? (3) Are there Reddit threads, music distributor warnings, or journalism from Hypebot, Music Business Worldwide, The Trichordist, or Water & Music that document this 'cliff-edge drop' as a diagnostic signature of pay-to-play bot services? (4) Does [SCANNER NAME]'s historical stream estimate for '[PLAYLIST NAME]' show a vertical cliff-edge at or near [CANCELLATION DATE]?"

**What to look for in results:** Organic decay takes 14–28 days as real listeners gradually stop encountering the track. A drop to zero within 24 hours of cancellation is a binary signature of a scripted stream service, not a human audience.

---

## SYNTHESIS PROMPT — Filing the Full Verdict

After running Prompts 1–5, use this to compile findings:

**Google Deep Research Prompt:**
> "Synthesize the following five data points about the Spotify playlist '[PLAYLIST NAME]' and its associated promoter '[PROMOTER NAME]': (1) Growth pattern analysis: [paste key finding from Prompt 1]. (2) Stream-to-follower ratio: [paste key finding from Prompt 2]. (3) Geographic signatures: [paste key finding from Prompt 3]. (4) Genre coherence score: [paste key finding from Prompt 4]. (5) Post-cancellation decay pattern: [paste key finding from Prompt 5]. Based on these findings, assess: (A) Is the '[SCANNER VERDICT]' from [SCANNER NAME] a false positive? (B) What is the estimated probability that streams from this playlist were artificially generated? (C) What specific actions should I take — contacting my distributor, filing a report with Spotify, or documenting for potential legal action against [PROMOTER NAME]?"

---

## METHODOLOGICAL NOTE

Automated scanners are a **first-line filter**, not a final verdict. Networks that have been operating for more than 12 months have reverse-engineered the detection thresholds of tools like artist.tools, Chartmetric's anomaly flags, and SubmitHub's trust scores. They calibrate their drip rates, geographic routing, and genre slot-filling to stay 1–2% below each tool's alert threshold.

The five prompts above bypass scanner logic entirely by examining:
- **Statistical improbability** (Prompts 1 & 2)
- **Infrastructure signatures** (Prompt 3)
- **Behavioral incoherence** (Prompt 4)
- **Temporal forensics** (Prompt 5)

None of these methods require access to Spotify's internal data. They require cross-referencing your own SFA private data against public research — which is exactly what an automated scanner cannot do.
