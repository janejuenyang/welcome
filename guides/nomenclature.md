# Nomenclature

Naming things is an art. While it may be quicker to choose the first thing that comes to mind, I've found it is worthwhile to be more thoughtful. Here's how I approach naming things:

## Code: consistency is queen

Prioritize readability and comprehension.

* Use letter prefixes to indicate the type of data structure. For instance:
  * `d_` for dataframes of disaggregated data
  * `s_` for dataframes of summarized data
  * `g_` for graphs
  * `m_` for models
  * `p_` for parameters

* Choose suffixes to show relation between / group things. For instance:
  * {`d_foo_raw`, `d_foo`}: `d_foo_raw` is the raw dataset that, post cleaning, becomes `d_foo`
  * {`d_foo`, `s_foo_year`}: `s_foo_year` is an aggregate of the data in `d_foo` by year

* Use verbs to name functions and be straightforward about what the function does. For instance:
  * `calculate_percentiles`
  * `load_acs_data`

* For multi-script projects, use numeric prefixes to name code files by the order they should be run. For instance:
  *  `1_prep_data`
  *  `2_geocode`
  *  `3_split`
  *  `4_train_model`
  *  `5_test_model`

## Systems / Products: make it memorable

If you're naming a new system or product, you have an opportunity to anchor how people think -- even *feel* -- about it. Take advantage of that, especially if you are driving data culture change. Some strategies I use:

* **Alliteration**: find something that rolls off the tongue and isn't a tongue-twister
* **Acronyms**: you want an acronym that is pronounceable and ideally elicits a sense of vision and/or fun
* **Crowdsource**: let the people who will be using the system / product nominate names and do a vote to select the winner
* **Celebrate**: throw a party to celebrate the initial launch and subsequent feature releases. I've previously held a "baby shower" for a system, which set things up to recognize each version as the system "growing up".

## Teams: use plain language

While system and products names can benefit from being cutesy, I think it's best to be straightforward when naming teams. 

* From a customer service perspective, you want people to know what you do simply from the name of your team. Ask some trusted folks if you aren't sure a name idea makes sense.
* Be as short as possible. Lots of "ands" in a team name suggests you need to find a pithier way to describe your team's core function.
* Consider the acronym. If you do have a long team name, know that it will typically be referred to by acronym. Avoid confusing acronyms that suggest a different function than your team's actual scope. For instance, "Office of Instruction & Training" could acronym to IT... which is an entirely different thing.

## Everything else: make sure it's worth naming

Remembering names takes mental overhead. Not everything should be named. If you are thinking of naming something, first ask yourself what benefit you / your team / your customers get from the name.

