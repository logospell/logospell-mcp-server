<p align="center">
  <img src="assets/og-image-16x9.jpg" alt="Logospell: AI image sets in one cohesive style" width="800">
</p>

An AI agent built this travel site twice from one prompt. Once it drew
its own art; once Logospell did.

https://github.com/user-attachments/assets/8b0516e6-f5d0-4cd6-be56-2fda38cbf0c6

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

### `generate_image_set` · 1 credit

A cohesive set of images on a solid background, such as icons, game assets or UI elements. You set the style (in words, with reference images, or both), the background color, an exact size or native resolution, how each subject fills its frame, the margin, the format and quality, and each file's name. A finished set can be grown with [`extend_image_set`](#extend_image_set--1-credit), re-cut with [`edit_image_set`](#edit_image_set--free), or exported as web, iOS, Android and Flutter icons with [`export_icons`](#export_icons--free).

<table>
  <tr>
    <th colspan="3" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="3"><samp><b>style</b></samp><br>American traditional tattoo flash: bold black outlines, flat saturated red, green, yellow and blue, simple black shading<br><br><samp><b>subjects</b></samp><ul><li>a swallow in flight</li><li>an anchor wrapped in rope</li><li>a red rose</li><li>a clipper ship under full sail</li><li>a panther head</li><li>a pocket watch</li><li>a lighthouse</li><li>a spread-winged eagle</li><li>a lucky horseshoe</li></ul><samp><b>background</b></samp><br>#E4D0A6<br><br><samp><b>width</b></samp><br>256<br><br><samp><b>height</b></samp><br>256<br><br><samp><b>sizing</b></samp><br>relative<br><br><samp><b>minimumMargin</b></samp><br>10</td>
  </tr>
  <tr>
    <th colspan="3" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_swallow_in_flight.png" alt="a swallow in flight" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/an_anchor_wrapped_in_rope.png" alt="an anchor wrapped in rope" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_red_rose.png" alt="a red rose" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_clipper_ship_under_full_sail.png" alt="a clipper ship under full sail" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_panther_head.png" alt="a panther head" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_pocket_watch.png" alt="a pocket watch" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_lighthouse.png" alt="a lighthouse" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_spread-winged_eagle.png" alt="a spread-winged eagle" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tattoo-flash/a_lucky_horseshoe.png" alt="a lucky horseshoe" width="256"></td>
  </tr>
</table>

<br>

### `generate_transparent_image_set` · 1 credit

The same kind of set with transparent backgrounds, ready to drop onto any backdrop, with the same size, sizing and format controls. [`edit_image_set`](#edit_image_set--free) can later lay a finished set onto a background color.

<table>
  <tr>
    <th colspan="3" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="3"><samp><b>style</b></samp><br>Venetian millefiori glass mosaic: subjects assembled from tightly packed slices of glass cane, each disc bearing its own tiny star, rosette, or concentric ring pattern, in luminous ruby, cobalt, amber, jade, and violet, glassy polished sheen, fine dark seams between the discs<br><br><samp><b>subjects</b></samp><ul><li>a tortoise with a domed shell</li><li>a fox with a sweeping tail</li><li>a koi fish mid-leap</li><li>a dragonfly with double wings</li><li>a toucan with an oversized beak</li><li>a rabbit sitting upright with ears tall</li><li>a cactus in a patterned pot</li><li>a mermaid with a curled tail</li><li>a peacock with its tail fanned</li></ul><samp><b>background</b></samp><br>transparent (always; this tool has no background parameter)<br><br><samp><b>width</b></samp><br>256<br><br><samp><b>height</b></samp><br>256<br><br><samp><b>sizing</b></samp><br>relative<br><br><samp><b>minimumMargin</b></samp><br>10</td>
  </tr>
  <tr>
    <th colspan="3" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_tortoise_with_a_domed_shell.png" alt="a tortoise with a domed shell" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_fox_with_a_sweeping_tail.png" alt="a fox with a sweeping tail" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_koi_fish_mid-leap.png" alt="a koi fish mid-leap" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_dragonfly_with_double_wings.png" alt="a dragonfly with double wings" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_toucan_with_an_oversized_beak.png" alt="a toucan with an oversized beak" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_rabbit_sitting_upright_with_ears_tall.png" alt="a rabbit sitting upright with ears tall" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_cactus_in_a_patterned_pot.png" alt="a cactus in a patterned pot" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_mermaid_with_a_curled_tail.png" alt="a mermaid with a curled tail" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/millefiori-glass/a_peacock_with_its_tail_fanned.png" alt="a peacock with its tail fanned" width="256"></td>
  </tr>
</table>

<br>

### `generate_character_set` · 1 credit

A set of one character, such as a mascot, creature, person or single product, one variation of it per image on a solid background: sticker and reaction packs, mascot poses, a product shown many ways. You describe the character in words (`character`), show it in up to 3 reference images (`characterReferences`, the most faithful way to keep one specific character), or both, and say what it is doing in each image (`variations`). The background, size, sizing, margin, format and quality controls are the image set tools'. A finished set can be grown with [`extend_character_set`](#extend_character_set--1-credit), re-cut with [`edit_image_set`](#edit_image_set--free), or exported as icons with [`export_icons`](#export_icons--free).

<table>
  <tr>
    <th colspan="3" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="3"><samp><b>character</b></samp><br>A round orange tabby cat mascot with a red bandana, drawn in 1930s rubber-hose cartoon style: pie-cut eyes, white gloves, bendy noodle limbs, thick black ink outlines and flat orange and cream fills<br><br><samp><b>variations</b></samp><ul><li>waving hello with a huge grin</li><li>laughing so hard it doubles over clutching its belly</li><li>a slow-burning silent glare with arms crossed</li><li>sobbing two fountains of tears</li><li>leaping in pure joy with arms flung up</li><li>sipping a steaming mug of coffee with eyes half closed in bliss</li><li>a confident thumbs up and a wink</li><li>asleep curled up in a striped nightcap</li><li>shocked with fur standing on end and jaw dropped</li></ul><samp><b>background</b></samp><br>#BFE0DA<br><br><samp><b>width</b></samp><br>256<br><br><samp><b>height</b></samp><br>256<br><br><samp><b>sizing</b></samp><br>relative<br><br><samp><b>minimumMargin</b></samp><br>10</td>
  </tr>
  <tr>
    <th colspan="3" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/waving_hello_with_a_huge_grin.png" alt="waving hello with a huge grin" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/laughing_so_hard_it_doubles_over_clutching_its_belly.png" alt="laughing so hard it doubles over clutching its belly" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/a_slow-burning_silent_glare_with_arms_crossed.png" alt="a slow-burning silent glare with arms crossed" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/sobbing_two_fountains_of_tears.png" alt="sobbing two fountains of tears" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/leaping_in_pure_joy_with_arms_flung_up.png" alt="leaping in pure joy with arms flung up" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/sipping_a_steaming_mug_of_coffee_with_eyes_half_closed_in_bliss.png" alt="sipping a steaming mug of coffee with eyes half closed in bliss" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/a_confident_thumbs_up_and_a_wink.png" alt="a confident thumbs up and a wink" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/asleep_curled_up_in_a_striped_nightcap.png" alt="asleep curled up in a striped nightcap" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/rubber-hose-cat/shocked_with_fur_standing_on_end_and_jaw_dropped.png" alt="shocked with fur standing on end and jaw dropped" width="256"></td>
  </tr>
</table>

<br>

### `generate_transparent_character_set` · 1 credit

The same kind of character set with transparent backgrounds, stickers that drop onto any chat or backdrop, with the same size, sizing and format controls. [`edit_image_set`](#edit_image_set--free) can later lay a finished set onto a background color.

<table>
  <tr>
    <th colspan="3" align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td colspan="3"><samp><b>character</b></samp><br>A vintage tin wind-up toy robot: boxy printed-tin body in cherry red and cream, round dome head, a brass wind-up key on its back, riveted seams and little printed dials on its chest, with a glossy painted-tin sheen<br><br><samp><b>variations</b></samp><ul><li>marching forward mid-stride with arms swinging</li><li>waving hello with one clamp hand</li><li>shyly holding a bouquet of daisies</li><li>frazzled and confused with sparks and smoke rising from its head</li><li>dancing a jaunty jig on one foot</li><li>straining to lift a dumbbell overhead</li><li>saluting stiffly at attention</li><li>slumped over and wound down with its key stopped</li><li>cheering with both arms raised and its chest lights flashing</li></ul><samp><b>background</b></samp><br>transparent (always; this tool has no background parameter)<br><br><samp><b>width</b></samp><br>256<br><br><samp><b>height</b></samp><br>256<br><br><samp><b>sizing</b></samp><br>relative<br><br><samp><b>minimumMargin</b></samp><br>10</td>
  </tr>
  <tr>
    <th colspan="3" align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/marching_forward_mid-stride_with_arms_swinging.png" alt="marching forward mid-stride with arms swinging" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/waving_hello_with_one_clamp_hand.png" alt="waving hello with one clamp hand" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/shyly_holding_a_bouquet_of_daisies.png" alt="shyly holding a bouquet of daisies" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/frazzled_and_confused_with_sparks_and_smoke_rising_from_its_head.png" alt="frazzled and confused with sparks and smoke rising from its head" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/dancing_a_jaunty_jig_on_one_foot.png" alt="dancing a jaunty jig on one foot" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/straining_to_lift_a_dumbbell_overhead.png" alt="straining to lift a dumbbell overhead" width="256"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/saluting_stiffly_at_attention.png" alt="saluting stiffly at attention" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/slumped_over_and_wound_down_with_its_key_stopped.png" alt="slumped over and wound down with its key stopped" width="256"></td>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/tin-robot/cheering_with_both_arms_raised_and_its_chest_lights_flashing.png" alt="cheering with both arms raised and its chest lights flashing" width="256"></td>
  </tr>
</table>

<br>

### `extend_image_set` · 1 credit

Add more subjects to a set made with either image set tool, generated exactly as the set was: the same tool, style text and style references, and the background, size, format, quality, margin and sizing of the batch you name, so a set grows past the 16-subject limit of one call without drifting. A set styled by text alone is sent up to 3 images from its first batch, so the new subjects are drawn like the rest. The new batch joins the set, and the whole set's download window restarts.

<br>

### `extend_character_set` · 1 credit

Add more variations to a set made with either character set tool, generated exactly as the set was: the same tool, character text and character references, and the background, size, format, quality, margin and sizing of the batch you name, so a set grows past the 16-variation limit of one call. A set made from text alone is sent up to 3 images from its first batch, so the new variations are drawn like the rest. The new batch joins the set, and the whole set's download window restarts.

<br>

### `generate_illustration` · 1 credit

One composed picture, such as a scene, hero image, banner or portrait, in a wide range of aspect ratios, as PNG, JPEG or WebP at the quality you choose. Up to 3 reference images (`references`) can supply a style to match, or a character, product or place to include; the prompt says what each is for. Each ratio's sizes are exact halves of one another, so this 1584x672 picture displays crisply at 792x336. A finished illustration can be delivered again at another of its sizes, format or quality with [`edit_illustration`](#edit_illustration--free).

<table>
  <tr>
    <th align="left">Your agent asks for</th>
  </tr>
  <tr>
    <td><samp><b>prompt</b></samp><br>A small brass-and-glass airship moored to a clifftop lighthouse at sunset: the keeper waves from the railed gallery, gulls wheel overhead, and warm amber light spills across a calm sea far below. Painterly storybook illustration, rich and detailed, luminous golden-hour palette<br><br><samp><b>width</b></samp><br>1584<br><br><samp><b>height</b></samp><br>672</td>
  </tr>
  <tr>
    <th align="left">Your agent receives</th>
  </tr>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/logospell/logospell-mcp-server/main/examples/airship-lighthouse.webp" alt="a brass-and-glass airship moored to a clifftop lighthouse at sunset" width="792"></td>
  </tr>
</table>

<br>

### `create_reference` · free

Create an upload slot for a reference image: you get back a ref_
token and a one-line curl upload command. Pass the token to whichever
tool takes reference images: `styleReferences` on the image set
tools, `characterReferences` on the character set tools, `references`
on `generate_illustration`, up to 3 each. To use an image from one of
your own recent generations, skip the upload: pass `sourceGeneration`
and `sourceImage` and the server copies that image in. To grow an
existing set, use [`extend_image_set`](#extend_image_set--1-credit) or
[`extend_character_set`](#extend_character_set--1-credit) instead.

<br>

### `list_references` · free

List your live reference images, most recently used or uploaded first, with each one's `ref` token, upload URL and expiry, to recover a token you lost instead of uploading the image again.

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

### `list_recent_generations` · free

List your recent generations, a page at a time, and get their download
URLs again, for example to recover a result lost to a dropped
connection. Generations made on the generate page at logospell.com
appear here too.

<br>

### `get_generations` · free

Get the full record of generations whose ids you have: download link and expiry, current delivery settings, where its reference images came from, and the prompt.json with the original call, so the generation can be extended or reproduced. Takes a `generations` list of ids.

<br>

### `edit_image_set` · free

Change how an existing image set or character set is delivered without generating again: `width` and `height` (both, one, or neither, as on the set tools), `canvas` (with no size fixed: `uniform` for one canvas across the set, `subject` to wrap each image around its own subject), `minimumMargin`, `sizing` (relative or fill), `format` and `quality`, and for a transparent set `background` (a `#RRGGBB` color to compose over, or `"transparent"`), or `reset` to return to the set as it was first delivered. Takes the set's `generation` id; a lever left out keeps its current value. The set's download is replaced in place, so the same URL serves the new delivery. Style, subjects and references cannot be edited.

<br>

### `edit_illustration` · free

Change how an existing illustration is delivered without generating again: `width` and `height` together, as one of its own sizes (the size the model made it at, or an exact half, quarter and so on of it, down to 256 pixels on the shorter side), `format` and `quality`, or `reset` to return to the first delivery. Takes the illustration's `generation` id; a setting left out keeps its current value. It is cut from the model's original image, and its download is replaced in place, so the same URL serves the new delivery. The prompt and references cannot be edited.

<br>

### `export_icons` · free

Export an existing image set or character set as icons for the web, iOS, Android and Flutter at the base size `iconSize` you name (an even number, 16 to 256; it sizes the batch, so every icon is the delivered image scaled and no file exceeds it): every subject at every density each platform needs, laid out as each expects, with a viewer and a ledger that says per tree whether any file has some blur. One batch and one size per call; `format` and `quality` default to the set's current ones.

<br>

### `delete_generations` · free

Permanently delete one or more of your generations before their download window closes: each download URL stops working, and the images and the source kept for edits and icon exports are removed. Takes a `generations` list of ids; pass all of a set's ids to delete the whole set. Only the API key that made a generation can delete it; there is no undo, and credits are not refunded.

<br>

### `delete_references` · free

Permanently delete one or more references you created with [`create_reference`](#create_reference--free), before they expire on their own: pass their tokens in `refs`, and the images are removed and the tokens stop working. Only the API key that created a reference can delete it.

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
