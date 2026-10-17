# DDL Todo Board

A month-calendar board plugin for [Super Productivity](https://github.com/super-productivity/super-productivity). It shows **only deadline todos** — tasks carrying the `DDL` tag with a due date/time — so hard deadlines never get buried among routine tasks, while those todos still behave as regular tasks everywhere else in the app.

## Features

- **Deadline-only month view**: a full-height calendar grid (weeks start Monday) listing only tasks tagged `DDL`. Overdue items are highlighted red; today is outlined.
- **In-cell creation**: hover a day cell and click the `+` that appears to open a small card next to the cell — title required, time optional (no time = all-day). The date is taken from the cell.
- **Click to edit**: click a todo's title to reopen the same card pre-filled, and change title, date or time.
- **Done items stay visible**: completed todos turn grey-green (configurable), get a strikethrough and sink to the bottom of their day.
- **Customizable colors**: a "配色" (Colors) button in the header opens a palette picker for pending and completed todo backgrounds (six presets each, persisted across sessions, dark-mode aware).
- **Real tasks under the hood**: a todo is a normal task with the `DDL` tag plus `dueDay`/`dueWithTime`, so it shows up in Today, Inbox, Planner and everywhere else. Tagging any existing task with `DDL` puts it on the board too.
- **Live refresh**: task create/update/delete hooks keep the board in sync with edits made in other views.

## Install

1. Download `ddl-todos-board.zip` from the [latest release](https://github.com/little-tiger001/ddl-todos-board/releases).
2. In Super Productivity: **Settings → Plugins → Choose Plugin File**, pick the zip.
3. Open **DDL 待办看板** from the left sidebar.

Requires Super Productivity ≥ 13.0.0 (developed and tested on 19.2.0).

## Usage notes

- The board lives in the main content area as its own view (left-sidebar entry), not in the built-in Schedule view — plugins cannot modify core views.
- The `DDL` tag is created automatically on first run and its id is remembered, so renaming the tag later is safe.
- UI strings are currently Chinese-only; the plugin structure follows the standard `manifest.json` + `index.html` iframe layout.

## Development

Source layout (zip root must contain these three files):

```
manifest.json   plugin metadata, permissions, hooks
index.html      the calendar board (iframe UI)
icon.svg        sidebar icon (fill-based outline, immune to host fill overrides)
```

Pack with: `Compress-Archive -Path manifest.json,index.html,icon.svg -DestinationPath ddl-todos-board.zip`
