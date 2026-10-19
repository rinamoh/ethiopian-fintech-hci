# Design Rationale — Ethiopian Fintech HCI Prototype

## Overview

Every design decision in this prototype was made in response to a 
specific constraint imposed by our target user: a low-literacy 
Ethiopian adult accessing capital market information on a mobile 
device for the first time. This document records those decisions 
and their justifications.

---

## Decision 1 — Mobile-first, Android-first

**Decision:** The prototype is designed for a 393×852px mobile 
frame representing a mid-range Android device.

**Rationale:** Ethiopian smartphone penetration is overwhelmingly 
Android-based, driven by affordable Chinese-manufactured handsets 
in the 2,000–5,000 birr range. Desktop and iOS interfaces are 
irrelevant to our target population. Every layout decision — 
touch target sizes (minimum 48px), bottom-anchored primary actions, 
single-column layouts — follows from this constraint.

---

## Decision 2 — Icon-only navigation on the Home screen

**Decision:** The home screen presents three navigation options 
as icons with no visible text labels on first load. Labels appear 
only on tap.

**Rationale:** Research on icon comprehension (McDougall, Curry & 
de Bruijn, 1999) establishes that familiar, concrete icons 
communicate function independently of literacy level when the 
icon-referent relationship is culturally appropriate. Text labels 
add cognitive load for users with low reading fluency without 
adding navigational value. The tap-to-reveal label behavior 
accommodates users who need textual confirmation without 
imposing it on users who don't.

**Risk acknowledged:** Icon comprehension is culturally variable. 
The usability study will test whether our chosen icons (plant for 
portfolio growth, bar chart for market, person for help) transfer 
meaning correctly to Ethiopian users without prior fintech exposure.

---

## Decision 3 — Color and arrow before numbers on Portfolio screen

**Decision:** The Portfolio Overview screen shows only a large 
colored circle (green = up, red = down) and a directional arrow. 
Numbers are hidden behind a secondary tap.

**Rationale:** The most important information for a first-time 
investor is directional: did my investment go up or down? Numerical 
precision is secondary and cognitively demanding. Color communicates 
valence pre-consciously (Hunsicker, 2012), meaning users receive 
the critical signal before processing any text or numbers. 
Progressive disclosure — revealing detail only on demand — reduces 
cognitive load for low-literacy users while preserving full 
information access for users who want it.

**Risk acknowledged:** Green and red carry different cultural 
associations in different contexts. In some Ethiopian cultural 
contexts red signals warning rather than loss specifically. 
The usability study will test whether participants correctly 
interpret color as directional rather than as a general alert.

---

## Decision 4 — Locally meaningful units instead of currency amounts

**Decision:** Financial changes are expressed in locally meaningful 
equivalents (kilograms of coffee, months of school fees) before 
birr amounts.

**Rationale:** Abstract numerical financial values are difficult 
to interpret without financial literacy context. Research on 
financial decision-making in low-income populations (Bock et al., 
2016) consistently shows that concrete real-world equivalents 
improve comprehension and decision quality compared to currency 
figures alone. Ibtasam et al. (2018) specifically document how 
conventional financial interfaces fail low-literacy women in 
Pakistan by assuming numerical fluency. Our locally meaningful 
unit layer is a direct design response to this documented failure.

**Choice of units:** Coffee (ቡና) was selected as the primary 
reference unit because it is a universally understood commodity 
across Ethiopian economic contexts, urban and rural. School fees 
serve as a secondary unit for users with children. Both are 
revised based on usability study findings.

---

## Decision 5 — Voice query interface

**Decision:** A floating microphone button appears on every screen, 
giving users the ability to ask questions in spoken Amharic at 
any point in the app.

**Rationale:** Literacy barriers that impede text-based navigation 
do not impede voice interaction. Vashistha et al. (2015) demonstrated 
that voice interfaces enable meaningful participation in information 
systems for users who are excluded by text-based equivalents. 
Medhi et al. (2011) specifically found that voice modality 
significantly reduced task abandonment for non-literate mobile 
money users compared to text navigation.

**Known limitation:** Amharic speech recognition accuracy in 
commercial APIs (Google Speech-to-Text, Azure Cognitive Services) 
is significantly lower than English accuracy, particularly for 
domain-specific financial terminology. The voice interface in 
this prototype is tested using Wizard of Oz methodology (Kelley, 
1984) — a researcher manually produces responses that simulate 
system behavior — to separate interface design questions from 
speech recognition accuracy questions. The usability study will 
document failure points to inform future technical development.

---

## Decision 6 — Three distinct error states

**Decision:** The prototype handles three error types separately: 
no internet connection, session timeout, and unknown general error. 
Each has a distinct visual treatment and primary action.

**Rationale:** Generic error screens ("Something went wrong") 
leave low-literacy users with no actionable path forward. 
Each error type has a different correct user response: check 
your connection, sign in again, or call support. Conflating 
these into one screen forces users to make a diagnostic decision 
they may not have the technical literacy to make. Separating 
them moves the diagnostic burden from user to system.

**Phone number on general error only:** The support phone number 
appears exclusively on the unknown error screen because it is 
the only state where the user has no self-service recovery path. 
Showing it on all error screens would train users to call support 
for problems they can resolve themselves, creating unnecessary 
support burden.

---

## Decision 7 — No onboarding tutorial

**Decision:** The onboarding screen contains a welcome message 
and a single start button. There is no feature walkthrough or 
tutorial sequence.

**Rationale:** Tutorial sequences assume users will read and 
retain instructional text before using an interface. For 
low-literacy users this assumption fails. Research on onboarding 
design for low-literacy populations (Medhi et al., 2011) 
consistently shows that tutorials are skipped or misunderstood, 
and that learning through direct interaction with a simple 
interface outperforms tutorial-based onboarding. The help screen 
provides a visual reference for users who need it after 
experiencing confusion, rather than front-loading information 
before any confusion has occurred.

---

## Limitations of This Design Process

This prototype was designed without direct input from the target 
user population during the design phase. All design decisions 
reflect the designer's interpretation of existing literature 
and prior experience building financial interfaces for Ethiopian 
users. The usability study is designed to 
surface the ways in which these decisions were wrong, not to 
confirm that they were right. Institutional affiliation and 
ethics review are required before the study can be conducted 
responsibly.

---

## References

- McDougall, S., Curry, M., & de Bruijn, O. (1999). Measuring 
  symbol and icon characteristics.
- Hunsicker, S. (2012). The effect of color on conscious and 
  unconscious cognition.
- Bock, et al. (2016). Framing effects in financial decision making.
- Ibtasam, S., et al. (2018). Knowledge, access, and 
  decision-making: Women's financial inclusion in Pakistan. COMPASS.
- Vashistha, A., et al. (2015). Sangeet Swara. CHI.
- Medhi, I., et al. (2011). A comparison of mobile money-transfer 
  UIs for non-literate and semi-literate users. CHI.
- Kelley, J. F. (1984). An iterative design methodology for 
  user-friendly natural language office information applications.
- Linxen, S., et al. (2021). How WEIRD is CHI? CHI.