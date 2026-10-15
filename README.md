<p align="center">
  <img src="assets/og-image-16x9.jpg" alt="Logospell: AI image sets in one cohesive style" width="800">
</p>

# Setup

1. Sign up at [logospell.com](https://logospell.com): free starter
   credits, no card required.
2. Copy the API key from your account page.
3. Connect your client. Logospell is a hosted MCP server, so there is
   nothing to build or run locally.

More clients, with step-by-step setup: [logospell.com/connect](https://logospell.com/connect)

### Any MCP client

Endpoint: `https://mcp.logospell.com/mcp` (streamable HTTP, bearer API key).

```json
{
  "mcpServers": {
    "logospell": {
      "type": "http",
      "url": "https://mcp.logospell.com/mcp",
      "headers": { "Authorization": "Bearer ls_<your-key>" }
    }
  }
}
```

Agent-assisted setup: see [llms-install.md](llms-install.md).

### Claude Code

```
/plugin marketplace add logospell/logospell-mcp-server
/plugin install logospell@logospell
```

Claude Code asks for your API key when it enables the plugin.

### Grok Build

```
grok plugin install logospell/logospell-mcp-server --trust
```

Then set `LOGOSPELL_API_KEY` in your environment.

### Cursor

Save the `mcp.json` from the Cursor tab at
[logospell.com/connect](https://logospell.com/connect). Signed in, it
has your key filled in.

### Gemini CLI

```
gemini extensions install https://github.com/logospell/logospell-mcp-server
```

Gemini CLI asks for your API key when it installs the extension.

<br>

# MCP Tools

## Make a set

### `generate_image_set` · 1 credit

A cohesive set of separate subjects in one style, such as icons, game assets or UI elements, on one solid background color or transparent (`background: "transparent"`), so each image drops onto any backdrop. You set the style (in words, with up to 3 reference images, or both), up to 16 subjects, the background, an exact size or native resolution, how each subject fills its frame, the margin, the format and quality, and each file's name. A finished set can be grown with [`extend_image_set`](#extend_image_set--1-credit), delivered again with [`edit_set`](#edit_set--free), or exported for the web, iOS, Android and Flutter with [`export_set`](#export_set--free).

**With a transparent background**

<table>
  <tr>
    <th colspan="4" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="4"><samp><b>style</b></samp><br>Art Nouveau stained glass with dark lead lines and jewel-toned glass panes<br><br><samp><b>subjects</b></samp><ul><li>a peacock</li><li>a dragonfly</li><li>a calla lily</li><li>an iris</li><li>a swan</li><li>a hummingbird</li><li>a monarch butterfly</li><li>a koi fish</li><li>a snail</li><li>a barn owl</li><li>a rose</li><li>a lotus</li><li>a heron</li><li>a fox</li><li>a seahorse</li><li>a pinecone</li></ul><samp><b>background</b></samp><br>transparent</td>
  </tr>
  <tr>
    <th colspan="4" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_peacock.png" alt="a peacock" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_dragonfly.png" alt="a dragonfly" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_calla_lily.png" alt="a calla lily" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/an_iris.png" alt="an iris" width="192"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_swan.png" alt="a swan" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_hummingbird.png" alt="a hummingbird" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_monarch_butterfly.png" alt="a monarch butterfly" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_koi_fish.png" alt="a koi fish" width="192"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_snail.png" alt="a snail" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_barn_owl.png" alt="a barn owl" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_rose.png" alt="a rose" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_lotus.png" alt="a lotus" width="192"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_heron.png" alt="a heron" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_fox.png" alt="a fox" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_seahorse.png" alt="a seahorse" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/stained-glass/a_pinecone.png" alt="a pinecone" width="192"></td>
  </tr>
  <tr>
    <td colspan="4"><sub>Delivered at 557x556, the set's native size. Shown here from <code>export_set</code> at base size 128.</sub></td>
  </tr>
</table>

**With a solid background color**

<table>
  <tbody>
  <tr>
    <th colspan="4" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="4"><samp><b>style</b></samp><br>Maya stone relief carving fused with Celtic knotwork and gilded Byzantine accents<br><br><samp><b>subjects</b></samp><ul><li>a jaguar</li><li>a quetzal bird</li><li>a feathered serpent</li><li>a sun disk</li><li>a cacao pod</li><li>a ceremonial drum</li><li>a stag</li><li>a round shield</li><li>a harp</li><li>a raven</li><li>a war horn</li><li>a longship</li><li>an oak sprig with acorns</li><li>a hare</li><li>a leaping salmon</li><li>a torc necklace</li></ul><samp><b>background</b></samp><br>#ffffff</td>
  </tr>
  <tr>
    <th colspan="4" align="left">Your agent receives</th>
  </tr>
  </tbody>
  <tbody>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_jaguar.png" alt="a jaguar" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_quetzal_bird.png" alt="a quetzal bird" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_feathered_serpent.png" alt="a feathered serpent" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_sun_disk.png" alt="a sun disk" width="192"></td>
  </tr>
  </tbody>
  <tbody>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_cacao_pod.png" alt="a cacao pod" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_ceremonial_drum.png" alt="a ceremonial drum" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_stag.png" alt="a stag" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_round_shield.png" alt="a round shield" width="192"></td>
  </tr>
  </tbody>
  <tbody>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_harp.png" alt="a harp" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_raven.png" alt="a raven" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_war_horn.png" alt="a war horn" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_longship.png" alt="a longship" width="192"></td>
  </tr>
  </tbody>
  <tbody>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/an_oak_sprig_with_acorns.png" alt="an oak sprig with acorns" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_hare.png" alt="a hare" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_leaping_salmon.png" alt="a leaping salmon" width="192"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/maya-celtic-relief/a_torc_necklace.png" alt="a torc necklace" width="192"></td>
  </tr>
  </tbody>
  <tbody>
  <tr>
    <td colspan="4"><sub>Delivered at 527x524, the set's native size. Shown here from <code>export_set</code> at base size 128.</sub></td>
  </tr>
  </tbody>
</table>

<br>

### `generate_character_set` · 1 credit

A set of one character, such as a mascot, creature, person or single product, one variation of it per image: sticker and reaction packs, mascot poses, a product shown many ways. You describe the character in words (`character`), show it in up to 3 reference images (`characterReferences`, the most faithful way to keep one specific character), or both, and say what it is doing in each image (`variations`, up to 16). The background (a color or transparent), size, sizing, margin, format and quality controls are `generate_image_set`'s. A finished set can be grown with [`extend_character_set`](#extend_character_set--1-credit), delivered again with [`edit_set`](#edit_set--free), or exported with [`export_set`](#export_set--free).

<table>
  <tr>
    <th colspan="4" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="4"><samp><b>character</b></samp><br>a scholarly fennec fox scribe in a hooded robe, rendered as Ottonian illuminated-manuscript painting fused with Scythian gold animal-style metalwork, with gilded spiral ornament on the robe and ears<br><br><samp><b>variations</b></samp><ul><li>writing with a quill in rapt concentration</li><li>unrolling a long scroll with delight</li><li>yawning hugely with ears drooping</li><li>holding a candle aloft</li><li>bowing politely with paws together</li><li>laughing with eyes squeezed shut</li><li>frowning at a blotted page in mild despair</li><li>sniffing a flower with eyes closed</li><li>juggling three ink pots nervously</li><li>sleeping curled around a stack of books</li><li>pointing at a star map in excitement</li><li>carrying a heavy tome with a grunt</li><li>peeking out from behind a lectern shyly</li><li>raising a goblet in triumph</li><li>startled with fur standing on end</li><li>playing a small harp serenely</li></ul><samp><b>background</b></samp><br>transparent</td>
  </tr>
  <tr>
    <th colspan="4" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/writing_with_a_quill_in_rapt_concentration.png" alt="writing with a quill in rapt concentration" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/unrolling_a_long_scroll_with_delight.png" alt="unrolling a long scroll with delight" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/yawning_hugely_with_ears_drooping.png" alt="yawning hugely with ears drooping" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/holding_a_candle_aloft.png" alt="holding a candle aloft" width="186"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/bowing_politely_with_paws_together.png" alt="bowing politely with paws together" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/laughing_with_eyes_squeezed_shut.png" alt="laughing with eyes squeezed shut" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/frowning_at_a_blotted_page_in_mild_despair.png" alt="frowning at a blotted page in mild despair" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/sniffing_a_flower_with_eyes_closed.png" alt="sniffing a flower with eyes closed" width="186"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/juggling_three_ink_pots_nervously.png" alt="juggling three ink pots nervously" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/sleeping_curled_around_a_stack_of_books.png" alt="sleeping curled around a stack of books" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/pointing_at_a_star_map_in_excitement.png" alt="pointing at a star map in excitement" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/carrying_a_heavy_tome_with_a_grunt.png" alt="carrying a heavy tome with a grunt" width="186"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/peeking_out_from_behind_a_lectern_shyly.png" alt="peeking out from behind a lectern shyly" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/raising_a_goblet_in_triumph.png" alt="raising a goblet in triumph" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/startled_with_fur_standing_on_end.png" alt="startled with fur standing on end" width="186"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/fennec-scribe/playing_a_small_harp_serenely.png" alt="playing a small harp serenely" width="186"></td>
  </tr>
  <tr>
    <td colspan="4"><sub>Delivered at 551x573, the set's native size. Shown here from <code>export_set</code> at base size 128.</sub></td>
  </tr>
</table>

<br>

### `generate_illustration_set` · 1 credit

A set of composed pictures in one style, such as scenes, hero images, banners, posters or portraits, one picture per scene and up to 6 per call. You set the style (in words, with up to 3 reference images, or both), the scenes, the size (every picture in a call shares one, from a fixed list of shapes running from 8:1 to 1:8), and the format and quality. Without style references, the first scene is drawn first and the rest are drawn to match it. A finished set can be grown with [`extend_illustration_set`](#extend_illustration_set--1-credit), at its size or another from the list, delivered again at another of its own sizes with [`edit_set`](#edit_set--free), or exported for apps and sites with [`export_set`](#export_set--free).

<table>
  <tr>
    <th colspan="3" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="3"><samp><b>style</b></samp><br>Bold, wildly colorful retro-futurist travel poster art in the spirit of mid-century airline and national-park posters: flat screen-printed color shapes with crisp edges, a limited saturated palette of deep space blues, tangerine, magenta, teal and sunset orange, soft halftone grain and subtle paper texture, strong graphic silhouettes, dramatic simplified perspective and glowing rim light<br><br><samp><b>scenes</b></samp><ul><li>Inside a vast rotating space habitat: farmland, lakes and little white towns curve up and over the sky in a continuous ring, a bright strip of sunlight running along the center like a daytime moon. A family has a picnic on a grassy hilltop in the foreground, a kite flying high toward the fields hanging overhead. Morning light, wide view looking along the habitat&#x27;s length so the land rises into an arch across the top of the poster.</li><li>A sleek hydrofoil sailboat skims across a dark methane lake on Titan beneath a thick tangerine haze, its translucent sail glowing with diffuse light. The faint banded disk of Saturn shows through the haze high above, and rounded ice hills line the far shore. Low angle from just above the glassy surface, the boat&#x27;s wake spraying in a long curve, open hazy sky across the top third.</li><li>A glass elevator car climbs a ribbon-thin space elevator cable rising from an ocean platform toward orbit at dawn. Far below, the platform&#x27;s lights glow on a deep blue sea, and the curve of the Earth shows a thin band of orange sunrise along the horizon. Passengers press against the car&#x27;s windows. The camera looks straight up the cable from the platform, the tether vanishing into a star-filled sky.</li><li>A floating sphere of water hangs in the middle of an orbital spa, swimmers gliding through it and laughing inside bubbles of light, droplets drifting free around them. A huge round window behind shows the blue Earth turning slowly below. Soft cool light from the planet mixes with warm lamps along the curved walls. Wide interior view from the spa&#x27;s edge, the sphere centered against the window.</li><li>A hot-air balloon festival on a small low-gravity moon: dozens of striped balloons in tangerine, magenta and teal drift lazily over a field of craters, their baskets carrying waving passengers. An enormous ringed gas giant fills the sky behind them in soft evening light. Seen from the rim of a crater, the nearest balloon rising past the camera in the lower foreground.</li><li>A city on giant rails crawls slowly across the surface of Mercury, staying in the narrow band of twilight between scorching day and frozen night. The huge white-gold sun sits half-risen on the horizon behind it, throwing long shadows across cracked grey plains, and the city&#x27;s domes and towers glow with warm windows. Wide shot from ahead of the city, its rails leading the eye toward the blazing sun.</li></ul><samp><b>width</b></samp><br>848<br><br><samp><b>height</b></samp><br>1264</td>
  </tr>
  <tr>
    <th colspan="3" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/inside_a_vast_rotating_space_habitat_farmland.webp" alt="Inside a vast rotating space habitat: farmland, lakes and little white towns curve up and over the sky in a continuous ring, a bright strip of sunlight running along the center like a daytime moon. A family has a picnic on a grassy hilltop in the foreground, a kite flying high toward the fields hanging overhead. Morning light, wide view looking along the habitat&#x27;s length so the land rises into an arch across the top of the poster." width="264"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/a_sleek_hydrofoil_sailboat_skims_across_a_dark.webp" alt="A sleek hydrofoil sailboat skims across a dark methane lake on Titan beneath a thick tangerine haze, its translucent sail glowing with diffuse light. The faint banded disk of Saturn shows through the haze high above, and rounded ice hills line the far shore. Low angle from just above the glassy surface, the boat&#x27;s wake spraying in a long curve, open hazy sky across the top third." width="264"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/a_glass_elevator_car_climbs_a_ribbon-thin_space.webp" alt="A glass elevator car climbs a ribbon-thin space elevator cable rising from an ocean platform toward orbit at dawn. Far below, the platform&#x27;s lights glow on a deep blue sea, and the curve of the Earth shows a thin band of orange sunrise along the horizon. Passengers press against the car&#x27;s windows. The camera looks straight up the cable from the platform, the tether vanishing into a star-filled sky." width="264"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/a_floating_sphere_of_water_hangs_in_the_middle.webp" alt="A floating sphere of water hangs in the middle of an orbital spa, swimmers gliding through it and laughing inside bubbles of light, droplets drifting free around them. A huge round window behind shows the blue Earth turning slowly below. Soft cool light from the planet mixes with warm lamps along the curved walls. Wide interior view from the spa&#x27;s edge, the sphere centered against the window." width="264"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/a_hot-air_balloon_festival_on_a_small.webp" alt="A hot-air balloon festival on a small low-gravity moon: dozens of striped balloons in tangerine, magenta and teal drift lazily over a field of craters, their baskets carrying waving passengers. An enormous ringed gas giant fills the sky behind them in soft evening light. Seen from the rim of a crater, the nearest balloon rising past the camera in the lower foreground." width="264"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/retro-space-posters/a_city_on_giant_rails_crawls_slowly_across_the.webp" alt="A city on giant rails crawls slowly across the surface of Mercury, staying in the narrow band of twilight between scorching day and frozen night. The huge white-gold sun sits half-risen on the horizon behind it, throwing long shadows across cracked grey plains, and the city&#x27;s domes and towers glow with warm windows. Wide shot from ahead of the city, its rails leading the eye toward the blazing sun." width="264"></td>
  </tr>
  <tr>
    <td colspan="3"><sub>Delivered at 848x1264. Shown here from <code>export_set</code> at base size 394.</sub></td>
  </tr>
</table>

<br>

## Grow a set

### `extend_image_set` · 1 credit

Add more subjects to a set made with `generate_image_set`, generated exactly as the set was: the same style text and style references, and the background (a color or transparent), size, format, quality, margin and sizing of the batch you name, so a set grows past the 16-subject limit of one call without drifting. A set styled by text alone is sent up to 3 images from its first batch, so the new subjects are drawn like the rest. The new batch joins the set, and the whole set's download window restarts.

<br>

### `extend_character_set` · 1 credit

Add more variations to a set made with `generate_character_set`, generated exactly as the set was: the same character text and character references, and the background (a color or transparent), size, format, quality, margin and sizing of the batch you name, so a set grows past the 16-variation limit of one call. A set made from text alone is sent up to 3 images from its first batch, so the new variations are drawn like the rest. The new batch joins the set, and the whole set's download window restarts.

<br>

### `extend_illustration_set` · 1 credit

Add more scenes to a set made with `generate_illustration_set`, drawn exactly as the set was: the same style text and style references, and the format and quality of the batch you name, at its size or any other size the tool lists, so one set can hold a wide hero and tall posters. A set made from text alone is sent up to 3 images from its first batch, so the new scenes are drawn like the rest. The new batch joins the set, and the whole set's download window restarts.

<br>

## Deliver a set again

### `edit_set` · free

Change how an existing image set, character set or illustration set is delivered, without generating again. On an image or character set: `width` and `height` (both, one, or neither, as on the set tools), `canvas` (with no size fixed: `uniform` for one canvas across the set, `subject` to wrap each image around its own subject), `minimumMargin`, `sizing` (relative or fill), `format` and `quality`, and for a character set or a transparent image set `background` (a `#RRGGBB` color to compose over, or `"transparent"`). On an illustration set: `width` and `height` together, as one of the batch's own sizes (the size its scenes were drawn at, or an exact half, quarter and so on of it, down to 256 pixels on the shorter side), `format` and `quality`. Or `reset`, to return to the set as it was first delivered. Takes the set's `generation` id; a setting left out keeps its current value. The set is cut again from its full-resolution source and its download is replaced in place, so the same URL serves the new delivery. What the pictures show cannot be edited.

<br>

### `export_set` · free

Export an existing set for the web, iOS, Android and Flutter at the base size `baseSize` you name: every image at every density each platform needs, laid out as each expects, with a viewer and a ledger that says per tree whether any file has some blur. An image or character set exports as icons, at base sizes from 16 to 256; an illustration set exports its scenes whole, up to its `crispBaseSize` (a quarter of the longest side its scenes were drawn at), so it is always crisp. One batch and one size per call; `format` and `quality` default to the set's current ones. Every example image on this page came from it.

<br>

## Reference images

### `create_reference` · free

Create an upload slot for a reference image: you get back a ref_
token and a one-line curl upload command. Pass the token to whichever
tool takes reference images: `styleReferences` on `generate_image_set`
and `generate_illustration_set`, `characterReferences` on
`generate_character_set`, up to 3 each. To use an image from one of
your own recent generations, skip the upload: pass `sourceGeneration`
and `sourceImage` and the server copies that image in. To grow an
existing set, use its extend tool instead.

<br>

### `list_references` · free

List your live reference images, most recently used or uploaded first, with each one's `ref` token, upload URL and expiry, to recover a token you lost instead of uploading the image again.

<br>

### `delete_references` · free

Permanently delete one or more references you created with [`create_reference`](#create_reference--free), before they expire on their own: pass their tokens in `refs`, and the images are removed and the tokens stop working. Only the API key that created a reference can delete it.

<br>

## Your generations and credits

### `list_recent_generations` · free

List your recent generations, a page at a time, and get their download
URLs again, for example to recover a result lost to a dropped
connection. Generations made on the generate page at logospell.com
appear here too.

<br>

### `get_generations` · free

Get the full record of generations whose ids you have: download link and expiry, current delivery settings, where its reference images came from, and the prompt.json with the original call, so the generation can be extended or reproduced. Takes a `generations` list of ids.

<br>

### `delete_generations` · free

Permanently delete one or more of your generations before their download window closes: each download URL stops working, and the images and the source kept for edits and exports are removed. Takes a `generations` list of ids; pass all of a set's ids to delete the whole set. Only the API key that made a generation can delete it; there is no undo, and credits are not refunded.

<br>

### `check_credits` · free

Check how many image generation credits remain on your account: one
balance shared by your MCP calls and the logospell.com generate page.

<br>

### `buy_credits` · no charge to call

Get a Stripe Checkout link that buys 1 to 10 credit packs (`packs`,
default 1) for the account your API key belongs to, with no sign-in.
Open it, or hand it to your user, to pay with a card or Link; the
credits land on the key within seconds of payment.

<br>

# Network and credentials

Logospell's plugins talk only to `mcp.logospell.com`: the MCP endpoint
(`https://mcp.logospell.com/mcp`) plus the time-limited download URLs
its results return on the same host. They authenticate with your
`LOGOSPELL_API_KEY` as a bearer token, sent only there. No third-party
endpoints, no client-side telemetry; service calls are recorded
server-side as described in the privacy policy.

<br>

<p align="center"><a href="https://logospell.com/docs">Docs</a> · <a href="https://logospell.com/privacy">Privacy</a> · <a href="mailto:support@logospell.com">Support</a> · <a href="https://registry.modelcontextprotocol.io/?q=com.logospell">MCP Registry</a></p>

<p align="center"><a href="https://glama.ai/mcp/connectors/com.logospell/logospell"><img src="https://glama.ai/mcp/connectors/com.logospell/logospell/badges/score.svg" width="110" height="20" alt="Logospell on Glama: tool definition grade and endpoint health"></a></p>
