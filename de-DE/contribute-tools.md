---
layout: de-DE/default
title: Bei Rust mitwirken &mdash; tooling, IDEs und Infrastruktur &middot; Die Rust Programmiersprache
---

# Bei Rust mitwirken &mdash; tooling, IDEs und Infrastruktur

Werkzeuge spielen im Erfolg einer Sprache eine große Rolle,
und es gibt in diesem Bereich noch eine Menge Arbeit.
***Ein großer Schwerpunkt der aktuellen Entwicklung von Rust
ist, [die IDE_Experience zu verbessern][ides]***.
Dies beinhaltet Arbeit am gesamten Rust-Stack, vom Compiler selbst
bis zu deiner Lieblings-IDE. Folge für mehr Information dem Link.

Sowohl Cargo, der Paketmanager, als auch rustdoc, der Dokumentationsgenerator,
sind zwar voll funktionsfähig, aber leiden an einem Mangel an Entwicklern.
Rustdoc hat viele offene Probleme, im Main-Repository unter dem Label
[A-rustdoc] gelistet. Es sind hauptsächlich Bugs und Mitarbeit würde
lediglich einen Bugfix und eine Pull-Request erfordern.
Cargo hat [sein eigenes Repository und Issue-Tracker][Cargo], und
wer beitragen möchte, sollte sich in [#cargo] melden.

Obwohl Rust-Programme sowohl mit dem gdb als auch mit dem lldb Debugger eingeschränkt
untersucht werden kann, gibt es noch immer viele Fälle, in denen debugging
unerwartete Ergebnisse liefert oder auf unerwartete Weise funktioniert.
Diese Fälle werden im [A-debuginfo]-Label verwaltet.

Ideen für weitere tooling-Projekte zum Mithelfen finden sich in
[awesome-rust].

Es gibt häufig andere interessante Tooling-Projekte, welche nur auf
die richtigen Leute warten, um implementiert zu werden.
Diese können mit anderen Tooling-Enthusiasten in
[#rust-tools] diskutiert werden.

[#cargo]: https://client00.chat.mibbit.com/?server=irc.mozilla.org&channel=%23rustc
[#rust-tools]: https://client00.chat.mibbit.com/?server=irc.mozilla.org&channel=%23rust-tools
[A-debuginfo]: https://github.com/rust-lang/rust/issues?q=is%3Aopen+is%3Aissue+label%3AA-debuginfo
[A-rustdoc]: https://github.com/rust-lang/rust/issues?q=is%3Aopen+is%3Aissue+label%3AA-rustdoc
[Cargo]: https://github.com/rust-lang/cargo/issues
[awesome-rust]: https://github.com/kud1ing/awesome-rust
[ides]: https://forge.rust-lang.org/ides.html
