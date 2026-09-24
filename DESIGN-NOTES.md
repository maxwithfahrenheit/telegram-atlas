# Design review and redesign

The previous page gave the headline, statistics, explanatory copy, filters, and cards similar visual weight. Repeated framing and accumulated style overrides made the layout feel less intentional. Pale text weakened the hierarchy, and separate control rows made browsing feel fragmented.

## The new sequence

1. **Understand the offer.** A short headline sits beside an actual question and reply. The example opens its full conversation.
2. **See the scale.** One restrained strip presents the four source-reported corpus figures, with the approved comparison statement underneath.
3. **Inspect the evidence.** A compact browser offers search, language selection, visible topic buttons, and real message previews.
4. **Explore in context.** The conversation reader preserves replies, participants, reactions, native translation controls, and a statistics sidebar. Community context and source details remain available without dominating the opening.

## Visual direction

Warm white, dark readable type, one muted indigo accent, and soft color within conversation previews. Consistent spacing and a single stylesheet replace layered overrides. Mobile stacks the opening, uses a two-column statistics grid, and collapses chat statistics.

## Verification

Checked the landing page and reader at desktop and 390px mobile widths, with no horizontal overflow. Verified opening the featured conversation, reply navigation, participant controls, and the Non-English filter (879 conversations). No browser console errors were reported. Translation service integration is retained; live Google translation still requires local key configuration.
