
# TakeMeter — planning.md

---

## 1. Community

* **Chosen Community:** The community i will be doing is `r/cars` on reddit. 
* **Why it's a good fit:** This community is a good fit because it has takes that fit certain label ranging from subject tive takes to factual takes. and for each of this take we can attribute them to them to a definate label

---

## 2. Labels & Taxonomy

### Label 1: technical_analysis

* **Definition:** The post evaluates a vehicle or automotive trend using specific, verifiable data, engineering principles, performance metrics, or mechanical breakdowns.
* **Example 1:** So the N54/N55 were open deck blocks... The new B58 is a closed deck design (block is stronger) with a forged crank and forged rods like the N54... It has a belt driven pump with an electronically control valve to control coolant flow instead of an electric water pump.
* **Example 2:** On the thermal management point, I think the layout of an I6 is one reason BMW was able to make the B58 closed deck. Closed deck blocks definitely have more issues with thermal management than open deck designs.

### Label 2: testimonial

* **Definition:** A personal reflection or first-hand ownership account of a car based entirely on the user's individual experience, daily driving habits, or subjective comfort.
* **Example 1:** I love my I6 with the DCT. Sometimes I could be tricked into thinking I have a CVT because the engine is so smooth, it pulls consistently through the powerband and the transmission shifts so fast.
* **Example 2:** An example from personal experience would be a buddy of mine who recently got a 2008ish 535i for $12.5k... Machinery breaks. Out of warranty machinery is costly to maintain and more expensive to repair.

### Label 3: hot_take

* **Definition:** A bold, controversial, or highly opinionated automotive claim stated as a fact without providing concrete evidence, data, or mechanical justification.
* **Example 1:** 99% of people who drive manual do it because they think it makes them look cool/better than other drivers. Modern autos are faster, more efficient, and don't require you to stomp on a pedal 1000 times in traffic.
* **Example 2:** It seems like the aim is to turn cars into soulless appliances that people give zero s*** about and that they will never even care to own. The current future 'vision' of electric cars is 100% autonomous, generic boxes

### Label 4: speculative

* **Definition:** Discussions, rumors, or emotional anticipation regarding unreleased vehicles, future concept cars, or industry predictions that cannot yet be proven or tested.
* **Example 1:** Seems like the BMW B58 has quite the potential in it - the fact it has a closed deck short block is a sign that BMW (and possibly Toyota) had planned for some higher boost variants down the road... Would it actually get to 1000hp without some major redesign and overhauling is the exciting part of this project.
* **Example 2:** If the next-gen Miata goes fully electric, it's dead in the water. The battery tech just isn't there to keep the weight under 2,500 lbs. I predict Mazda holds out with a micro-hybrid setup for at least another five years.

---

## 3. Hard Edge Cases

* **The Overlap Scenario:** A user posts an incredibly aggressive or bold opinion, but throws in a single statistic or a mention of their personal car to make it look credible.
* **Explicit Decision Rule:** If the core intent of the post is to state a sweeping, emotional opinion ("All modern cars are trash") and a stat or personal car is just used as a decorative, defensive token, it is a hot_take. If the post focuses on breaking down the why using gross available data, specifications, or balanced multi-point observations, it is under technical_analysis or anecdotal_review.

---

## 4. Data Collection Plan

* **Source Location:** the subreddit [r/cars](https://www.reddit.com/r/cars/) 
* **Target Distribution:** my target distribution is a **50-50-50** split for the labels.
* **Imbalance Strategy:** if the label is underrepresented/imbalaced, i will add more data fo that specific label.

---

## 5. Evaluation Metrics

* **Selected Metrics:** confusion metrix and classification report
* **Reasoning:** Using an sklearn confusion matrix alongside a classification report is highly effective because it pairs an intuitive visual diagnostic with precise statistical metrics. the confusion matrix immediately exposes the exact direction of the model's mistakes and the classification report provides the mathematical proof via per-label precision, recall, and F1-scores.

---

## 6. Definition of Success

* **Overall Accuracy:** A minimum of **70% overall accuracy** on the test set. Because a random guesser on a 4-class problem yields 25%, achieving 70% proves the model is catching structural features rather than making baseline guesses.
* **Per-class F1-Score:** At least **0.65 F1-score for every individual class**, with a specific emphasis on `technical_analysis` and `hot_take`. 
* **Justification:** For a community moderation or filtering tool, the classifier needs to be reliable enough that users can confidently filter out noisy `hot_take` rants while highlighting deep `technical_analysis` threads without losing 30%+ of the relevant data to false positives or false negatives.
---

## 7. AI Tool Plan

* **Label Stress-Testing:**
* *Plan:* 
1. **Post:** *"Everyone losing their minds over the new engine clearly doesn’t understand basic thermodynamics. It runs a 12.5:1 compression ratio on a tiny single scroll turbo. I don't care what the marketing team says, that thermal load is an absolute ticking time bomb. Any enthusiast buying this is an idiot who enjoys cracked ring lands at 40k miles."* 
**Final Label:** `hot_take`

2. **Post:** *"Looking at the packaging of the current chassis, if the upcoming 2028 hybrid refresh keeps the same rear subframe geometry, they literally cannot fit a dual-motor setup without changing the multi-link suspension to a trailing arm. Because trailing arms alter the camber curve under compression, the new hybrid variant will inherently have worse cornering stability than the current ICE model."* 
**Final Label:** `speculative`

3. **Post:** *"I’ve driven manual transmission sports cars for 15 years, but I just spent a week tracking my buddy's new PDK Porsche. Anyone who says manuals are 'more engaging' is coping out of their mind. The instant shifts actually let you focus on the physics of the car. Manuals are objectively dead, and purists are just holding back automotive progress because they're scared of change."* 
**Final Label:** `hot_take`

4. **Post:** *"As someone who has put 60,000 daily miles on the current generation, I know exactly where the weak points are. The cabin NVH (noise, vibration, harshness) is awful on the highway. Since the leaked dealer sheets show the next-gen model is keeping the exact same acoustic glass and floor pan insulation, I can guarantee you the new model is going to be just as exhausting to drive on long road trips."* 
**Final Label:** `speculative`

5. **Post:** *"My MK7 GTI threw a cel today for underboost. Hooked up the OBD scanner and logged the wastegate voltage—it was reading 4.2V at idle instead of the factory spec 3.5V, meaning the actuator arm is wearing out. If you own one of these and notice a slight lag around 3k RPM like I did, check your voltage sweeps before replacing the whole turbo."* 
**Final Label:** `technical_analysis`

6. **Post:** *"EV start-ups are a cancer on the industry. Mark my words, by 2030 every single one of these companies except Tesla will file for bankruptcy, leaving buyers with 5,000-pound paperweights. The legacy automakers are just letting them play sandbox right now before they step in and completely wipe them off the map."* 
**Final Label:** `hot_take`

7. **Post:** *"I just traded in my CVT crossover because the rubber-band effect made me want to drive into a wall. CVTs use steel bands on variable pulleys, which inherently limits torque capacity to around 250 lb-ft before slipping. Anyone who buys a CVT car is a mindless commuter who doesn't care about engineering and deserves to have their transmission blow up at 80k."* 
**Final Label:** `hot_take`

8. **Post:** *"Rumor has it that the 2029 Miata will feature a 0.5-liter 2-cylinder engine wrapped in wet cardboard to save weight, because according to internet engineers, anything over 2,000 lbs is basically a commercial semi-truck. I predict it will sell zero units because purists won't be able to fit their massive egos inside."*  
**Final Label:** `hot_take`

* **Annotation Assistance:**
* *Plan:* Yes, i will you an llm to pre label. First i will give it the definations and examples in my planning.md file, then i will ask it to pre-label the posts from [r/cars](https://www.reddit.com/r/cars/). Afterwards, i will cross-check to make sure that no mistakes were made.


* **Failure Analysis:**
* **Failure Analysis:**
    * *Plan:* Once evaluation is complete, I will collect all rows from the test set where the fine-tuned model's prediction did not match the true label. I will feed these mismatched pairs (consisting of the raw Reddit text, the true label, and the model's incorrect prediction) into Groq. 
    * I will instruct the LLM to analyze the errors for systemic linguistic patterns, specifically looking for:
        1. **Sarcasm/Hyperbole:** Is the model interpreting a sarcastic, dramatized post as a literal `technical_analysis` or `speculative` statement rather than a `hot_take`?
        2. **Keyword Blinding:** Is the model misclassifying posts simply because they contain specific heavy automotive keywords (e.g., automatically labeling any post containing "B58 engine" or "turbo" as `technical_analysis`, even if it's an emotional rant)?
        3. **Length Bias:** Is it defaulting short posts to `hot_take` and long posts to `technical_analysis`?
    * *Verification:* I will not blindly trust the LLM's summary; I will manually read through the flagged error clusters to verify if the suggested pattern is statistically prevalent across the test set before adding it to my final README evaluation report.



---

## 8. Hard Annotation Decisions (To be tracked during Milestone 3)

1. **Post:** *"*...*"* $\rightarrow$ **Final Label:** [Label] because...
2. **Post:** *"*...*"* $\rightarrow$ **Final Label:** [Label] because...
3. **Post:** *"*...*"* $\rightarrow$ **Final Label:** [Label] because...