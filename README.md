<p align="center">
  <a href="https://gomezabajo.github.io/Wodel/wodel-edu.html">
    <img src="https://gomezabajo.github.io/Wodel/images/wodelEdu.png" width="120" height="140" alt="Wodel-Edu logo" />
  </a>
</p>

<h1 align="center">Wodel-Edu</h1>

<p align="center"><em>An MDE solution for the automated generation and evaluation of exercises</em></p>

<p align="center">
  <a href="https://gomezabajo.github.io/Wodel/wodel-edu.html"><img src="https://img.shields.io/badge/Website-Wodel--Edu-blue" alt="Website" /></a>
  <a href="https://github.com/gomezabajo/Wodel/wiki/2.-Get-Started-with-Wodel-Edu"><img src="https://img.shields.io/badge/Docs-Get%20Started-green" alt="Get Started" /></a>
  <a href="https://www.eclipse.org/legal/epl-2.0/"><img src="https://img.shields.io/badge/license-EPL%202.0-orange" alt="EPL-2.0 license" /></a>
</p>

**Wodel-Edu** is an extension to [Wodel](https://github.com/gomezabajo/Wodel) — a domain-specific language for model mutation — for the automated generation and evaluation of exercises. Starting from a seed model, Wodel-Edu applies mutations to synthesize exercises, renders them as diagrams or text, and generates a complete web or [Moodle](https://moodle.org/) application ready for students to use.

> **Note:** This repository hosts the Wodel-Edu **website**, which redirects to the [main Wodel-Edu page](https://gomezabajo.github.io/Wodel/wodel-edu.html). The Wodel-Edu **source code** lives in the [Wodel repository](https://github.com/gomezabajo/Wodel).

## Exercise types

Wodel-Edu generates seven kinds of exercises:

| Exercise type | The student has to... |
| --- | --- |
| Alternative response | tell whether the diagram or the textual representation is correct |
| Multiple diagram choice | tell which of the shown diagrams is correct |
| Multiple text choice | tell which of the shown textual representations is correct |
| Multiple emendation choice | tell which text options fix the shown diagram |
| Match pairs choice | match each statement on the left with the correct option in a drop-down list |
| Missing words choice | complete the gaps in a text with the correct options in drop-down lists |
| Text drag and drop | complete the gaps in a text by dragging labels from categorized sets |

## The DSLs

Wodel-Edu provides four domain-specific languages that work together with [Wodel](https://gomezabajo.github.io/Wodel):

### eduTest

Configures the questionnaire and defines the exercises:

```
navigation=free
MultiChoiceDiagram simple {
    retry=no
    description for 'exercise4.model' = 'Select which of these automata
                                         accepts only "a*bab*"'
}
MultiChoiceEmendation complex {
    retry=no, weighted=no, penalty=0.0,
    order=options-descending, mode=checkbox
    description for 'exercise5.model' = 'Select the required changes so that
                                         the automaton accepts only "a+b+"'
}
MatchPairs rfs1, mts2, rfs2 {
    retry=no
    description for 'exercise6.model' = 'Select which of these options modifies
                                         the above automaton to accept only
                                         the language defined by ' %text('reg-exp')
}
MissingWords mtsrfs1 {
    retry=no
    description for 'exercise7.model' = 'Complete the following text with the
                                         options for each gap that modify this automaton
                                         to accept only the language defined by "ab(ba)*"'
}
```

### modelDraw

Configures the graphical visualization of models, rendered with [Graphviz](https://www.graphviz.org/) or [Circuit Macros](https://ece.uwaterloo.ca/~aplevich/Circuit_macros/):

```
metamodel "http://dfaAutomaton/1.0"

Automaton: diagram {
    State(isInitial): markednode
    State(not isFinal): node shape=circle
    State(isFinal): node shape=doublecircle
    Transition(src, tar): edge label=symbol.symbol
}
```

### modelText (optional)

Configures the textual identification of model elements:

```
metamodel "http://dfaAutomaton/1.0"

>State: State %name
>State(isFinal): final
>State(isInitial): initial
>Transition: Transition %symbol.symbol
>Transition.tar: target
>Transition.src: source
```

### mutaText (optional)

Configures the text options shown in the multiple emendation choice, match pairs, missing words, and text drag and drop exercises:

```
metamodel "http://dfaAutomaton/1.0"

>TargetReferenceChanged: Change %object from %fromObject
                         to %toObject with new %refName %oldToObject /
                         Change %object from %fromObject to %oldToObject
                         with new %refName %toObject
>AttributeChanged: Change %object to %oldValue /
                   Change %object to %value
```

## Live demos

- **Web application** generated with Wodel-Edu: [www.wodel.eu](http://www.wodel.eu/)
- **Moodle integration** (work in progress): [moodle.wodel.eu](http://moodle.wodel.eu/) (user: `demo`; password: `Wodel-Edu4Moodle`)

### Videos

All demos are also collected on the [Wodel-Edu video page](https://gomezabajo.github.io/Wodel/wodel-edu-video.html).

- [Short video demo of Wodel and Wodel-Edu](https://www.youtube.com/watch?v=pFFDBRddzb8)
- [Automated generation and correction of diagram-based exercises for Moodle with Wodel-Edu](https://www.youtube.com/watch?v=39L6Y6kZ42g)
- Gamified diagram-based exercises for Moodle with Wodel-Edu and [SGAME](https://sgame.etsisi.upm.es/games/25404), with [Daniel López](https://portalcientifico.upm.es/es/ipublic/researcher/306683)

## Getting started

- [Get Started with Wodel-Edu](https://github.com/gomezabajo/Wodel/wiki/2.-Get-Started-with-Wodel-Edu) (wiki)
- [Sample exercises](https://gomezabajo.github.io/Wodel/wodel-edu-samples.html)
- [User evaluation](https://gomezabajo.github.io/Wodel/wodel-edu-eval.html)

### Downloads

- [Eclipse update site](https://gomezabajo.github.io/Wodel/update-site)
- [Standalone Eclipse + Wodel](https://www.dropbox.com/scl/fi/0kt6menthzsb5rz9uelvq/eclipse.zip?rlkey=i22wvj3888juh45y5qx5wle1e&dl=0)
- [Windows 7 x64 VirtualBox VM + Wodel](https://www.dropbox.com/scl/fi/wlpr7e0ab0981kvfthi5n/Windows.7.x64.Wodel.2.0.zip?rlkey=hxlk3y0mh3flqp6763dfsgm20&st=pkor7ex6&dl=0)
- Wodel-Edu samples: [.zip](https://github.com/gomezabajo/Wodel/zipball/WodelEduSamples) · [.tar.gz](https://github.com/gomezabajo/Wodel/tarball/WodelEduSamples)

## About this repository

This repository contains the Jekyll site deployed to GitHub Pages. The workflow in `.github/workflows/jekyll-gh-pages.yml` builds and deploys the site automatically on every push to `main`; it can also be triggered manually from the **Actions** tab ("Deploy Jekyll with GitHub Pages dependencies preinstalled" → "Run workflow").

## Acknowledgements

This work has been funded by the Spanish Ministry of Science (RTI2018-095255-B-I00, project "MASSIVE") and the R&D programme of Madrid (P2018/TCS-4314, project "[FORTE](https://antares.sip.ucm.es/forte-cm/)").

## License

Distributed under the [Eclipse Public License 2.0](LICENSE).

## Contact

Wodel-Edu is maintained by [Pablo Gómez-Abajo](https://github.com/gomezabajo). Send your comments or questions to [pablo.gomeza@uam.es](mailto:pablo.gomeza@uam.es).
