---
title: Add UML & Other Diagrams To Markdown With PlantUML
description: PlantUML enables you to create diagrams using text descriptions.
images: 
date: 2023-10-11T10:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: 
tags: [Markdown, PlantUML, Diagrams]
categories: [Documentation]
series: [Markdown]
---

PlantUML provides an extensive markup language to describe diagrams. The resulting diagrams can be exported to many formats, including graphics files such as .png, .svg and document formats such as .pdf and .html.

<!--more-->

[PlantUML](https://plantuml.com/) can be used to define a [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language) diagram in text.  As well as UML, several other diagram types are supported. For example, [Gantt Charts](https://plantuml.com/gantt-diagram) visualisations of [JSON data sets](https://plantuml.com/json).


## Including PlantUML Diagrams in Markdown

The [CommonMark](https://commonmark.org/) specification of Markdown does not include PlantUML within it's scope.  So PlantUML is an extension to the standard.  This means that you are likely to have to install add-on extensions to your Markdown tools.

If your are using VSCode to edit and create Markdown documents, extension [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf) is a great place to start. This extension converts Markdown files to .pdf and .html formats and supports embedded PlantUML, as well as Mermaid and LaTeX.

To add a diagram to a Markdown document, simply wrap the PlantUML code to begin with ```@startuml``` and end with ```@enduml```, like this:

```Text
@startuml
  some PlantUML code here
@enduml
```

## PlantUML Diagrams: Going Beyond Markdown

You can use PlantUML to create complex diagrams as part of a larger documentation project.

Use VSCode to create and edit stand-alone, native PlantUML files (.wsd, .pu, .puml, .plantuml, .iuml).

VSCode extension [PlantUML](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) provides a live preview of PlantUML diagrams, short-cut <kbd>Alt</kbd> + <kbd>D</kbd>.  The extension can also convert native PlantUML files (.wsd, .pu, .puml, .plantuml, .iuml) to a wide variety of formats (but not Markdown files with embedded PlantUML).

## Themes

The look and style of diagrams is flexible.  You have control over how diagrams are rendered.  Each element in a diagram can have its own colour, specified in the PlantUML script. Also, an overall theme can be applied to a diagram.

Selecting a [prebuilt theme](https://github.com/plantuml/plantuml/tree/master/themes) or making your own.

There is a [gallery](https://bschwarz.github.io/puml-themes/gallery.html) of prebuilt themes.

## Example: Class Diagram

Here's a classic Class Diagram, illustrating inheritance. In this example, a theme called "crt-amber" has been used, resulting in a dark background with amber coloured lines and text. This is under your control, there are many themes to choose from or you can specify your own colours.

![a Class Diagram showing a parent Class called Pet, with three further Classes that inherit from Pet](/images/example_class_diagram.svg "Class diagram generated by PlantUML")

The above class diagram was generated by this PlantUML code:

```Text
@startuml example_class_diagram

' this is a comment line

' set the theme
!theme crt-amber

' hide PlantUML "circle", to use classic UML Class notation
hide circle

' show class attributes visibility as -,+,#,~ rather than icons
skinparam classAttributeIconSize 0


' define class Pet and bold the name, using **
class Pet as "**Pet**" {
  -name: String
  -weight: int
  -canFly: boolean
  +getName()
  +setName()
  +eat()
}

class Cat as "**Cat**" {
  -scratches: boolean
  +getScratches()
  +setScratches()
}

class Dog as "**Dog**" {
  -catChaser: boolean
  +isCatChaser()
}

class Goldfish as "**Goldfish**" {
  -color: String
  +getColor()
  +setColor()
}

' represent inheritance relationships
Pet <|-- Cat
Pet <|-- Dog
' or like this
class Goldfish extends Pet

@enduml
```
 
## Example: MindMap

Moving beyond UML diagrams, PlantUML supports a variety of other frequently used digram types.  This is an example of a MindMap.  Here a different theme has been used, this one is called "mimeeograph", giving a light background with mauve coloured lines and text.  A different theme could have been used, such as "crt-amber" as used above, or any theme frome [those available](https://github.com/plantuml/plantuml/tree/master/themes).

![a mindmap diagram showing "Summer Learning" at the centre and several branches and sub branches of things to learn](/images/example_mindmap.svg "MindMap generated by PlantUML")

Here's the PlantUML that generated this mindmap:

```Text
@startmindmap example_mindmap
' set the theme
!theme mimeograph

* Summer Learning
  ** Markdown
    *** CommonMark
    *** KaTeX
    *** Mermaid
    *** PlantUML
  ** Hugo Framework
    *** CI/CD
    *** GitHub Tasks
    *** Azure Static Sites

left side

** Rust
** HTML5
** CSS
** JavaScript
  *** Node
  *** Electron
** Angular
** React

@endmindmap
```

## Example: Gantt Chart

This Gantt chart does not have a theme specified, so uses the default colours from PlantUML.

![a gantt chart showing three tasks and a milestone](/images/example_gantt_chart.svg "Gantt chart generated by PlantUML")

Here's the PlantUML that generated this Gantt chart:

```Text
@startuml example_gantt_chart
' set the theme

hide footbox
saturday are closed
sunday are closed
project starts on 1 october 2021
printscale daily zoom 2

title New Idea Development

[workshop ideas] as [task01] lasts 3 days
[feasibility testing] as [task02] lasts 2 days
[review for approval] as [task03] lasts 5 days
[task01]->[task02]
[task02]->[task03]
-- finance --
[estimate costs] as [task10] lasts 1 days
[task01]->[task10]
[task10]->[task03]
-- mission, vision & values --
[assess corporate compliance] as [task20] lasts 4 days and ends at [task03]'s start


[approved] happens at [task03]'s end

@enduml
```

## Other PlantUML Resources

- [Online Server](http://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)
- [Themes Gallery](https://bschwarz.github.io/puml-themes/gallery.html)
- [Official Docker Image](https://hub.docker.com/r/plantuml/plantuml-server)
- [Several Pandoc Filters](https://www.google.com/search?q=pandoc+plantuml+filter&sxsrf=ALeKk01rF9BLhe73T-jGYnYHK16Lc5Emlw%3A1628441844196&ei=9AwQYfO_C9e4lwTc3qXYDw&oq=pandoc+plantuml+filter&gs_lcp=Cgdnd3Mtd2l6EAMyBggAEBYQHjIGCAAQFhAeOgcIIxCwAxAnOgcIABBHELADOgUIABCABDoICAAQCBANEB5KBAhBGABQok1Y31lgzmNoAXACeACAAVWIAacEkgEBOJgBAKABAcgBCcABAQ&sclient=gws-wiz&ved=0ahUKEwjziaTN8qHyAhVX3IUKHVxvCfsQ4dUDCA8&uact=5)