class: center, middle, inverse

# xonsh

A Python-powered, bashwards-learning shell

![](/ascii_conch_part_transparent_tight.png)
---
layout: false
# Getting to know [me]
.left-column[
  ## Who
]
.right-column[
Gil Forsyth, I work for a company*

![](/GitHub-Mark-32px.png) gforsyth

Contributing and maintaining `xonsh` since 2015

.footnote[.red[*] It's a good company, but unrelated to this talk and I'm here as my personal self]

]
---
# Getting to know [us]
.left-column[
  ## Who
]
.right-column[

100 contributors, about 10k commits, over 6 years

Created by the inimitable Anthony Scopatz

also: @adqm, @melund, @AstraLuma, @mitnk, @laloch, @anki-code, @jnoortheen, @blahgeek, @daniel-shimon and more!

Current active maintainers: @daniel-shimon, @gforsyth

How many users do we have?

Very hard to measure.  We average around 12-13k downloads a month on PyPI.
(but also, conda-forge, CI, shell update frequency, so who knows?)

]
---
# Getting to know [you]
.left-column[
  ## Who
]
.right-column[
.big[Show of hands]
]
--
.right-column[
Who here uses `bash`?
]
--
.right-column[
Who here uses `zsh`?
]
--
.right-column[
Who here uses something else?
]
--
.right-column[
Huh?  What are you talking about?
]

---
# Getting to know [not you]
.left-column[
  ## Who
]
.right-column[
Love writing bash?
]
--
.right-column[
Have 10,000 lines of lovingly hand-crafted RC files?
]
--
.right-column[
Absolutely require _strict_ POSIX compatibility?
]
--
.right-column[
Hate Python?
]
---
# Getting to know [you]
.left-column[
  ## Who
]
.right-column[
[Avoid|shy away from] writing bash?
]
--
.right-column[
Have 10,000 lines of RC files you grabbed from SO or `oh-my-zsh` but are unsure about how to edit them?
]
--
.right-column[
Love Python?
]
--
.right-column[
Have wanted to write custom tab completion but `*yikes*`
]
---
# A brief history

.left-column[
  ## Who
  ## What
]
.right-column[
.big[Where it all started]

---

```
commit 5757edb15e7c4e440d3320a821c5f90564c93eac
Author: Anthony Scopatz <scopatz@gmail.com>
Date:   Wed Jan 21 17:04:13 2015 -0500

    everything is a mess
```
.footnote[.red[*] Things are much better now!]
]
---
# But what is it?

.left-column[
  ## Who
  ## What
]
.right-column[

I'm so glad you asked.

Am I done making slides?
]
---
# A brief history

.left-column[
  ## Who
  ## What
  ## Why
]
.right-column[
]
---
# A brief history

.left-column[
  ## Who
  ## What
  ## Why
  ## How
]
.right-column[
]
---
# Exeunt

## Installation

```bash
conda install -c conda-forge xonsh

python -m pip install "xonsh[full]"

apt install xonsh

pacman -S xonsh

dnf install xonsh

brew install xonsh
```

Or come say hi at 

https://github.com/xonsh/xonsh/

https://xon.sh
