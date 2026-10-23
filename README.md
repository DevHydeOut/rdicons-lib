# rd icons

521 free line icons on a 24 x 24 grid: 1.5 px stroke, round caps and joins, soft corners and an open top-right corner on container shapes. Every icon also has a hover animation.

Browse, customise and download them at **https://rdicons.vimalbhatt.com/library/rd**.

## Use

```bash
npm i @rdicons/react-rd
```

```jsx
import { Home, Bell } from '@rdicons/react-rd'

<Home />
<Bell animate />            // plays on hover
<Bell animate="loop" />     // repeats
```

Or copy a file from [`svg/`](svg) (static) or [`svg-animated/`](svg-animated) (animated, no JavaScript needed).

| Folder or file | What it is |
| --- | --- |
| [`svg/`](svg) | 521 static icons, `currentColor` |
| [`svg-animated/`](svg-animated) | 521 animated icons (CSS inside the SVG) |
| `icons.json` | all icons in the Iconify format |
| `animations.json` | animated drawing and CSS for each icon |
| [`STYLE.md`](STYLE.md), [`MOTION.md`](MOTION.md) | the drawing and animation rules |

## Contribute

Found an icon that looks off, or want one added? Open an issue with the name and a sketch or reference. The icons are generated from a private source, so accepted changes are applied there and published here.

## License

MIT. Use the icons in personal and commercial projects, no attribution needed.
