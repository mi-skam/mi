---
created: 2024-06-07
tags: output/teaching
dg-publish: true
---
![[qr.png|200]]
## Installation

Wir arbeiten mit dem [Glitch-Editor](https://glitch.com/~aframe-base-template) um [A-Frame](https://aframe.io/docs/1.6.0/introduction/) kennen zu lernen.

## Basics


Minimales Setup um `A-Frame` im Browser nutzen zu können:

>[!box] HTML Grundgerüst
>```html
><!doctype html>
> <html>
>     <head>
>         <title>Grundgerüst</title>
>         <script src="https://aframe.io/releases/1.6.0/aframe.min.js"></script>
>     </head>
> 
>     <body>
>         <a-scene>
>          <!-- Hier gehts los :) -->
>         </a-scene>
>     </body>
> </html>
>```

### Geometrien

Wir erzeugen eine weiße Kiste
> [!box]- a-box
> ```html
> <a-box></a-box>
> ```

Wo ist die Kiste?

Weiße Kisten sind "langweilig", daher ändern wir die Farben. Wir müssen diese in hexadezimaler Notation angeben. 
> [!box]- a-box with a color
> >*Farbe = "#**RRGGBB**". Hier nutzen wir einen [Color picker](https://imagecolorpicker.com/color-code/d94848).*
> ```html
> <a-box color="#689f38"></a-box>
> ```

Wir positionieren eine Kiste im Raum mit dem `position` Attribut und machen sie sichtbar.
>[!box]- Positionieren im Raum 
> *Position ="x y z"* 
>
> ```html
> <a-box position="-1 0.5 -4"></a-box>
> ```
>![[right hand rule.jpg]]
> **X-Koordinate**
> ![](Atlas/Utilities/Attachments/1!IS0QPc6WC1f_HUIk6TkFhA.png.webp)
> **Y-Koordinate**
> ![](Atlas/Utilities/Attachments/1!KqaRvaAxqiKQhLpu6G4HEQ.png.webp)
> **Z-Koordinate**
> ![](Atlas/Utilities/Attachments/1!EJByuF99E2fIfyJWuJzASg.png.webp)

Weitere Properties

>*Width, depth and height*
Damit beinflussen wir die Breite, Tiefe und Höhe der Geometrie


>[!box]- Relative und absolutes Positionieren im Raum
> >*HTML Elemente sind hierarchisch angeordnet*
> ```html
> <div>
> 	<p>Paragraph 1</p> <!-- Geschwister-Element -->
> 	<p>Paragraph 2</p><!-- Geschwister-Element -->
> 	 <div>
> 		 <p>verschachtelter Paragraph 3</p><!-- Kind-Element -->
> 	</div>
> </div>
> ```
> Die Position eines verschachtelten Elementes bezieht sich *relativ* zu der Position des "Elternelements"
> ```html
> <a-box position="-1 0.5 -4">
> 	<a-box position="1 0 0"></a-box>
> </a-box>
> ```
> >*Wofür braucht man das?* (Beispiel mit den zwei Kreisen auf einem Panel)
> ```html
>          <a-box color="#689F38"
>                    width="8"
>                    height="4.5"
>                    depth="0.2"
>                    position="0 3 -7">
>                    <!-- Circle | Child Entity -->
>                    <a-circle color="#333333"
>                              side="double"
>                              position="2 0 0.11">
>                    </a-circle>
>             </a-box>
>             
>             <!-- Yellow Circle -->
>             <a-circle color="#FFC107"
>                       side="double"
>                       position="-2 3 -6.89">
>             </a-circle>
>```


Noch andere Basis-Geometrien

>[!box]- **a-cylinder**
>```html
><a-cylinder color="616161" height="2" radius=2 segments-radial=6 open-ended=true side="double"></a-cylinder
>```

>[!box]- **a-circle**
>```html
><a-circle color="#FFC107" side="double" position="-2 1 -7" rotation="" scale="" 
visible="" material="" geometry=""></a-circle>
>```

### Rotation

```html
<a-cylinder color="616161" height="2" radius=2 segments-radial=6 open-ended=true side="double" rotation="90 0 0"></a-cylinder>
```

### Scale

```html
<a-cylinder color="616161" height="2" radius=2 segments-radial=6 open-ended=true side="double" scale="1 1 1"></a-cylinder>
```

### Primitives

https://glitch.com/edit/#!/wild-shade-sushi?path=index.html%3A12%3A143

---
https://medium.com/@axcodes/an-overview-of-the-three-js-coordinate-system-07f75ee76e64

### Textures
`src` Attribut
[Ziegeltextur](https://cdn.glitch.global/3694ad6f-6029-48ee-8ecf-847d93d400ca/brick-piles-placed-factory-floor.jpg?v=1718354927626)
[Metalgittertextur](https://cdn.glitch.global/3694ad6f-6029-48ee-8ecf-847d93d400ca/metal-grid-texture_1048-5434.jpg?v=1718354928342)

https://opengameart.org/content/50-free-textures-4-normalmaps


>[!box] Assets managen
>```html
><a-assets>
> 	<img id="ziegel-textur" src="">
></a-assets>
><a-box material="color: #FFFFFF;
>                              src: #ziegel-textur;
>                              repeat: 2 2;
>                    width="4" height="4" depth="4"
>                    position="2 1.5 -9"
>                    scale="-1 1 1">
>             </a-box>
>```

> *Welche Eigenschaften haben Texturen?*

- Typen:
	- Albedo (oder Base material)
	- Normal (map)
	- Roughness
	- ... (gibt noch viel mehr 😆)

>[!box]- Normap map
> ```html
> <!doctype html>
> <html>
>     <head>
>         <title>Skybox</title>
>         <script src="https://aframe.io/releases/1.6.0/aframe.min.js"></script>
>     </head>
>     
>     <body>
>         <a-scene>
>             <!-- Asset Management System -->
>             <a-assets>
>                 <img id="floor" src="https://cdn.glitch.global/326bdbad-d0e2-476e-8a9b-ad9dad19771b/153.JPG?v=1718362016939">
>                 <img id="floor-NRM" src="https://cdn.glitch.global/326bdbad-d0e2-476e-8a9b-ad9dad19771b/153_norm.JPG?v=1718367787761">
>                 <img id="clear-sunny-sky" src="https://cdn.glitch.global/326bdbad-d0e2-476e-8a9b-ad9dad19771b/clear-sunny-sky.jpg?v=1718365668092">
>                 <img id="360-panorama" src="L12-IMGs/360-panorama.jpg">
>             </a-assets>
>             
>             <!-- Sky -->
>             <a-sky src="#clear-sunny-sky"
>                    rotation="0 64 0" radius="100">
>             </a-sky> 
>             
>             <!-- Ground | Realistic Style -->
>             <a-plane material="color: #FFFFFF;
>                                src: #floor;
>                                repeat: 5000 5000;
>                                normal-map: #floor-NRM;
>                                normal-texture-repeat: 5000 5000"
>                      rotation="-90 0 0"
>                      scale="10000 10000 1">
>             </a-plane> 
>             
>             <!-- Ground | Cartoonish Style
>             <a-plane material="color: #00AA00;
>                                shader: flat"
>                      rotation="-90 0 0"
>                      scale="10000 10000 1">
>             </a-plane> -->
>             
>             <!-- 360° Panorama 
>             <a-sky src="#360-panorama"></a-sky>
>             -->
>         </a-scene>
>     </body>
> </html>
> ```



