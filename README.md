# lau-griot

Living memory, told through stories. A griot doesn't store data — a griot tells stories about data. The story IS the memory.

Inspired by the West African griot tradition: the community's historian, genealogist, and musician all in one. When you need to remember something, you don't look it up — you ask the griot, and they tell you a story that contains the answer.

## The concept in 60 seconds

Traditional databases store facts. A griot stores *narratives* — sequences of events connected by cause, consequence, and character. This crate implements:

- **Oral histories:** sequences of events with emotional weight, not just timestamps
- **Story composition:** combine smaller stories into larger narratives
- **Memory recall:** query by character, theme, or emotional arc — not just key-value
- **Living memory:** memories that evolve when retold (like real oral traditions)
- **Genealogy:** who begat what, when, and why it matters

## Quick start

```rust
use lau_griot::{Griot, OralHistory, Story, MemoryQuery};

let mut griot = Griot::new("village historian");

// Tell a story about what happened
let story = Story::new("the great refactor")
    .with_character("Hermes")
    .with_event("discovered the deadlock at port.rs:102")
    .with_emotion("surprise", 0.8)
    .with_consequence("rewrote with AtomicBool, 13 lines");
griot.tell(story);

// Recall stories about Hermes
let memories = griot.recall(MemoryQuery::about("Hermes"));
for memory in &memories {
    println!("{}", memory.narrative());
}

// Oral history — the full village chronicle
let history = griot.oral_history();
history.export_json("village_chronicle.json");
```

## Key types

| Type | What it is |
|------|-----------|
| `Griot` | The storyteller — receives stories, recalls them on demand |
| `Story` | A narrative with characters, events, emotions, and consequences |
| `OralHistory` | The full chronicle — all stories the griot carries |
| `MemoryQuery` | Ask by character, theme, emotion, or time period |
| `Genealogy` | Who begat what — the lineage of agents and systems |

## Contributing

[Open an issue](https://github.com/SuperInstance/lau-griot/issues) or PR.
