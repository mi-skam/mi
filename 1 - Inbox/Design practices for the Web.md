---
modified: 2024-10-27T14:38:35+01:00
---
[How to Make Your Website Not Ugly: Basic UX for Programmers - Hilary Stohs-Krause - YouTube](https://www.youtube.com/watch?v=Jf0cjocP8Wk)

*Cool fonts, she is using*
for text: Avenir, Helvetic Neue
for headlines: Futura Bold, Gilroy Bold
## WORDS

### make text readable

**60 to 100 characters per line** (`ch` unit in css)

Example for limiting the amounts of character per line:

```css
}
p {
  max-width: 40ch;
  margin-right: 20px;
}
```

- text size >= 16.px
- line height: 1.4
- padding >= 15px

[contrast checker](https://webaim.org/resources/contrastchecker/)
![[Pasted image 20241027134308.png]]
### make text scannable
- highlight key content
- subheads with lowercase and uppercase letters
- bulleted lists
- "first two words" rule (*= we are reading only the first eleven characters of a line*)
![[Design practices for the Web 2024-10-27 13.51.49.excalidraw]]
### keep the decoration to a minimum
- limit number of typefaces (2 or 3) -> often serif for body text, sans-serif for the headers
- limit colors (2 to 3, not counting shades) -> two many are looked at like "ads"
## IMAGES
### icons
- **Icons should always have labels**, meaning of icons are not as timeless as one might think, culture-specific... (in a study only 34% predicted the right meaning if no label was provided)
- work best in navigation / in a menu
- avoid conflicting meaning
### photos and graphics
- "banner blindness" ( we ignore banner contents for historical reasons)
- integrate with content ("part of the content" instead of "next to the content")
- informative and/or relevant 
![[Design practices for the Web 2024-10-27 14.10.17.excalidraw]]

## LOGICAL DESIGN
### patterns
- alternate between small, medium and wide
- consistency beats originality
- find something that works and use it as a model

### progressive disclosure
- "disclose all informations step-by-step, not everything from the get-go" (overwhelming)
- f-shape reading pattern 
  ![[Pasted image 20241027142518.png]]
  - top to bottom = important to less important
  - above the fold (we are lazy people)
  - avoid putting key content in traditional ad areas
### be consistent
- links, buttons
- alert messages
- forms
- tables
- header typefaces / sizes
