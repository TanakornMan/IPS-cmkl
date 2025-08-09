# Paper Analysis: Deviations from Main Contributions

## Main Contributions (from Introduction)
The paper claims four main contributions:
1. **Feature filtering effects on model complexity**
2. **Grid size vs precision trade-offs**
3. **Introduction of AGT and ADT metrics**
4. **IPS design insights for practical improvements**

**ACTION**:
Let's shuffle the order of main contributions a bit since this sets the expectation of which is significant, let's go with this order instead
1. **Introduction of AGT and ADT metrics**
2. **Grid size vs precision trade-offs**
3. **IPS design insights for practical improvements**
4. **Feature filtering effects on model complexity**


## Areas That Deviate from Main Contributions

### 1. Section 3.1: Over-detailed Implementation Discussion
**Issue**: The section spends excessive space on implementation minutiae that don't contribute to the core research.

**Problematic Content**:
- Detailed discussion of RSSI data collection methodology initially capturing "all detectable access points within network configuration"
- Lengthy explanation about neighboring buildings' access points being included
- Discussion of "zero-inflated spatial data" effects
- Multiple paragraphs about grid alignment across floors

**Why it's problematic**: These are implementation details that distract from the main research questions about feature filtering and grid size optimization.

**Recommendation**: Move to appendix or significantly condense.

**ACTION**: the rest can stay I just need a more concise explanation on grid aligment across floors

### 2. Section 3.2: Excessive Interpolation Method Details
**Issue**: Too much space devoted to explaining RSSI interpolation mechanics.

**Problematic Content** (Line 139):
```
By collecting 5 datapoints in a grid (top left, top right, bottom left, bottom right and centre), 
these RSSI values can be interpolated into a combined grid by averaging the values from the individual grids.
```

**Why it's problematic**: This is a standard interpolation technique that doesn't need detailed explanation in a research paper focused on higher-level contributions.

**Recommendation**: Reduce to one sentence: "RSSI values were interpolated from 5 collection points per grid using standard averaging techniques."

**ACTION**: Reduction to one sentence is fine!

### 3. Literature Review: Generic IPS Overview
**Issue**: The literature review spends too much time on general IPS background rather than focusing on the specific research gaps this paper addresses.

**Problematic Content**:
- Extended discussion of GPS limitations indoors
- General overview of trilateration and BLE devices
- Basic ML algorithm enumeration without connection to the paper's specific contributions

**Why it's problematic**: Doesn't directly support the paper's novel contributions about feature filtering and grid size optimization.

**Recommendation**: Focus more on existing work specifically related to feature selection in IPS and grid size optimization studies.

**ACTION**: GPS limitations indoors has to be reduced to a few sentences while maintaining its citation. trilateration I feel is a repetition to the intro so if they use the same citation I say why keep it. Main connection of the ml algorithm is how accessible and simple the architecture is, we can make this the point of connection.

### 4. Result Section: Missing Direct Connection to Contributions
**Issue**: The results don't clearly map back to the stated contributions.

**Gaps**:
- Feature filtering effects (Contribution #1) are shown but not thoroughly analyzed in relation to model complexity
- Grid size trade-offs (Contribution #2) are demonstrated but practical design insights (Contribution #4) are underdeveloped
- AGT/ADT metrics (Contribution #3) are introduced but their advantages over existing metrics aren't clearly established

**ACTION**: In term of complexity I was intending to reflect it on actual compute time that's why there's the hardware thing later on. FOr practical insights on grid size trade-off I believe you can expand more based on agt and adt tradeoff itself. I agree that agt and adt introduction is very random and isn't clearly established, anything we can do to highlight them more is appreciated, and yes without going off the rail on current definition.

### 5. Discussion Section: Computational Hardware Focus
**Issue**: Disproportionate focus on hardware limitations rather than research insights.

**Problematic Content**:
- Extended discussion about RTX 3080 Ti struggling with unfiltered datasets
- Hardware-specific observations that don't generalize

**Why it's problematic**: This is more of an implementation note than a research contribution.

**Recommendation**: Move hardware discussion to appendix; focus on generalizable insights about feature dimensionality.

**ACTION**: please extract only what we need for the previous context, the rest can go straight to appendix I agree.

## Contradictions and Flow Issues

### 1. Metric Introduction Timing
**Issue**: AGT and ADT are introduced in Section 3.2 but not properly motivated until results.

**Fix**: Introduce metrics earlier with clear motivation for why existing metrics are insufficient.

**ACTION**: It's not that existing metric is insufficient but rather getting global coordiate indoor without professional equipment is almost impossible, not only that but even with professional equipment it required extensive cooperation with the entire floor to modify points where satellite connection can be recieved which defeats the point of making this simple and accessible.

### 2. Feature Filtering Justification
**Issue**: The paper presents feature filtering as both a research contribution and a necessity due to hardware limitations.

**Contradiction**: Is this a methodological contribution or a practical workaround?

**Fix**: Clarify whether feature filtering is being studied as a research question or used as a practical solution.

**ACTION**: it's a contribution since previous work relies on blindly collecting all rssi, this one @misc{LRE1,
  author    = {Intachuen, B. and Charoenphon, M. and Mankhetwit, T.},
  title     = {Classification-based IPS},
  year      = {2024},
  note      = {Available at: \url{https://github.com/RinRin-32/Classification-based-IPS}}
} they fully rely on collecting all rssi available and we wanted to continue on exploring whether we can achieve similar results without brute forcing it so much,

### 3. Grid Size Optimization Claims
**Issue**: The paper claims to find "optimal" grid sizes but only tests specific environment.

**Contradiction**: Results may not generalize, but conclusions are stated broadly.

**Fix**: Qualify conclusions to specific experimental environment or provide broader validation.

**ACTION**: yeah we don't mean to generalize, please make it clear on this,

## Recommendations for Appendix Migration

### High Priority (Move to Appendix)
1. **Detailed RSSI collection methodology** (Section 3.1)
2. **Grid interpolation technical details** (Section 3.2)
3. **Hardware performance discussion** (Discussion section)
4. **Edge grid effects analysis** (Already moved)

### Medium Priority (Significantly Condense)
1. **Generic IPS background** (Literature Review)
2. **Basic ML algorithm overview** (Literature Review)
3. **Detailed experimental setup** (Method section)

### Low Priority (Minor Edits)
1. **Results presentation** - better connection to contributions
2. **Conclusion** - more specific to actual findings vs claims

## Summary
The paper would benefit from:
1. **Tighter focus** on the four stated contributions
2. **Moving implementation details** to appendix
3. **Strengthening the connection** between results and claimed contributions  
4. **Clearer positioning** of what's novel vs what's implementation necessity
5. **More rigorous evaluation** of when findings generalize beyond the specific experimental setup

The core research on feature filtering effects and grid size optimization is valuable, but it's currently obscured by excessive implementation details and generic background material.