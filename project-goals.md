# Project Goals

## List of goals proposed at some point

No specific organization, mostly copy and paste from weekly project status. We will have to see how things get pushed back as the development complexity increases. It will be tremendous.

* **0.02:** 
  * Real data model using graph DB as backend? Continue to use text file? Will need to evaluate. Pros and cons to each side. 
  * Probably Strava too
* **0.03:** Probably some kind of user authentication... might even need to come earlier. 
* **0.04:** Start doing NLP server side. Basically want to do Named Entity Recognition. Give feedback on it on the desktop UI \(and maybe even mobile\). Such that it can be easily corrected as well \(like it doesn't pick up a clearly named entity, I can highlight it and tell it that its an entitiy\)
  * **0.10:** Will also want to be able to recognize other things than entities. Also actions/implied actions. For example last night I wrote "Goodnight" =&gt; I'm going to sleep. This morning I wrote "woke" =&gt; awake.
* **0.06:** Health data scraping, HR
* **0.08:** iMessage scraping. This will mostly be about scheduling events from my messages I think. Or knowing what events are happening without explicitly entering them
* **0.11:** Put this tracker in the app
* **0.14:** Really start building the stream, mostly for desktop to replace Twitter and this wiki. This might come later than I expect due to the prereqs. Basically need the data model by this point. UI for mobile and desktop \(+iPad later ~**0.32** post WWDC, I want the rumored handwriting recognition built in\)
* **0.15:** More thinking about how 'apps' should interact with the backend system. Specifically after writing more Swift code. There are so many times I wish I could just pull some state from another system but I can't. Would like to know and interact with that state. But some state needs protection as well. Like it can be a blocking state in some sense. Only certain kinds of events can remove that blocking. Will have to see. Will need to protect from malicious intent, but also its all my code for now. Other code can be hooked in but only explicitly.
  * **0.15-:** As prereq to **0.15** should integrate [https://github.com/thesephist/mira](https://github.com/thesephist/mira) 
  * **0.32:** Some kind of package manager for my own sanity? This will mostly go on the server side, but could even be triggered from Application side. Will have to have the prior thinking done above.
  * **0.20:** Want to be able to have a solid picture of the model between other apps, or if its all just this one?
* **0.13:** podcast commenting system, maybe soundcloud like with annotations as well.. ala [https://twitter.com/adam\_keesling/status/1243647609874481152](https://twitter.com/adam_keesling/status/1243647609874481152)
* **0.10:** Establish some data model. I will be interacting with entities that are public, so I need to be able to link that data. Semantic web kind of concept. This can use WikiData or ConceptNet or similar. May be needed in NLP \(**0.04?** this is seeming a bit early now\)
  * Some kind of multi-tier system. Private, circles, and public? Can also be anon, but ideally these things. Anon is completely separate entity. Ideally something not comfortable saying, but is something vulnerable? This has so many problems tho given how people use anon interactions today. Maybe only real users can comment on an anon message? Anon to be implemented around **1.00+**
  * Might have to begin to write my own graph db, or at least begin to conceptualize about it. **Graph DB is a straight up research project.** It's like the fabric of everything
* **0.07** Alarm integration 
* **0.05** Audio/video input integration + transcription \(**~0.08?**\)
  * Want to be able to publish/live stream these things. **0.13**
* **0.04** Custom input toolbar, ability to also send a tweet when the note hits \(better to do this locally\)
* **0.04** Public vs Private notes
* **0.03** Think about parsing vs db + think about message queue too \(pub sub\)
* **0.03** Provide feedback based on state \(specifically around if it hit the server and if it hit the web\)
* **0.03** Think about app interaction with the backend. Unified backend
  * Thinking that even a text file is potentially enough as long as theres some kind of definite language to parse it. Basically add things, and things can refer back to other things, but doing this efficiently may be hard. Need some notion of 'pointers'

