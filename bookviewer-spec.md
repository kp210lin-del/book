# bookviewer Specification

`bookviewer` is the shared interaction and layout spec for the interactive HTML shogi-book pages in this repository.

## Goal

- Keep the board large and touch-friendly on iPad landscape.
- Keep answer images readable without collapsing the board/editor UI.
- Support direct board editing without sending the user to a separate edit mode first.
- Make promotion choice and move feedback happen on the board itself.
- Reuse the same UI language across multiple books.

## Covered Pages

The following pages currently follow the `bookviewer` spec.

- `yose-20260704d.html`
- `nidan.html`
- `laku.html`
- `kihonop.html`
- `honsuji.html`

## Layout Rules

- Use a two-column desktop/tablet layout with a wider left reading column and a centered right board column.
- Compute board size from real DOM width and height, not just viewport percentage.
- Keep the right column structured as `gote hand / board + tool column / sente hand`.
- Move the answer toggle into the right tool column on tablet/desktop.
- Keep the prev/next navigation fixed at the bottom of the left column.
- Hide hand labels such as `後手 持駒` and `先手 持駒` when they waste width.

## Board Interaction Rules

- Board interaction is direct by default.
- Hand pieces are selectable large tap targets.
- `SFENコピー` and `初期配置` stay in the right tool column.
- If a move can promote, show an on-board overlay with `成る / 成らず`.
- Do not require the user to use a side button for promotion choice.
- When a move or drop is committed, play a short move click sound.
- When a correct answer is committed, reveal the answer first and then play the success chime.

## Visual Rules

- Hand bands and tool buttons should use the same panel language and corner radius.
- Tool column controls should align to a single width rhythm.
- Answer images should use the full left-column width available to the answer area.
- The board should not grow without limit on wide desktop screens.

## Responsive Rules

- Mobile keeps the stacked layout.
- Tablet landscape uses the widened left reading column and the capped right board column.
- Board cell size is capped so the board remains balanced against the answer area.

## Reuse Guidance

- When another shogi-book HTML page uses the same interactive viewer structure, migrate it to `bookviewer` instead of inventing a new layout.
- If a page already has `answerModeBtn`, `reviewModeBtn`, board edit handlers, and hand-piece editing, it is a `bookviewer` migration candidate.
- Versioned HTML filenames may still be used for cache-busting on iPad/Safari when needed.

## Change Checklist

- Apply the shared CSS layout and size calculation.
- Ensure `showBtn` is relocated into the right tool column.
- Enable the promotion overlay.
- Enable move click audio.
- Verify at least one promotion position on the migrated page.
- Verify mobile stacking still works.
