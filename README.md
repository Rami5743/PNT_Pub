# PNT_pub

The published copy of the video on the Prime Number Theorem (in Hebrew), its
fourteen scenes, and their subtitles, with a page to watch them on
(`index.html`, served by GitHub Pages).

The source of the video (the script, the Manim code of every scene, the
plans) is in the repository `Rami5743/PNT`, under `video/pnt-intro/`. Nothing
here is edited by hand except `index.html`, this README, and the list of
subtitle languages in `manifest.json`.

## Layout

```
index.html                 the page
manifest.json              the videos, their titles and lengths, the subtitle languages
videos/pnt-intro.mp4       the whole video
videos/NN-slug.mp4         scene NN
subtitles/<lang>/<id>.srt  subtitles of video <id> in language <lang>
fonts/SubtitleSans.woff2   the subtitle font: DejaVu Sans, in which the % of p₁%(n) is an index too
icons/                     the site icon (π and ζ, set in TeX's Computer Modern), SVG and PNG
.nojekyll                  serve the files as they are
```

## Updating the videos

From a checkout of `Rami5743/PNT`, after the final video was assembled:

```bash
python3 video/pnt-intro/tools/publish.py /path/to/PNT_pub
```

It copies the videos and the Hebrew subtitles here and rewrites
`manifest.json`, keeping its list of languages.

## Adding subtitles in another language

1. Put the files in `subtitles/<code>/`, one per video, named after the video:
   `pnt-intro.srt`, `01-a-large-number.srt`, … (any subset; a video without a
   file simply does not offer that language).
2. Add the language to the `languages` list of `manifest.json`:

   ```json
   { "code": "en", "label": "English" }
   ```

The page reads the SRT files directly (it converts them to WebVTT in the
browser), so nothing has to be built. Run `publish.py` again after adding a
language, so that the subtitle font includes its letters.

## GitHub Pages

Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
`/ (root)`. The page is then at `https://rami5743.github.io/PNT_Pub/` (the path is case-sensitive: it is the repository name exactly).
