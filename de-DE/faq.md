---
layout: de-DE/faq
title: Häufig gestellte Fragen &middot; Die Programmiersprache Rust
---

# Häufig gestellte Fragen

<p class="faq-intro">
Auf dieser Seite werden häufig gestellte Fragen über die Programmiersprache Rust beantwortet. Die Seite ist keine vollständige Anleitung und zum Lernen der Sprache ungeeignet. Sie versucht, Antworten auf Fragen zu geben, welche in der Rust Community immer wieder aufgetreten sind, und verdeutlicht einige Überlegungen hinter Rust's Design-Entscheidungen.
</p>

<p class="faq-intro">
Wenn dir auffällt, dass hier eine wichtige oder verbreitete Frage fehlt, dann <a href="https://github.com/rust-lang/rust-www/blob/master/CONTRIBUTING.md">hilf uns, das zu ändern</a>.
</p>

<div id="toc">
    <h2>Inhaltsverzeichnis</h2><a href="#toggle-toc"></a>
    <div class="contents">
        <ol id="toc-contents">
            <li><a href="#project">Das Rust Projekt</a></li>
            <li><a href="#performance">Performance</a></li>
            <li><a href="#syntax">Syntax</a></li>
            <li><a href="#numerics">Arithmetik</a></li>
            <li><a href="#strings">Strings</a></li>
            <li><a href="#collections">Collections</a></li>
            <li><a href="#ownership">Ownership</a></li>
            <li><a href="#lifetimes">Lifetimes</a></li>
            <li><a href="#generics">Generics</a></li>
            <li><a href="#input-output">Eingabe / Ausgabe</a></li>
            <li><a href="#error-handling">Fehlerbehandlung</a></li>
            <li><a href="#concurrency">Nebenläufigkeit</a></li>
            <li><a href="#macros">Makros</a></li>
            <li><a href="#debugging">Debugging und Tooling</a></li>
            <li><a href="#low-level">Low-Level</a></li>
            <li><a href="#cross-platform">Cross-Platform</a></li>
            <li><a href="#modules-and-crates">Module und Crates</a></li>
            <li><a href="#libraries">Bibliotheken</a></li>
            <li><a href="#design-patterns">Entwurfsmuster</a></li>
            <li><a href="#other-languages">Andere Sprachen</a></li>
            <li><a href="#documentation">Dokumentation</a></li>
        </ol>
    </div>
</div>


<h2 id="project">Das Rust Projekt</h2>

<h3><a href="#what-is-this-projects-goal" name="Was ist das Ziel des Rust Projektes?">
Was ist das Ziel des Rust Projektes?
</a></h3>

Das Ziel des Rust Projektes ist es, eine sichere, nebenläufige und praktikable Systemsprache zu implementieren.

Rust existiert, weil andere, ähnlich abstrakte und effiziente Sprachen folgende Erwartungen nicht erfüllen:

1. Es wird zu wenig auf Sicherheit geachtet.
2. Die Unterstützung für Nebenläufigkeit ist mangelhaft.
3. Für manche Sprachmerkmale gibt es keine praktische, einleuchtende Benutzung.
4. Es gibt nur eingeschränkte Kontrolle über Ressourcen.

Rust existiert als eine Alternative, welche sowohl effizienten Code als auch ein komfortables Abstraktionsniveau bietet, und dabei für jeden dieser vier Punkte Verbesserungen vorschlägt.

<h3><a href="#is-this-project-controlled-by-mozilla" name="Wird dieses Projekt von Mozilla kontrolliert?">
Wird dieses Projekt von Mozilla kontrolliert?
</a></h3>

Nein. Im Jahr 2006 startete Graydon Hoare Rust als Teilzeitprojekt, und so blieb es für 3 Jahre. Erst als Rust 2009 die nötige Reife erreichte, um Kernkonzepte anhand einfacher Tests zu demonstrieren, beteiligte sich Mozilla. Rust wird vorrangig von Mozilla unterstützt, aber eine vielfältige, enthusiastische Community in der ganzen Welt arbeitet daran. Das [Rust Team](https://www.rust-lang.org/team.html) besteht sowohl aus Mitarbeitern von Mozilla als auch aus unabhängigen Mitgliedern, und `rust` auf GitHub hatte bisher schon über [1,500 verschiedene Mitwirkende](https://github.com/rust-lang/rust/).

Die [Führung des Projektes](https://github.com/rust-lang/rfcs/blob/master/text/1068-rust-governance.md) besteht aus einem Kernteam, welches die Vision und die Prioritäten festlegt und das Projekt von einer globalen Perspektive aus leitet. Es gibt auch kleinere Teams, welche sich um die Entwicklung bestimmter Interessenbereiche kümmern. Das können zum Beispiel der Kern der Sprache, der Compiler, Rust Bibliotheken, Tooling oder die Moderation der offiziellen Rust Communities sein. Fortschritt in jedem dieser Bereiche wird über einen [RFC-Prozess](https://github.com/rust-lang/rfcs) erreicht. Änderungen, für welche kein RFC notwendig ist, werden normalerweise in einer Pull Request im [`rustc` Repository](https://github.com/rust-lang/rust) diskutiert.

<h3><a href="#what-are-some-non-goals" name="Welche Ziele werden nicht angestrebt?">
Welche Ziele werden nicht angestrebt?
</a></h3>

1. Wir verwenden keine besonders modernen Technologien. Alte, etablierte Technologien sind besser.
2. Expressivität, Minimalismus oder Eleganz sind wünschenswerte, aber untergeordnete Ziele.
3. Wir beabsichtigen nicht, alle Eigenschaften und Möglicheiten von C++ oder anderen Sprachen abzudecken. Rust sollte die häufigsten Fälle abdecken.
4. Wir beabsichtigen nicht, 100% statisch, 100% sicher, 100% reflektiv oder zu dogmatisch in irgendeiner anderen Hinsicht zu sein. Es gibt Kompromisse.
5. Wir zielen nicht darauf ab, dass Rust auf jeder möglichen Plattform läuft. Rust soll ohne unnötige Kompromisse auf üblichen, verbreiteten Hardware- und Softwareplattformen laufen.

<h3><a href="#how-does-mozilla-use-rust" name="Wie nutzt Mozilla Rust?">
In welchen Projekten nutzt Mozilla Rust?
</a></h3>

Hauptsächlich wird Rust in [Servo](https://github.com/servo/servo), einer experimentellen Browser Engine, an welcher Mozilla arbeitet, verwendet. Mozilla arbeitet auch daran, weitere Rust Komponenten [in Firefox zu integrieren](https://bugzilla.mozilla.org/show_bug.cgi?id=1135640).

<h3><a href="#what-examples-are-there-of-large-rust-projects" name="Welche großen Rust-Projekte gibt es?">
Welche großen Rust-Projekte gibt es?
</a></h3>

Die zwei im Moment größten quelloffenen Rust-Projekte sind [Servo](https://github.com/servo/servo) und der [Rust Compiler](https://github.com/rust-lang/rust) selbst.

<h3><a href="#who-else-is-using-rust" name="Wer benutzt sonst noch Rust?">
Wer benutzt sonst noch Rust?
</a></h3>

[Eine wachsende Zahl von Organisationen!](friends.html)

<!--
### What projects are good examples of idiomatic Rust code?

TODO: Write this answer.
-->

<h3><a href="#how-can-i-try-rust-easily" name="Wie kann ich Rust einfach ausprobieren?">
Wie kann ich Rust einfach ausprobieren?
</a></h3>

Der einfachste Weg, Rust auszuprobieren, ist der [Playpen](https://play.rust-lang.org/) - eine Online-Applikation, in welcher man einfach Rust Code schreiben und Ausführen kann. Wenn du Rust auf deinem eigenen System ausprobieren willst, [installiere es](https://www.rust-lang.org/install.html) und gehe das [Guessing Game](https://doc.rust-lang.org/stable/book/guessing-game.html) Tutorial im Buch durch.

<h3><a href="#how-do-i-get-help-with-rust-issues" name="Wie bekomme ich bei Problemen mit Rust Hilfe?">
Wie bekomme ich bei Problemen mit Rust Hilfe?
</a></h3>

Es gibt viele Wege. Du kannst:

- Einen Forenpost im offiziellen Rust User Forum [users.rust-lang.org](https://nsers.rust-lang.org/) absetzen.
- Im offiziellen [Rust IRC Kanal](https://chat.mibbit.com/?server=irc.mozilla.org&channel=%23rust) (#rust on irc.mozilla.org) eine Frage stellen.
- Auf [Stack Overflow](https://stackoverflow.com/questions/tagged/rust) eine Frage stellen (markiere sie mit dem "rust" tag!).
- Im inoffiziellen Rust Subreddit [/r/rust](https://www.reddit.com/r/rust) posten.

<h3><a href="#why-has-rust-changed-so-much" name="Warum hat sich Rust so stark verändert?">
Warum hat sich Rust über die Zeit so stark verändert?
</a></h3>

Das ursprüngliche Ziel von Rust war es, eine sichere, aber einfach zu benutzende Systemprogrammiersprache zu erstellen.
Um dieses Ziel zu erreichen, verfolgte Rust eine Vielzahl von Ideen, von denen es manche behielt (lifetimes, traits) und andere wieder verwarf (das typestate-System oder green threading). Außerdem wurde ein großer Teil der Rust Standardbibliotheken vor der Veröffentlichung der Version 1.0 neu geschrieben, um mithilfe der Features von Rust eine qualitativ hochwertige, konsistente, Plattformübergreifende API anzubieten. Jetzt, wo Rust die Version 1.0 erreicht hat, wird garantiert, dass die Sprache stabil ist; obwohl die Sprache sich weiter entwickelt, wird Code, welcher auf aktuellen Versionen von Rust funktioniert, auch in zukünftigen Versionen des Compilers gültiger Rust Code sein.

<h3><a href="#how-does-rust-language-versioning-work" name="Wie funktioniert Versionierung in Rust?">
Wie funktioniert Versionierung in Rust?
</a></h3>

Die Sprachversionierung von Rust folgt [SemVer](http://semver.org/). Änderungen an stabilen API's, welche die Abwärtskompatibilitätnicht gewährleisten, sind in 'minor' Versionen nur erlaubt, wenn sie Fehler oder Sicherheitslücken im Compiler beheben, oder wenn die Änderungen weitere Annotationen für Dispatch oder Typinferenz erforderlich machen. Weitere, detailreichere Richtlinien für 'minor' Versionsänderungen sind als genehmigte RFC's sowohl für die [Sprache](https://github.com/rust-lang/rfcs/blob/master/text/1122-language-semver.md) als auch die [Standardbibliotheken](https://github.com/rust-lang/rfcs/blob/master/text/1105-api-evolution.md) zu finden.

Es gibt drei Veröffentlichungskanäle für Rust: Stable, Beta, und Nightly. Die Kanäle Stable und Beta werden alle sechs Wochen aktualisiert, wobei der aktuelle Nightly zur neuen Beta und die aktuelle Beta das neue Stable wird. Teile der Standardbibliotheken sind als 'unstable' markiert oder durch 'Feature Gates' abgeschirmt. Diese können ausschließlich im Nightly-Kanal verwendet werden. Neue Features sind solange als 'unstable' markiert, bis das Kernteam und zuständige Unterteams ihre Zustimmung zur Freigabe gegeben haben. Diese Herangehensweise erlaubt es Entwicklern, zu experimentieren, ohne die Garantie auf Abwärtskompatibilität zu gefährden.

Mehr Details finden sich im Blogpost ["Stability as a Deliverable"](http://blog.rust-lang.org/2014/10/30/Stability.html).

<h3><a href="#can-i-use-unstable-features-on-the-beta-or-stable-channel" name="Kann ich auf dem Beta- oder Stable Channel Features aus dem Unstable Channel verwenden?">
Kann ich auf dem Beta- oder Stable Channel Features aus dem Unstable Channel verwenden?
</a></h3>

Nein, das ist unmöglich. An Rust wird hart gearbeitet, um die Stabilität der Beta- und Stable Kanäle zu gewährleisten. Wir wollen nicht, dass sich jemand auf unstabile Features verlässt, für welche wir keine Stabilität gewährleisten und welche sich jederzeit ändern könnten. Das gibt uns auch die Möglichkeit, Änderungen im Nightly-Kanal realistisch auszutesten, während der Beta- und Stable Kanal stabil und unverändert bleiben.

Alle sechs Wochen werden die Beta- und Stable Kanäle mit den stabilisierten Features aktualisiert. Im Nightly-Kanal gibt es häufig stabilisierende Updates, während die anderen Kanäle seltener Fixes akzeptieren. Wenn du darauf wartest, dass ein Feature im Beta- oder Stable Kanal bereitgestellt wird, dann kannst du die zugehörige Issue mit dem Tag [`B-unstable`](https://github.com/rust-lang/rust/issues?q=is%3Aissue+is%3Aopen+tracking+label%3AB-unstable) auf dem Issue Tracker finden.

<h3><a href="#what-are-feature-gates" name="Was sind 'Feature Gates'?">
Was sind 'Feature Gates'?
</a></h3>

"Feature Gates" sind der Sprachmechanismus, den Rust verwendet, um Features des Compilers, der Sprache und der Standardbibliotheken zu stabilisieren. Ein Feature hinter einer 'gate' ist nur im Nightly-Kanal verfügbar, und auch nur dann, wenn es explizit durch ein `#[feature]`-Attribut oder das Kommandozeilenargument `-Z unstable-options` angefordert wurde. Wenn ein Feature stabilisiert und in den Stable-Kanal übernommen wird, muss es nicht mehr explizit angefordert werden. Dann wird dieses Feature als "ungated" bezeichnet. Feature Gates erlauben es den Entwicklern, zu experimentieren, während sie in der Entwicklung sind. Erst wenn die Entwickler sich auf eine Implementierung festlegen, halten die Features in der stabilen Sprache Einzug.

<h3><a href="#why-a-dual-mit-asl2-license" name="Warum eine MIT-ASL2 Doppellizenz?">
Warum eine MIT-ASL2 Doppellizenz?
</a></h3>

Die Apache-Lizenz enthält wichtigen Schutz gegen Patentaggressoren, aber ist mit der GPLv2 inkompatibel. Um Probleme bei der Verwendung von Rust mit der GPLv2-Lizenz zu vermeiden, ist es alternativ MIT-lizenziert.

<h3><a href="#why-a-permissive-license" name="Warum eine permissive Lizenz?">
Warum eine BSD-artige Freizügige Lizenz anstelle von MPL oder einer dreifachen Lizenz?
</a></h3>

Das liegt zu einem Teil an einer persönlichen Vorliebe des originalen Entwicklers Graydon Hoare, zum anderen daran, dass Programmiersprachen im Gegensatz zu Produkten wie Webbrowsern normalerweise einen weiter gefächerten Einflussbereich und ein vielseitigeres Einsatzzgebiet haben. Wir würden gerne möglichst viele dieser potenziellen Mitwirkenden anziehen.

<h2 id="performance">Performance</h2>

<h3><a href="#how-fast-is-rust" name="Wie schnell ist Rust?">
Wie schnell ist Rust?
</a></h3>

Sehr Schnell! Rust kann sich bereits in einigen Benchmarks (zu Beispiel dem [Benchmarks Game](https://benchmarksgame.alioth.debian.org/u64q/compare.php?lang=rust&lang2=gpp) und [anderen](https://github.com/kostya/benchmarks)) mit idiomatischem C und C++ Code messen.

Eins der wichtigsten Prinzipien in Rust (wie auch in C++) sind [Zero-Cost Abstractions](http://blog.rust-lang.org/2015/05/11/traits.html): Keine der Abstraktionen in Rust verursachen Programmweite Verlangsamungen, und es gibt keinen Mehraufwand zur Laufzeit des Programms.

Da Rust auf LLVM aufbaut und deshalb auch versucht, Clang-kompatiblen Code zu generieren, sind Leistungsverbesserungen in LLVM auch für Rust vorteilhaft. Langfristig sollten die detaillierten Informationen des Typsystems Optimisationen ermöglichen, welche in C/C++ unmöglich wären.

<h3><a href="#is-rust-garbage-collected" name="Gibt es in Rust einen Garbage Collector?">
Gibt es in Rust einen Garbage Collector?
</a></h3>

Nein. Eine der Schlüsselinnovationen von Rust ist es, *ohne* Garbage Collection Speichersicherheit (keine Segfaults) zu garantieren. 

Rust erlangt dadurch einige Vorteile: Vorhersagbare Bereinigung von Ressourcen, niedrige Mehrkosten für Speichermanagement, und ein minimales Laufzeitsystem. Diese Eigenschaften ermöglichen es, Rust in beliebige Umgebungen einzubinden, und vereinfachen die [Integration von Rust in Sprachen mit GC](http://calculist.org/blog/2015/12/23/neon-node-rust/).

Das Ownership und Borrowing System ermöglicht nicht nur Speichersicherheit ohne einen GC sondern ist auch in anderen Zusammenhängen nützlich, zum Beispiel [allgemeines Ressourcenmanagement](http://blog.skylight.io/rust-means-never-having-to-close-a-socket/) und [Nebenläufigkeit](http://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html).

In Fällen, in denen einfache Ownership nicht genügt, nutzen Rust Programme den üblichen Referenzzähler/Smart Pointer Typ [`Rc`](https://doc.rust-lang.org/std/rc/struct.Rc.html) und sein Thread-sicheres Gegenstück, [`Arc`](https://doc.rust-lang.org/std/sync/struct.Arc.html).

Allerdings wird daran gearbeitet, in Zukunft einen *optionalen* Garbage Collector als Erweiterung anzubieten, um eine gute Integration mit Laufzeitumgebungen wie [Spidermonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)
und [V8](https://developers.google.com/v8/?hl=en) zu ermöglichen, welche Garbage Collection verwenden.

Es gibt auch experimentelle, in [purem Rust implementierte Freispeichersammler](https://manishearth.github.io/blog/2015/09/01/designing-a-gc-in-rust/), welche ohne Unterstützung des Compilers funktionieren.

<h3><a href="#why-is-my-program-slow" name="Warum ist mein Programm langsam?">
Warum ist mein Programm langsam?
</a></h3>

Der Rust Compiler optimiert Programme nur dann, wenn man das explizit anfordert, da [Optimisationen die Kompiliergeschwindigkeit verringern und allgemein während der Entwicklung unerwünscht sind](https://users.rust-lang.org/t/why-does-cargo-build-not-optimise-by-default/4150/3).

Wenn du mit `cargo` kompilierst, nutze die `--release` option. Wenn du dein Program direkt mit `rustc` erstellst, nutze die Option `-0`. Beide Optionen schalten Optimisationen ein.

<h3><a href="#why-is-rustc-slow" name="Warum ist Rustc langsam?">
Warum ist die Erstellung meines Programmes zeitaufwändig?
</a></h3>

Rustc übersetzt und optimiert Code. Die hochwertigen Abstraktionen in Rust kompilieren zu effizientem Maschinencode, und um diese Übersetzungen durchzuführen, wird Zeit benötigt - insbesondere beim Optimieren.

Die Zeit, welche Rust zum Kompilieren benötigt, ist besser als sie scheint, und es gibt Anlass zur Hoffnung, dass sie sich verbessern wird. Kompilierzeiten von ähnlich umfangreichen Rust- und C++ Projekten sind im Allgemeinen miteinander vergleichbar.

Die häufige Auffassung, dass Rust langsam kompiliert, kommt zum Großteil aus dem Unterschied zwischen dem *Kompiliermodell* von C++ und Rust: Eine Kompiliereinheit in C++ ist eine Datei, während in Rust eine gesamte Crate kompiliert wird, welche aus vielen Dateien bestehen kann. Eine einzelne Datei während der Entwicklung zu verändern führt in C++ normalerweise zu weniger Rekompilation als in Rust. Es wird derzeit viel Arbeit in [inkrementelle Programmerstellung](https://github.com/rust-lang/rfcs/blob/master/text/1298-incremental-compilation.md) investiert, welche die Vorteile des Modells von C++ in Rust einführt.

Neben dem Kompilationsmodell gibt es andere Aspekte des Sprachdesigns und der Compilerimplementation, welche die Kompilierleistung beeinflussen.

Rust hat zunächst ein relativ komplexes Typsystem, und der Compiler muss einige Zeit darauf verwenden, die Typbeschränkungen zu überprüfen, welche Rust zur Laufzeit absichern.

Außerdem sind einige Teile des Rust Compilers ziemlich veraltet. Diese generieren insbesondere LLVM IR niedriger Qualität, welche LLVM erst "reparieren" muss. Es gibt Hoffnung, dass zukünftige, [MIR-basierte](https://github.com/rust-lang/rfcs/blob/master/text/1211-mir.md) Übersetzungs- und Optimierungsdurchläufe LLVM die Arbeit einfacher machen.

Drittens hat die Nutzung von LLVM auch ihre Kosten: Rust hat dadurch hohe Leistung zur Laufzeit, aber LLVM ist ein großes Framework welches nicht auf hohe Leistung zur Kompilation fokussiert ist, insbesondere bei Eingaben mit mangelhafter Qualität.

Letztlich führt auch die übliche Strategie der Monomorphisierung von Generics (wie in C++) zwar zu schnellem Code zur Laufzeit, aber sie erfordert die Erzeugung von Signifikant mehr Code als andere Strategien. Durch die Verwendung von Trait-Objekten können Rust-Programmierer diese Aufblähung vermeiden, müssen dann aber Dynamic Dispatch verwenden.

<h3><a href="#why-are-rusts-hashmaps-slow" name="Warum ist die HashMap in Rust so langsam?">
Warum ist die <code>HashMap</code> in Rust so langsam?
</a></h3>

Standardmäßig nutzt Rust's [`HashMap`][HashMap] den [SipHash](https://131002.net/siphash/) Algorithmus, welcher entworfen wurde, um [Kollisionsattacken auf Hash-Tabellen](http://programmingisterrible.com/post/40620375793/hash-table-denial-of-service-attacks-revisited) zu verhindern und dabei dennoch [für die häufigsten Anwendungsfälle gute Leistung](https://www.reddit.com/r/rust/comments/3hw9zf/rust_hasher_comparisons/cub4oh6) zu erzielen.

Obwohl SipHash [in vielen Fällen hohe Leistung vorweisen kann](http://cglab.ca/%7Eabeinges/blah/hash-rs/), ist der Algorithmus für Anwendungsfälle mit kurzen Schlüsseln wie Ganzzahlen merklich langsamer. Deshalb wird von Rust-Programmierern häufig niedrige Leistung bei der Verwendung einer [`HashMap`][HashMap] beobachtet. In solchen Fällen wird häufig der [FNV hasher](https://crates.io/crates/fnv) empfohlen, welcher aber nicht die Kollisionsresistenz von SipHash vorweisen kann.

<h3><a href="#why-is-there-no-integrated-benchmarking" name="Warum gibt es kein integriertes Benchmarking?">
Warum gibt es keine integrierte Benchmarking-Infrastruktur?
</a></h3>

Es gibt eine, welche aber nur im Nightly-Kanal verfügbar ist. Wir planen ein modulares System, welches integrierte Leistungstests ermöglicht. In der Zwischenzeit wird das System als [unstabil](https://github.com/rust-lang/rust/issues/29553) eingeschätzt.

<h3><a href="#does-rust-do-tail-call-optimization" name="Unterstützt Rust Tail Call Elimination?">
Unterstützt Rust Tail Call Elimination?
</a></h3>

Im Allgemeinen nicht. Tail-call Optimierung kann unter [bestimmten Vorraussetzungen](http://llvm.org/docs/CodeGenerator.html#sibling-call-optimization) erfolgen, aber ist [nicht gewährleistet](https://mail.mozilla.org/pipermail/rust-dev/2013-April/003557.html). Da die Optimisierung ein vielfach erwünschtes Sprachmerkmal ist, wurde das Schlüsselwort (`become`) dafür reserviert, wobei allerdings die technische Umsetzbarkeit noch nicht geklärt ist. Eine [vorgeschlagene Erweiterung](https://github.com/rust-lang/rfcs/pull/81), welche Tail-Call Optimisation ermöglichen würde, wurde vorgeschlagen, wurde aber zunächst verschoben.

<h3><a href="#does-rust-have-a-runtime" name="Hat Rust ein Laufzeitsystem?">
Hat Rust ein Laufzeitsystem?
</a></h3>

Nach üblichem Sprachgebrauch, wie er in Sprachen wie Java verwendet wird, hat Rust kein Laufzeitsystem. Teile der Standardbibliotheken könnte man als "Laufzeitsystem" bezeichnen, welches einen Heap, Backtraces, Unwinding, und Stack Guards anbietet. Eine relativ [kleine Menge Code zur Initialisierung](https://github.com/rust-lang/rust/blob/33916307780495fe311fe9c080b330d266f35bfb/src/libstd/rt.rs#L43) läuft vor der `main`-Funktion des Benutzers. Die Standardbibliotheken linken außerdem in die C-Standardbibliotheken, welche ebenfalls eine ähnliche [Laufzeitinitialisierung](http://www.embecosm.com/appnotes/ean9/html/ch05s02.html) vornehmen. Rust kann ohne die Standardbibliotheken kompiliert werden, dann ist die Laufzeitumgebung äquivalent zu der von C.

<h2 id="syntax">Syntax</h2>

<h3><a href="#why-curly-braces" name="Warum geschwungene Klammern?">
Warum geschwungene Klammern? Warum kann Rust's Syntax nicht mehr wie der von Haskell oder Python sein?
</a></h3>

Die Benutzung geschweifter Klammern ist eine Entwurfsentscheidung, welche eine Vielzahl von Programmiersprachen getroffen haben, und da Rust hier konsistent bleibt, ist es für in anderen Sprachen erfahrene Programmierer einfacher zu lernen.

Geschweifte Klammern ermöglichen dem Programmierer eine flexible Syntax und dem Kompilierer einen einfacheren Parser.

<h3><a href="#why-brackets-around-blocks" name="Warum Klammern um Blöcke?">
Ich kann die Klammern um <code>if</code>-Bedingungen weglassen, warum muss ich sie dann um einzeilige Blöcke setzen? Warum ist der C-Stil nicht erlaubt?
</a></h3>

Während C Klammerung um ein `if`-Statement, aber keine Klammern für einzeilige Blöcke erfordert, trifft Rust die genau entgegengesetzte Wahl. Das trennt die Bedingung klar vom Block und vermeidet die Gefahren der optionalen Klammern, welche zu leicht übersehbaren Fehlern wie Apple's [goto fail Bug](https://gotofail.com/) führen können.

<h3><a href="#why-no-literal-syntax-for-dictionaries" name="Warum kein literaler Syntax für Dictionaries?">
Warum kein literaler Syntax für Dictionaries?
</a></h3>

Rust's overall design preference is for limiting the size of the *language* while enabling powerful *libraries*. While Rust does provide initialization syntax for arrays and string literals, these are the only collection types built into the language. Other library-defined types, including the ubiquitous [`Vec`][Vec] collection type, use macros for initialization like the [`vec!`][VecMacro] macro.

This design choice of using Rust's macro facilities to initialize collections will likely be extended generically to other collections in the future, enabling simple initialization of not only [`HashMap`][HashMap] and [`Vec`][Vec], but also other collection types such as [`BTreeMap`][BTreeMap]. In the meantime, if you want a more convenient syntax for initializing collections, you can [create your own macro](https://stackoverflow.com/questions/27582739/how-do-i-create-a-hashmap-literal) to provide it.

<h3><a href="#when-should-i-use-an-implicit-return" name="when-should-i-use-an-implicit-return">
When should I use an implicit return?
</a></h3>

Rust is a very expression-oriented language, and "implicit returns" are part of that design. Constructs like `if`s, `match`es, and normal blocks are all expressions in Rust. For example, the following code checks if an [`i64`][i64] is odd, returning the result by simply yielding it as a value:

```rust
fn is_odd(x: i64) -> bool {
    if x % 2 != 0 { true } else { false }
}
```

Although it can be simplified even further like so:

```rust
fn is_odd(x: i64) -> bool {
    x % 2 != 0
}
```

In each example, the last line of the function is the return value of that function. It is important to note that if a function ends in a semicolon, its return type will be `()`, indicating no returned value. Implicit returns must omit the semicolon to work.

Explicit returns are only used if an implicit return is impossible because you are returning before the end of the function's body. While each of the above functions could have been written with a `return` keyword and semicolon, doing so would be unnecessarily verbose, and inconsistent with the conventions of Rust code.

<h3><a href="#why-arent-function-signatures-inferred" name="why-arent-function-signatures-inferred">
Why aren't function signatures inferred?
</a></h3>

In Rust, declarations tend to come with explicit types, while actual code has its types inferred. There are several reasons for this design:

- Mandatory declaration signatures help enforce interface stability at both the module and crate level.
- Signatures improve code comprehension for the programmer, eliminating the need for an IDE running an inference algorithm across an entire crate to be able to guess at a function's argument types; it's always explicit and nearby.
- Mechanically, it simplifies the inference algorithm, as inference only requires looking at one function at a time.

<h3><a href="#why-does-match-have-to-be-exhaustive" name="why-does-match-have-to-be-exhaustive">
Why does <code>match</code> have to be exhaustive?
</a></h3>

To aid in refactoring and clarity.

First, if every possibility is covered by the `match`, adding variants to the `enum` in the future will cause a compilation failure, rather than an error at runtime. This type of compiler assistance makes fearless refactoring possible in Rust.

Second, exhaustive checking makes the semantics of the default case explicit: in general, the only safe way to have a non-exhaustive `match` would be to panic the thread if nothing is matched. Early versions of Rust did not require `match` cases to be exhaustive and it was found to be a great source of bugs.

It is easy to ignore all unspecified cases by using the `_` wildcard:

```rust
match val.do_something() {
    Cat(a) => { /* ... */ }
    _      => { /* ... */ }
}
```

<h2 id="numerics">Numerics</h2>

<h3><a href="#which-type-of-float-should-i-use" name="which-type-of-float-should-i-use">
Which of <code>f32</code> and <code>f64</code> should I prefer for floating-point math?
</a></h3>

The choice of which to use is dependent on the purpose of the program.

If you are interested in the greatest degree of precision with your floating point numbers, then prefer [`f64`][f64]. If you are more interested in keeping the size of the value small or being maximally efficient, and are not concerned about the associated inaccuracy of having fewer bits per value, then [`f32`][f32] is better. Operations on [`f32`][f32] are usually faster, even on 64-bit hardware. As a common example, graphics programming typically uses [`f32`][f32] because it requires high performance, and 32-bit floats are sufficient for representing pixels on the screen.

If in doubt, choose [`f64`][f64] for the greater precision.

<h3><a href="#why-cant-i-compare-floats" name="why-cant-i-compare-floats">
Why can't I compare floats or use them as <code>HashMap</code> or <code>BTreeMap</code> keys?
</a></h3>

Floats can be compared with the `==`, `!=`, `<`, `<=`, `>`, and `>=` operators, and with the `partial_cmp()` function. `==` and `!=` are part of the [`PartialEq`][PartialEq] trait, while `<`, `<=`, `>`, `>=`, and `partial_cmp()` are part of the [`PartialOrd`][PartialOrd] trait.

Floats cannot be compared with the `cmp()` function, which is part of the [`Ord`][Ord] trait, as there is no total ordering for floats. Furthermore, there is no total equality relation for floats, and so they also do not implement the [`Eq`][Eq] trait.

There is no total ordering or equality on floats because the floating-point value [`NaN`](https://en.wikipedia.org/wiki/NaN) is not less than, greater than, or equal to any other floating-point value or itself.

Because floats do not implement [`Eq`][Eq] or [`Ord`][Ord], they may not be used in types whose trait bounds require those traits, such as [`BTreeMap`][BTreeMap] or [`HashMap`][HashMap]. This is important because these types *assume* their keys provide a total ordering or total equality relation, and will malfunction otherwise.

There [is a crate](https://crates.io/crates/ordered-float) that wraps [`f32`][f32] and [`f64`][f64] to provide [`Ord`][Ord] and [`Eq`][Eq] implementations, which may be useful in certain cases.

<h3><a href="#how-can-i-convert-between-numeric-types" name="how-can-i-convert-between-numeric-types">
How can I convert between numeric types?
</a></h3>

There are two ways: the `as` keyword, which does simple casting for primitive types, and the [`Into`][Into] and [`From`][From] traits, which are implemented for a number of type conversions (and which you can implement for your own types). The [`Into`][Into] and [`From`][From] traits are only implemented in cases where conversions are lossless, so for example, `f64::from(0f32)` will compile while `f32::from(0f64)` will not. On the other hand, `as` will convert between any two primitive types, truncating values as necessary.


<h3><a href="#why-doesnt-rust-have-increment-and-decrement-operators" name="why-doesnt-rust-have-increment-and-decrement-operators">
Why doesn't Rust have increment and decrement operators?
</a></h3>

Preincrement and postincrement (and the decrement equivalents), while convenient, are also fairly complex. They require knowledge of evaluation order, and often lead to subtle bugs and undefined behavior in C and C++. `x = x + 1` or `x += 1` is only slightly longer, but unambiguous.

<h2 id="strings">Strings</h2>

<h3><a href="#how-to-convert-string-or-vec-to-slice" name="how-to-convert-string-or-vec-to-slice">
How can I convert a <code>String</code> or <code>Vec&lt;T&gt;</code> to a slice (<code>&amp;str</code> and <code>&amp;[T]</code>)?
</a></h3>

Usually, you can pass a reference to a `String` or `Vec<T>` wherever a slice is expected.
Using [Deref coercions](https://doc.rust-lang.org/stable/book/deref-coercions.html), [`String`s][String] and [`Vec`s][Vec] will automatically coerce to their respective slices when passed by reference with `&` or `& mut`.

Methods implemented on `&str` and `&[T]` can be accessed directly on `String` and `Vec<T>`. For example, `some_string.char_at(0)` will work even though `char_at` is a method on `&str` and `some_string` is a `String`.

In some cases, such as generic code, it's necessary to convert manually. Manual conversions can be achieved using the slicing operator, like so: `&my_vec[..]`.

<h3><a href="#how-to-convert-between-str-and-string" name="how-to-convert-between-str-and-string">
How can I convert from <code>&amp;str</code> to <code>String</code> or the other way around?
</a></h3>

The [`to_string()`][to_string] method converts from a [`&str`][str] into a [`String`][String], and [`String`s][String] are automatically converted into [`&str`][str] when you borrow a reference to them. Both are demonstrated in the following example:

```rust
fn main() {
    let s = "Jane Doe".to_string();
    say_hello(&s);
}

fn say_hello(name: &str) {
    println!("Hello {}!", name);
}
```

<h3><a href="#what-are-the-differences-between-str-and-string" name="what-are-the-differences-between-str-and-string">
What are the differences between the two different string types?
</a></h3>

[`String`][String] is an owned buffer of UTF-8 bytes allocated on the heap. Mutable [`String`s][String] can be modified, growing their capacity as needed. [`&str`][str] is a fixed-capacity "view" into a [`String`][String] allocated elsewhere, commonly on the heap, in the case of slices dereferenced from [`String`s][String], or in static memory, in the case of string literals.

[`&str`][str] is a primitive type implemented by the Rust language, while [`String`][String] is implemented in the standard library.

<h3><a href="#how-do-i-do-o1-character-access-in-a-string" name="how-do-i-do-o1-character-access-in-a-string">
How do I do O(1) character access in a <code>String</code>?
</a></h3>

You cannot. At least not without a firm understanding of what you mean by "character", and preprocessing the string to find the index of the desired character.

Rust strings are UTF-8 encoded. A single visual character in UTF-8 is not necessarily a single byte as it would be in an ASCII-encoded string. Each byte is called a "code unit" (in UTF-16, code units are 2 bytes; in UTF-32 they are 4 bytes). "Code points" are composed of one or more code units, and combine in "grapheme clusters" which most closely approximate characters.

Thus, even though you may index on bytes in a UTF-8 string, you can't access the `i`th code point or grapheme cluster in constant time. However, if you know at which byte that desired code point or grapheme cluster begins, then you _can_ access it in constant time. Functions including [`str::find()`][str__find] and regex matches return byte indices, facilitating this sort of access.

<h3><a href="#why-are-strings-utf-8" name="why-are-strings-utf-8">
Why are strings UTF-8 by default?
</a></h3>

The [`str`][str] type is UTF-8 because we observe more text in the wild in this encoding – particularly in network transmissions, which are endian-agnostic – and we think it's best that the default treatment of I/O not involve having to recode codepoints in each direction.

This does mean that locating a particular Unicode codepoint inside a string is an O(n) operation, although if the starting byte index is already known then they can be accessed in O(1) as expected. On the one hand, this is clearly undesirable; on the other hand, this problem is full of trade-offs and we'd like to point out a few important qualifications:

Scanning a [`str`][str] for ASCII-range codepoints can still be done safely byte-at-a-time. If you use [`.as_bytes()`][str__as_bytes], pulling out a [`u8`][u8] costs only `O(1)` and produces a value that can be cast and compared to an ASCII-range [`char`][char]. So if you're (say) line-breaking on `'\n'`, byte-based treatment still works. UTF-8 was well-designed this way.

Most "character oriented" operations on text only work under very restricted language assumptions such as "ASCII-range codepoints only". Outside ASCII-range, you tend to have to use a complex (non-constant-time) algorithm for determining linguistic-unit (glyph, word, paragraph) boundaries anyway. We recommend using an "honest" linguistically-aware, Unicode-approved algorithm.

The [`char`][char] type is UTF-32. If you are sure you need to do a codepoint-at-a-time algorithm, it's trivial to write a `type wstr = [char]`, and unpack a [`str`][str] into it in a single pass, then work with the `wstr`. In other words: the fact that the language is not "decoding to UTF32 by default" shouldn't stop you from decoding (or re-encoding any other way) if you need to work with that encoding.

For a more in-depth explanation of why UTF-8 is usually preferable over UTF-16 or UTF-32, read the [UTF-8 Everywhere manifesto](http://utf8everywhere.org/).

<h3><a href="#what-string-type-should-i-use" name="what-string-type-should-i-use">
What string type should I use?
</a></h3>

Rust has four pairs of string types, [each serving a distinct purpose](http://www.suspectsemantics.com/blog/2016/03/27/string-types-in-rust/). In each pair, there is an "owned" string type, and a "slice" string type. The organization looks like this:

|               | "Slice" type | "Owned" type |
|:--------------|:-------------|:-------------|
| UTF-8         | `str`        | `String`     |
| OS-compatible | `OsStr`      | `OsString`   |
| C-compatible  | `CStr`       | `CString`    |
| System path   | `Path`       | `PathBuf`    |

Rust's different string types serve different purposes. `String` and `str` are UTF-8 encoded general-purpose strings. `OsString` and `OsStr` are encoded according to the current platform, and are used when interacting with the operating system. `CString` and `CStr` are the Rust equivalent of strings in C, and are used in FFI code, and `PathBuf` and `Path` are convenience wrappers around `OsString` and `OsStr`, providing methods specific to path manipulation.

<h3><a href="#why-are-there-multiple-types-of-strings" name="why-are-there-multiple-types-of-strings">
How can I write a function that accepts both <code>&str</code> and <code>String</code>?
</a></h3>

There are several options, depending on the needs of the function:

- If the function needs an owned string, but wants to accept any type of string, use an `Into<String>` bound.
- If the function needs a string slice, but wants to accept any type of string, use an `AsRef<str>` bound.
- If the function does not care about the string type, and wants to handle the two possibilities uniformly, use `Cow<str>` as the input type.

__Using `Into<String>`__

In this example, the function will accept both owned strings and string slices, either doing nothing or converting the input into an owned string within the function body. Note that the conversion needs to be done explicitly, and will not happen otherwise.

```rust
fn accepts_both<S: Into<String>>(s: S) {
    let s = s.into();   // This will convert s into a `String`.
    // ... the rest of the function
}
```

__Using `AsRef<str>`__

In this example, the function will accept both owned strings and string slices, either doing nothing or converting the input into a string slice. This can be done automatically by taking the input by reference, like so:

```rust
fn accepts_both<S: AsRef<str>>(s: &S) {
    // ... the body of the function
}
```

__Using `Cow<str>`__

In this example, the function takes in a `Cow<str>`, which is not a generic type but a container, containing either an owned string or string slice as needed.

```rust
fn accepts_cow(s: Cow<str>) {
    // ... the body of the function
}
```


<h2 id="collections">Collections</h2>

<h3><a href="#can-i-implement-linked-lists-in-rust" name="can-i-implement-linked-lists-in-rust">
Can I implement data structures like vectors and linked lists efficiently in Rust?
</a></h3>

If your reason for implementing these data structures is to use them for other programs, there's no need, as efficient implementations of these data structures are provided by the standard library.

If, however, [your reason is simply to learn](http://cglab.ca/~abeinges/blah/too-many-lists/book/), then you will likely need to dip into unsafe code. While these data structures _can_ be implemented entirely in safe Rust, the performance is likely to be worse than it would be with the use of unsafe code. The simple reason for this is that data structures like vectors and linked lists rely on pointer and memory operations that are disallowed in safe Rust.

For example, a doubly-linked list requires that there be two mutable references to each node, but this violates Rust's mutable reference aliasing rules. You can solve this using [`Weak<T>`][Weak], but the performance will be poorer than you likely want. With unsafe code you can bypass the mutable reference aliasing rule restriction, but must manually verify that your code introduces no memory safety violations.

<h3><a href="#how-can-i-iterate-over-a-collection-without-consuming-it" name="how-can-i-iterate-over-a-collection-without-consuming-it">
How can I iterate over a collection without moving/consuming it?
</a></h3>

The easiest way is by using the collection's [`IntoIterator`][IntoIterator] implementation. Here is an example for [`&Vec`][Vec]:

```rust
let v = vec![1,2,3,4,5];
for item in &v {
    print!("{} ", item);
}
println!("\nLength: {}", v.len());
```

Rust `for` loops call `into_iter()` (defined on the [`IntoIterator`][IntoIterator] trait) for whatever they're iterating over. Anything implementing the [`IntoIterator`][IntoIterator] trait may be looped over with a `for` loop. [`IntoIterator`][IntoIterator] is implemented for [`&Vec`][Vec] and [`&mut Vec`][Vec], causing the iterator from `into_iter()` to borrow the contents of the collection, rather than moving/consuming them. The same is true for other standard collections as well.

If a moving/consuming iterator is desired, write the `for` loop without `&` or `&mut` in the iteration.

If you need direct access to a borrowing iterator, you can usually get it by calling the `iter()` method.

<h3><a href="#why-do-i-need-to-type-the-array-size-in-the-array-declaration" name="why-do-i-need-to-type-the-array-size-in-the-array-declaration">
Why do I need to type the array size in the array declaration?
</a></h3>

You don't necessarily have to. If you're declaring an array directly, the size is inferred based on the number of elements. But if you're declaring a function that takes a fixed-size array, the compiler has to know how big that array will be.

One thing to note is that currently Rust doesn't offer generics over arrays of different size. If you'd like to accept a contiguous container of a variable number of values, use a [`Vec`][Vec] or slice (depending on whether you need ownership).

<h2 id="ownership">Ownership</h2>

<h3><a href="#how-can-i-implement-a-data-structure-that-contains-cycles" name="how-can-i-implement-a-data-structure-that-contains-cycles">
How can I implement a graph or other data structure that contains cycles?
</a></h3>

There are at least four options (discussed at length in [Too Many Linked Lists](http://cglab.ca/~abeinges/blah/too-many-lists/book/)):

- You can implement it using [`Rc`][Rc] and [`Weak`][Weak] to allow shared ownership of nodes,
although this approach pays the cost of memory management.
- You can implement it using `unsafe` code using raw pointers. This will be
more efficient, but bypasses Rust's safety guarantees.
- Using vectors and indices into those vectors. There are [several](http://smallcultfollowing.com/babysteps/blog/2015/04/06/modeling-graphs-in-rust-using-vector-indices/) [available](https://featherweightmusings.blogspot.com/2015/04/graphs-in-rust.html) examples and explanations of this approach.
- Using borrowed references with [`UnsafeCell`][UnsafeCell]. There are [explanations and code](https://github.com/nrc/r4cppp/blob/master/graphs/README.md#node-and-unsafecell) available for this approach.

<h3><a href="#how-can-i-define-a-struct-that-contains-a-reference-to-one-of-its-own-fields" name="how-can-i-define-a-struct-that-contains-a-reference-to-one-of-its-own-fields">
How can I define a struct that contains a reference to one of its own fields?
</a></h3>

It's possible, but useless to do so. The struct becomes permanently borrowed by itself and therefore can't be moved. Here is some code illustrating this:

```rust
use std::cell::Cell;

#[derive(Debug)]
struct Unmovable<'a> {
    x: u32,
    y: Cell<Option<&'a u32>>,
}


fn main() {
    let test = Unmovable { x: 42, y: Cell::new(None) };
    test.y.set(Some(&test.x));

    println!("{:?}", test);
}
```

<h3><a href="#what-is-the-difference-between-consuming-and-moving" name="what-is-the-difference-between-consuming-and-moving">
What is the difference between passing by value, consuming, moving, and transferring ownership?
</a></h3>

These are different terms for the same thing. In all cases, it means the value has been moved to another owner, and moved out of the possession of the original owner, who can no longer use it. If a type implements the `Copy` trait, the original owner's value won't be invalidated, and can still be used.

<h3><a href="#why-can-values-of-some-types-by-reused-while-others-are-consumed" name="why-can-values-of-some-types-by-reused-while-others-are-consumed">
Why can values of some types be used after passing them to a function, while reuse of values of other types results in an error?
</a></h3>

If a type implements the [`Copy`][Copy] trait, then it will be copied when passed to a function. All numeric types in Rust implement [`Copy`][Copy], but struct types do not implement [`Copy`][Copy] by default, so they are moved instead. This means that the struct can no longer be used elsewhere, unless it is moved back out of the function via the return.

<h3><a href="#how-do-you-deal-with-a-use-of-moved-value-error" name="how-do-you-deal-with-a-use-of-moved-value-error">
How do you deal with a "use of moved value" error?
</a></h3>

This error means that the value you're trying to use has been moved to a new owner. The first thing to check is whether the move in question was necessary: if it moved into a function, it may be possible to rewrite the function to use a reference, rather than moving. Otherwise if the type being moved implements [`Clone`][Clone], then calling `clone()` on it before moving will move a copy of it, leaving the original still available for further use. Note though that cloning a value should typically be the last resort since cloning can be expensive, causing further allocations.

If the moved value is of your own custom type, consider implementing [`Copy`][Copy] (for implicit copying, rather than moving) or [`Clone`][Clone] (explicit copying). [`Copy`][Copy] is most commonly implemented with `#[derive(Copy, Clone)]` ([`Copy`][Copy] requires [`Clone`][Clone]), and [`Clone`][Clone] with `#[derive(Clone)]`.

If none of these are possible, you may want to modify the function that acquired ownership to return ownership of the value when the function exits.

<h3><a href="#what-are-the-rules-for-different-self-types-in-methods" name="what-are-the-rules-for-different-self-types-in-methods">
What are the rules for using <code>self</code>, <code>&amp;self</code>, or <code>&amp;mut self</code> in a method declaration?
</a></h3>

- Use `self` when a function needs to consume the value
- Use `&self` when a function only needs a read-only reference to the value
- Use `&mut self` when a function needs to mutate the value without consuming it

<h3><a href="#how-can-i-understand-the-borrow-checker" name="how-can-i-understand-the-borrow-checker">
How can I understand the borrow checker?
</a></h3>

The borrow checker applies only a few rules, which can be found in the Rust book's [section on borrowing](https://doc.rust-lang.org/stable/book/references-and-borrowing.html#the-rules), when evaluating Rust code. These rules are:

> First, any borrow must last for a scope no greater than that of the owner. Second, you may have one or the other of these two kinds of borrows, but not both at the same time:
>
> - one or more references (&T) to a resource.
> - exactly one mutable reference (&mut T)

While the rules themselves are simple, following them consistently is not, particularly for those unaccustomed to reasoning about lifetimes and ownership.

The first step in understanding the borrow checker is reading the errors it produces. A lot of work has been put into making sure the borrow checker provides quality assistance in resolving the issues it identifies. When you encounter a borrow checker problem, the first step is to slowly and carefully read the error reported, and to only approach the code after you understand the error being described.

The second step is to become familiar with the ownership and mutability-related container types provided by the Rust standard library, including [`Cell`][Cell], [`RefCell`][RefCell], and [`Cow`][Cow]. These are useful and necessary tools for expressing certain ownership and mutability situations, and have been written to be of minimal performance cost.

The single most important part of understanding the borrow checker is practice. Rust's strong static analyses guarantees are strict and quite different from what many programmers have worked with before. It will take some time to become completely comfortable with everything.

If you find yourself struggling with the borrow checker, or running out of patience, always feel free to reach out to the [Rust community](community.html) for help.

<h3><a href="#when-is-rc-useful" name="when-is-rc-useful">
When is <code>Rc</code> useful?
</a></h3>

This is covered in the official documentation for [`Rc`][Rc], Rust's non-atomically reference-counted pointer type. In short, [`Rc`][Rc] and its thread-safe cousin [`Arc`][Arc] are useful to express shared ownership, and have the system automatically deallocate the associated memory when no one has access to it.

<h3><a href="#how-do-i-return-a-closure-from-a-function" name="how-do-i-return-a-closure-from-a-function">
How do I return a closure from a function?
</a></h3>

To return a closure from a function, it must be a "move closure", meaning that the closure is declared with the `move` keyword. As [explained in the Rust book](https://doc.rust-lang.org/book/closures.html#move-closures), this gives the closure its own copy of the captured variables, independent of its parent stack frame. Otherwise, returning a closure would be unsafe, as it would allow access to variables that are no longer valid; put another way: it would allow reading potentially invalid memory. The closure must also be wrapped in a [`Box`][Box], so that it is allocated on the heap. Read more about this [in the book](https://doc.rust-lang.org/book/closures.html#returning-closures).

<h3><a href="#what-are-deref-coercions" name="what-are-deref-coercions">
What is a deref coercion and how does it work?
</a></h3>

A [deref coercion](https://doc.rust-lang.org/book/deref-coercions.html) is a handy coercion
that automatically converts references to pointers (e.g., `&Rc<T>` or `&Box<T>`) into references
to their contents (e.g., `&T`). Deref coercions exist to make using Rust more ergonomic, and are implemented via the [`Deref`][Deref] trait.

A Deref implementation indicates that the implementing type may be converted into a target by a call to the `deref` method, which takes an immutable reference to the calling type and returns a reference (of the same lifetime) to the target type. The `*` prefix operator is shorthand for the `deref` method.

They're called "coercions" because of the following rule, quoted here [from the Rust book](https://doc.rust-lang.org/stable/book/deref-coercions.html):

> If you have a type `U`, and it implements `Deref<Target=T>`, values of `&U` will automatically coerce to a `&T`.

For example, if you have a `&Rc<String>`, it will coerce via this rule into a `&String`, which then coerces to a `&str` in the same way. So if a function takes a `&str` parameter, you can pass in a `&Rc<String>` directly, with all coercions handled automatically via the `Deref` trait.

The most common sorts of deref coercions are:

- `&Rc<T>` to `&T`
- `&Box<T>` to `&T`
- `&Arc<T>` to `&T`
- `&Vec<T>` to `&[T]`
- `&String` to `&str`

<h2 id="lifetimes">Lifetimes</h2>

<h3><a href="#why-lifetimes" name="why-lifetimes">
Why lifetimes?
</a></h3>

Lifetimes are Rust's answer to the question of memory safety. They allow Rust to ensure memory safety without the performance costs of garbage collection. They are based on a variety of academic work, which can be found in the [Rust book](https://doc.rust-lang.org/stable/book/bibliography.html#type-system).

<h3><a href="#why-is-the-lifetime-syntax-the-way-it-is" name="why-is-the-lifetime-syntax-the-way-it-is">
Why is the lifetime syntax the way it is?
</a></h3>

The `'a` syntax comes from the ML family of programming languages, where `'a` is used to indicate a generic type parameter. For Rust, the syntax had to be something that was unambiguous, noticeable, and fit nicely in a type declaration right alongside traits and references. Alternative syntaxes have been discussed, but no alternative syntax has been demonstrated to be clearly better.

<h3><a href="#how-do-i-return-a-borrow-to-something-i-created-from-a-function" name="how-do-i-return-a-borrow-to-something-i-created-from-a-function">
How do I return a borrow to something I created from a function?
</a></h3>

You need to ensure that the borrowed item will outlive the function. This can be done by binding the output lifetime to some input lifetime like so:

```rust
type Pool = TypedArena<Thing>;

// (the lifetime below is only written explicitly for
// expository purposes; it can be omitted via the
// elision rules described in a later FAQ entry)
fn create_borrowed<'a>(pool: &'a Pool,
                       x: i32,
                       y: i32) -> &'a Thing {
    pool.alloc(Thing { x: x, y: y })
}
```

An alternative is to eliminate the references entirely by returning an owning type like [`String`][String]:

```rust
fn happy_birthday(name: &str, age: i64) -> String {
    format!("Hello {}! You're {} years old!", name, age)
}
```

This approach is simpler, but often results in unnecessary allocations.

<h3><a href="#when-are-lifetimes-required-to-be-explicit" name="when-are-lifetimes-required-to-be-explicit">
Why do some references have lifetimes, like <code>&amp;'a T</code>, and some do not, like <code>&amp;T</code>?
</a></h3>

In fact, *all* reference types have a lifetime, but most of the time you do not have to write
it explicitly. The rules are as follows:

1. Within a function body, you never have to write a lifetime explicitly; the correct value
   should always be inferred.
2. Within a function *signature* (for example, in the types of its
   arguments, or its return type), you *may* have to write a lifetime
   explicitly. Lifetimes there use a simple defaulting scheme called
   ["lifetime elision"](https://doc.rust-lang.org/book/lifetimes.html#lifetime-elision),
   which consists of the following three rules:
  - Each elided lifetime in a function’s arguments becomes a distinct lifetime parameter.
  - If there is exactly one input lifetime, elided or not, that
    lifetime is assigned to all elided lifetimes in the return values
    of that function.
  - If there are multiple input lifetimes, but one of them is &self
    or &mut self, the lifetime of self is assigned to all elided
    output lifetimes.
3. Finally, in a `struct` or `enum` definition, all lifetimes must be explicitly declared.

If these rules result in compilation errors, the Rust compiler will provide an error message indicating the error caused, and suggesting a potential solution based on which step of the inference process caused the error.

<h3><a href="#how-can-rust-guarantee-no-null-pointers" name="how-can-rust-guarantee-no-null-pointers">
How can Rust guarantee "no null pointers" and "no dangling pointers"?
</a></h3>

The only way to construct a value of type `&Foo` or `&mut Foo` is to specify an existing value of type `Foo` that the reference points to. The reference "borrows" the original value for a given region of code (the lifetime of the reference), and the value being borrowed from cannot be moved or destroyed for the duration of the borrow.

<h3><a href="#how-do-i-express-the-absense-of-a-value-without-null" name="how-do-i-express-the-absense-of-a-value-without-null">
How do I express the absence of a value without <code>null</code>?
</a></h3>

You can do that with the [`Option`][Option] type, which can either be `Some(T)` or `None`. `Some(T)` indicates that a value of type `T` is contained within, while `None` indicates the absence of a value.

<h2 id="generics">Generics</h2>

<h3><a href="#what-is-monomorphisation" name="what-is-monomorphisation">
What is "monomorphisation"?
</a></h3>

Monomorphisation specializes each use of a generic function (or structure) with specific instance,
based on the parameter types of calls to that function (or uses of the structure).

During monomorphisation a new copy of the generic function is translated for each unique set of types the function is instantiated with. This is the same strategy used by C++. It results in fast code that is specialized for every call-site and statically dispatched, with the tradeoff that functions instantiated with many different types can cause "code bloat", where multiple function instances result in larger binaries than would be created with other translation strategies.

Functions that accept [trait objects](https://doc.rust-lang.org/book/trait-objects.html) instead of type parameters do not undergo monomorphisation. Instead, methods on the trait objects are dispatched dynamically at runtime.

<h3><a href="#whats-the-difference-between-a-function-and-a-closure-that-doesnt-capture" name="whats-the-difference-between-a-function-and-a-closure-that-doesnt-capture">
What's the difference between a function and a closure that doesn't capture any variables?
</a></h3>

Functions and closures are operationally equivalent, but have different runtime representations due to their differing implementations.

Functions are a built-in primitive of the language, while closures are essentially syntactic sugar for one of three traits: [`Fn`][Fn], [`FnMut`][FnMut], and [`FnOnce`][FnOnce]. When you make a closure, the Rust compiler automatically creates a struct implementing the appropriate trait of those three and containing the captured environment variables as members, and makes it so the struct can be called as a function. Bare functions can not capture an environment.

The big difference between these traits is how they take the `self` parameter. [`Fn`][Fn] takes `&self`, [`FnMut`][FnMut] takes `&mut self`, and [`FnOnce`][FnOnce] takes `self`.

Even if a closure does not capture any environment variables, it is represented at runtime as two pointers, the same as any other closure.

<h3><a href="#what-are-higher-kinded-types" name="what-are-higher-kinded-types">
What are higher-kinded types, why would I want them, and why doesn't Rust have them?
</a></h3>

Higher-kinded types are types with unfilled parameters. Type constructors, like [`Vec`][Vec], [`Result`][Result], and [`HashMap`][HashMap] are all examples of higher-kinded types: each requires some additional type parameters in order to actually denote a specific type, like `Vec<u32>`. Support for higher-kinded types means these "incomplete" types may be used anywhere "complete" types can be used, including as generics for functions.

Any complete type, like [`i32`][i32], [`bool`][bool], or [`char`][char] is of kind `*` (this notation comes from the field of type theory). A type with one parameter, like [`Vec<T>`][Vec] is of kind `* -> *`, meaning that [`Vec<T>`][Vec] takes in a complete type like [`i32`][i32] and returns a complete type `Vec<i32>`. A type with three parameters, like [`HashMap<K, V, S>`][HashMap] is of kind `* -> * -> * -> *`, and takes in three complete types (like [`i32`][i32], [`String`][String], and [`RandomState`][RandomState]) to produce a new complete type `HashMap<i32, String, RandomState>`.

In addition to these examples, type constructors can take *lifetime* arguments, which we'll denote as `Lt`. For example, `slice::Iter` has kind `Lt -> * -> *`, because it must be instantiated like `Iter<'a, u32>`.

The lack of support for higher-kinded types makes it difficult to write certain kinds of generic code. It's particularly problematic for abstracting over concepts like iterators, since iterators are often parameterized over a lifetime at least. That in turn has prevented the creation of traits abstracting over Rust's collections.

Another common example is concepts like functors or monads, both of which are type constructors, rather than single types.

Rust doesn't currently have support for higher-kinded types because it hasn't been a priority compared to other improvements we want to make. Since the design is a major, cross-cutting change, we also want to approach it carefully. But there's no inherent reason for the current lack of support.

<h3><a href="#what-do-named-type-parameters-in-generic-types-mean" name="what-do-named-type-parameters-in-generic-types-mean">
What do named type parameters like <code>&lt;T=Foo&gt;</code> in generic types mean?
</a></h3>

These are called [associated types](https://doc.rust-lang.org/stable/book/associated-types.html), and they allow for the expression of trait bounds that can't be expressed with a `where` clause. For example, a generic bound `X: Bar<T=Foo>` means "`X` must implement the trait `Bar`, and in that implementation of `Bar`, `X` must choose `Foo` for `Bar`'s associated type, `T`." Examples of where such a constraint cannot be expressed via a `where` clause include trait objects like `Box<Bar<T=Foo>>`.

Associated types exist because generics often involve families of types, where one type determines all of the others in a family. For example, a trait for graphs might have as its `Self` type the graph itself, and have associated types for nodes and for edges. Each graph type uniquely determines the associated types. Using associated types makes it much more concise to work with these families of types, and also provides better type inference in many cases.

<h3><a href="#how-do-i-overload-operators" name="how-do-i-overload-operators">
Can I overload operators? Which ones and how?
</a></h3>

You can provide custom implementations for a variety of operators using their associated traits: [`Add`][Add] for `+`, [`Mul`][Mul] for `*`, and so on. It looks like this:

```rust
use std::ops::Add;

struct Foo;

impl Add for Foo {
    type Output = Foo;
    fn add(self, rhs: Foo) -> Self::Output {
        println!("Adding!");
        self
    }
}
```

The following operators can be overloaded:

| Operation            | Trait                          |
|:---------------------|:-------------------------------|
| `+`                  | [`Add`][Add]                   |
| `+=`                 | [`AddAssign`][AddAssign]       |
| `binary -`           | [`Sub`][Sub]                   |
| `-=`                 | [`SubAssign`][SubAssign]       |
| `*`                  | [`Mul`][Mul]                   |
| `*=`                 | [`MulAssign`][MulAssign]       |
| `/`                  | [`Div`][Div]                   |
| `/=`                 | [`DivAssign`][DivAssign]       |
| `unary -`            | [`Neg`][Neg]                   |
| `%`                  | [`Rem`][Rem]                   |
| `%=`                 | [`RemAssign`][RemAssign]       |
| `&`                  | [`BitAnd`][BitAnd]             |
| <code>&#124;</code>  | [`BitOr`][BitOr]               |
| <code>&#124;</code>= | [`BitOrAssign`][BitOrAssign]   |
| `^`                  | [`BitXor`][BitXor]             |
| `^=`                 | [`BitXorAssign`][BitXorAssign] |
| `!`                  | [`Not`][Not]                   |
| `<<`                 | [`Shl`][Shl]                   |
| `<<=`                | [`ShlAssign`][ShlAssign]       |
| `>>`                 | [`Shr`][Shr]                   |
| `>>=`                | [`ShrAssign`][ShrAssign]       |
| `*`                  | [`Deref`][Deref]               |
| `mut *`              | [`DerefMut`][DerefMut]         |
| `[]`                 | [`Index`][Index]               |
| `mut []`             | [`IndexMut`][IndexMut]         |

<h3><a href="#why-the-split-between-eq-partialeq-and-ord-partialord" name="why-the-split-between-eq-partialeq-and-ord-partialord">
Why the split between <code>Eq</code>/<code>PartialEq</code> and <code>Ord</code>/<code>PartialOrd</code>?
</a></h3>

There are some types in Rust whose values are only partially ordered, or have only partial equality. Partial ordering means that there may be values of the given type that are neither less than nor greater than each other. Partial equality means that there may be values of the given type that are not equal to themselves.

Floating point types ([`f32`][f32] and [`f64`][f64]) are good examples of each. Any floating point type may have the value `NaN` (meaning "not a number"). `NaN` is not equal to itself (`NaN == NaN` is false), and not less than or greater than any other floating point value. As such, both [`f32`][f32] and [`f64`][f64] implement [`PartialOrd`][PartialOrd] and [`PartialEq`][PartialEq] but not [`Ord`][Ord] and not [`Eq`][Eq].

As explained in [the earlier question on floats](#why-cant-i-compare-floats), these distinctions are important because some collections rely on total orderings/equality in order to give correct results.

<h2 id="input-output">Input / Output</h2>

<h3><a href="#how-do-i-read-a-file-into-a-string" name="how-do-i-read-a-file-into-a-string">
How do I read a file into a <code>String</code>?
</a></h3>

Using the [`read_to_string()`][read__read_to_string] method, which is defined on the [`Read`][Read] trait in [`std::io`][std-io].

```rust
use std::io::Read;
use std::fs::File;

fn read_file(path: &str) -> Result<String, std::io::Error> {
    let mut f = try!(File::open(path));
    let mut s = String::new();
    try!(f.read_to_string(&mut s));  // `s` contains the contents of "foo.txt"
    Ok(s)
}

fn main() {
    match read_file("foo.txt") {
        Ok(_) => println!("Got file contents!"),
        Err(err) => println!("Getting file contents failed with error: {}", err)
    };
}
```

<h3><a href="#how-do-i-read-file-input-efficiently" name="how-do-i-read-file-input-efficiently">
How do I read file input efficiently?
</a></h3>

The [`File`][File] type implements the [`Read`][Read] trait, which has a variety of functions for reading and writing data, including [`read()`][read__read], [`read_to_end()`][read__read_to_end], [`bytes()`][read__bytes], [`chars()`][read__chars], and [`take()`][read__take]. Each of these functions reads a certain amount of input from a given file. [`read()`][read__read] reads as much input as the underlying system will provide in a single call. [`read_to_end()`][read__read_to_end] reads the entire buffer into a vector, allocating as much space as is needed. [`bytes()`][read__bytes] and [`chars()`][read__chars] allow you to iterate over the bytes and characters of the file, respectively. Finally, [`take()`][read__take] allows you to read up to an arbitrary number of bytes from the file. Collectively, these should allow you to efficiently read in any data you need.

For buffered reads, use the [`BufReader`][BufReader] struct, which helps to reduce the number of system calls when reading.

<h3><a href="#how-do-i-do-asynchronous-input-output-in-rust" name="how-do-i-do-asynchronous-input-output-in-rust">
How do I do asynchronous input / output in Rust?
</a></h3>

There are several libraries providing asynchronous input / output in Rust, including [mio](https://github.com/carllerche/mio), [tokio](https://github.com/tokio-rs/tokio-core), [mioco](https://github.com/dpc/mioco), [coio-rs](https://github.com/zonyitoo/coio-rs), and [rotor](https://github.com/tailhook/rotor).

<h3><a href="#how-do-i-get-command-line-arguments" name="how-do-i-get-command-line-arguments">
How do I get command line arguments in Rust?
</a></h3>

The easiest way is to use [`Args`][Args], which provides an iterator over the input arguments.

If you're looking for something more powerful, there are a [number of options on crates.io](https://crates.io/keywords/argument).

<h2 id="error-handling">Error Handling</h2>

<h3><a href="#why-doesnt-rust-have-exceptions" name="why-doesnt-rust-have-exceptions">
Why doesn't Rust have exceptions?
</a></h3>

Exceptions complicate understanding of control-flow, they express validity/invalidity outside of the type system, and they interoperate poorly with multithreaded code (a major focus of Rust).

Rust prefers a type-based approach to error handling, which is [covered at length in the book](https://doc.rust-lang.org/stable/book/error-handling.html). This fits more nicely with Rust's control flow, concurrency, and everything else.

<h3><a href="#whats-the-deal-with-unwrap" name="whats-the-deal-with-unwrap">
What's the deal with <code>unwrap()</code> everywhere?
</a></h3>

`unwrap()` is a function that extracts the value inside an [`Option`][Option] or [`Result`][Result] and panics if no value is present.

`unwrap()` shouldn't be your default way to handle errors you expect to arise, such as incorrect user input. In production code, it should be treated like an assertion that the value is non-empty, which will crash the program if violated.

It's also useful for quick prototypes where you don't want to handle an error yet, or blog posts where error handling would distract from the main point.

<h3><a href="#why-do-i-get-errors-with-try" name="why-do-i-get-errors-with-try">
Why do I get an error when I try to run example code that uses the <code>try!</code> macro?
</a></h3>

It's probably an issue with the function's return type. The [`try!`][TryMacro] macro either extracts the value from a [`Result`][Result], or returns early with the error [`Result`][Result] is carrying. This means that [`try`][TryMacro] only works for functions that return [`Result`][Result] themselves, where the `Err`-constructed type implements `From::from(err)`. In particular, this means that the [`try!`][TryMacro] macro cannot work inside the `main` function.

<h3><a href="#error-handling-without-result" name="error-handling-without-result">
Is there an easier way to do error handling than having <code>Result</code>s everywhere?
</a></h3>

If you're looking for a way to avoid handling [`Result`s][Result] in other people's code, there's always [`unwrap()`][unwrap], but it's probably not what you want. [`Result`][Result] is an indicator that some computation may or may not complete successfully. Requiring you to handle these failures explicitly is one of the ways that Rust encourages robustness. Rust provides tools like the [`try!` macro][TryMacro] to make handling failures ergonomic.

If you really don't want to handle an error, use [`unwrap()`][unwrap], but know that doing so means that the code panics on failure, which usually results in a shutting down the process.

<h2 id="concurrency">Concurrency</h2>

<h3><a href="#can-i-use-static-values-across-threads-without-an-unsafe-block" name="can-i-use-static-values-across-threads-without-an-unsafe-block">
Can I use static values across threads without an <code>unsafe</code> block?
</a></h3>

Mutation is safe if it's synchronized. Mutating a static [`Mutex`][Mutex] (lazily initialized via the [lazy-static](https://crates.io/crates/lazy_static/) crate) does not require an `unsafe` block, nor does mutating a static [`AtomicUsize`][AtomicUsize] (which can be initialized without lazy_static).

More generally, if a type implements [`Sync`][Sync] and does not implement [`Drop`][Drop], it [can be used in a `static`](https://doc.rust-lang.org/book/const-and-static.html#static).

<h2 id="macros">Macros</h2>

<h3><a href="#can-i-write-a-macro-to-generate-identifiers" name="can-i-write-a-macro-to-generate-identifiers">
Can I write a macro to generate identifiers?
</a></h3>

Not currently. Rust macros are ["hygienic macros"](https://en.wikipedia.org/wiki/Hygienic_macro), which intentionally avoid capturing or creating identifiers that may cause unexpected collisions with other identifiers. Their capabilities are significantly different than the style of macros commonly associated with the C preprocessor. Macro invocations can only appear in places where they are explicitly supported: items, method declarations, statements, expressions, and patterns. Here, "method declarations" means a blank space where a method can be put. They can't be used to complete a partial method declaration. By the same logic, they can't be used to complete a partial variable declaration.

<h2 id="debugging">Debugging and Tooling</h2>

<h3><a href="#how-do-i-debug-rust-programs" name="how-do-i-debug-rust-programs">
How do I debug Rust programs?
</a></h3>

Rust programs can be debugged using [gdb](https://sourceware.org/gdb/current/onlinedocs/gdb/) or [lldb](http://lldb.llvm.org/tutorial.html), the same as C and C++. In fact, every Rust installation comes with one or both of rust-gdb and rust-lldb (depending on platform support). These are wrappers over gdb and lldb with Rust pretty-printing enabled.

<h3><a href="#how-do-i-locate-a-panic" name="how-do-i-locate-a-panic">
<code>rustc</code> said a panic occurred in standard library code. How do I locate the mistake in my code?
</a></h3>

This error is usually caused by [`unwrap()`ing][unwrap] a `None` or `Err` in client code. Enabling backtraces by setting the environment variable `RUST_BACKTRACE=1` helps with getting more information. Compiling in debug mode (the default for `cargo build`) is also helpful. Using a debugger like the provided `rust-gdb` or `rust-lldb` is also helpful.

<h3><a href="#what-ide-should-i-use" name="what-ide-should-i-use">
What IDE should I use?
</a></h3>

There are a number of options for development environment with Rust, all of which are detailed on the official [IDE support page](https://forge.rust-lang.org/ides.html).

<h3><a href="#wheres-rustfmt" name="wheres-rustfmt">
<code>gofmt</code> is great. Where's <code>rustfmt</code>?
</a></h3>

`rustfmt` is [right here](https://github.com/rust-lang-nursery/rustfmt), and is being actively developed to make reading Rust code as easy and predictable as possible.

<h2 id="low-level">Low-Level</h2>

<h3><a href="#how-do-i-memcpy-bytes" name="how-do-i-memcpy-bytes">
How do I <code>memcpy</code> bytes?
</a></h3>

If you want to clone an existing slice safely, you can use [`clone_from_slice`][clone_from_slice].

To copy potentially overlapping bytes, use [`copy`][copy]. To copy nonoverlapping bytes, use [`copy_nonoverlapping`][copy_nonoverlapping]. Both of these functions are `unsafe`, as both can be used to subvert the language's safety guarantees. Take care when using them.

<h3><a href="#does-rust-work-without-the-standard-library" name="does-rust-work-without-the-standard-library">
Can Rust function reasonably without the standard library?
</a></h3>

Absolutely. Rust programs can be set to not load the standard library using the `#![no_std]` attribute. With this attribute set, you can continue to use the Rust core library, which is nothing but the platform-agnostic primitives. As such, it doesn't include IO, concurrency, heap allocation, etc.

<h3><a href="#can-i-write-an-operating-system-in-rust" name="can-i-write-an-operating-system-in-rust">
Can I write an operating system in Rust?
</a></h3>

Yes! In fact there are [several projects underway doing just that](http://wiki.osdev.org/Rust).

<h3><a href="#how-can-i-write-endian-independent-values" name="how-can-i-write-endian-independent-values">
How can I read or write numeric types like <code>i32</code> or <code>f64</code> in big-endian or little-endian format in a file or other byte stream?
</a></h3>

You should check out the [byteorder crate](http://burntsushi.net/rustdoc/byteorder/), which provides utilities for exactly that.

<h3><a href="#does-rust-guarantee-data-layout" name="does-rust-guarantee-data-layout">
Does Rust guarantee a specific data layout?
</a></h3>

Not by default. In the general case, `enum` and `struct` layouts are undefined. This allows the compiler to potentially do optimizations like re-using padding for the discriminant, compacting variants of nested `enum`s, reordering fields to remove padding, etc. `enums` which carry no data ("C-like") are eligible to have a defined representation. Such `enums` are easily distinguished in that they are simply a list of names that carry no data:

```rust
enum CLike {
    A,
    B = 32,
    C = 34,
    D
}
```

The `#[repr(C)]` attribute can be applied to such `enums` to give them the same representation they would have in equivalent C code. This allows using Rust `enum`s in FFI code where C `enum`s are also used, for most use cases. The attribute can also be applied to `struct`s to get the same layout as a C `struct` would.

<h2 id="cross-platform">Cross-Platform</h2>

<!--
### How do I build a Windows binary that doesn't display the console window?

TODO: Write this answer.
-->

<!--
### How do I make the console-less binary not crash on panic!?

TODO: Write this answer.
-->

<h3><a href="#how-do-i-express-platform-specific-behavior" name="how-do-i-express-platform-specific-behavior">
What's the idiomatic way to express platform-specific behavior in Rust?
</a></h3>

Platform-specific behavior can be expressed using [conditional compilation attributes](https://doc.rust-lang.org/reference/attributes.html#conditional-compilation) such as `target_os`, `target_family`, `target_endian`, etc.

<h3><a href="#can-rust-be-used-for-android-ios-programs" name="can-rust-be-used-for-android-ios-programs">
Can Rust be used for Android/iOS programming?
</a></h3>

Yes it can! There are already examples of using Rust for both [Android](https://github.com/tomaka/android-rs-glue) and [iOS](https://www.bignerdranch.com/blog/building-an-ios-app-in-rust-part-1/). It does require a bit of work to set up, but Rust functions fine on both platforms.

<h3><a href="#can-i-run-my-rust-program-in-a-web-browser" name="can-i-run-my-rust-program-in-a-web-browser">
Can I run my Rust program in a web browser?
</a></h3>

Possibly. Rust has [experimental support][wasm] for both [asm.js] and [WebAssembly].

[wasm]: https://davidmcneil.gitbooks.io/the-rusty-web/
[asm.js]: http://asmjs.org/
[WebAssembly]: http://webassembly.org/

<h3><a href="#how-do-i-cross-compile-rust" name="how-do-i-cross-compile-rust">
How do I cross-compile in Rust?
</a></h3>

Cross compilation is possible in Rust, but it requires [a bit of work](https://github.com/japaric/rust-cross/blob/master/README.md) to set up. Every Rust compiler is a cross-compiler, but libraries need to be cross-compiled for the target platform.

Rust does distribute [copies of the standard library](https://static.rust-lang.org/dist/index.html) for each of the supported platforms, which are contained in the `rust-std-*` files for each of the build directories found on the distribution page, but there are not yet automated ways to install them.

<h2 id="modules-and-crates">Module und Crates</h2>

<h3><a href="#what-is-the-relationship-between-a-module-and-a-crate" name="what-is-the-relationship-between-a-module-and-a-crate">
Wie verhalten sich Crates und Module zueinander?
</a></h3>

- Ein Crate ist eine Übersetzungseinheit, also die kleinste Einheit, auf der der Rust-Compiler arbeiten kann.
- Ein Modul ist eine (möglicherweise verschachtelte) Organisationseinheit innerhalb eines Crates.
- Ein Crate enthält ein implizites, unbenanntes Modul auf Wurzelebene.
- Rekursive Definitionen können sich über mehrere Module erstrecken, nicht aber über mehrere Crates.

<h3><a href="#why-cant-the-rust-compiler-find-a-library-im-using" name="why-cant-the-rust-compiler-find-a-library-im-using">
Warum kann der Rust-Compiler die Bibliothek nicht finden, die ich eingebunden habe?
</a></h3>

Hier gibt es eine Reihe von Möglichkeiten, aber ein häufiger Grund ist, dass die `use`-Deklaration nicht relativ zur Crate-Wurzel angegben wurde. Versuche deine Deklarationen so zu schreiben, dass sie den gleichen Pfad haben wie wenn sie in der Wurzeldatei deines Projekts importiert würden.

Es gibt außerdem noch die Schlüsselwörter `self` und `super`, die es erlauben, Pfade relativ zum akutellen oder zum Elternmodul anzugeben.

Mehr Informationen findest du im Kapitel ["Crates and Modules"](https://doc.rust-lang.org/stable/book/crates-and-modules.html) des Rust Book.

<h3><a href="#why-do-i-have-to-declare-modules-with-mod" name="why-do-i-have-to-declare-modules-with-mod">
Warum muss ich Moduldateien mit <code>mod</code> im Crate deklarieren, anstatt sie einfach mit <code>use</code> einzubinden?
</a></h3>

Module können in Rust auf zwei Arten deklariert werden: Direkt im Code, oder in einer separaten Datei. Hier ein Beispiel beider Varianten:

```rust
// In main.rs
mod hello {
    pub fn f() {
        println!("Hallo!");
    }
}

fn main() {
    hello::f();
}
```

```rust
// In main.rs
mod hello;

fn main() {
    hello::f();
}

// In hello.rs
pub fn f() {
    println!("Hallo!");
}
```

Im ersten Beispiel wird das Modul in der Datei definiert, in der es auch benutzt wird. Im zweiten Beispiel weist die Moduldeklaration den Compiler darauf hin, die Definition aus `hello.rs` oder `hello/mod.rs` zu laden.

`mod` deklariert also ein neues Modul, wogegen sich `use` auf ein anderswo existierendes Modul bezieht und dessen Inhalte in den aktuellen Gültigkeitsberich übernimmt.

<h3><a href="#how-do-i-configure-cargo-to-use-a-proxy" name="how-do-i-configure-cargo-to-use-a-proxy">
Wie kann ich Cargo dazu bringen, einen Proxy zu verwenden?
</a></h3>

Wie in der [Cargo-Dokumentation](http://doc.crates.io/config.html) (englisch) beschrieben, kann ein Proxyserver eingerichtet werden, indem die `proxy`-Variable in der `[http]`-Sektion der Konfigurationsdatei gesetzt wird.

<h3><a href="#why-cant-the-compile-find-method-implementations" name="why-cant-the-compile-find-method-implementations">
Warum kann der Compiler eine Implementierung nicht finden, obwohl ich das Modul des Typs bereits importiert habe?
</a></h3>

Für Methoden, die über einen Trait definiert werden, muss die Trait-Deklaration explizit mit importiert werden. Es genügt also nicht, das Modul zu importieren, in dem der Trait für den Struct imlplementiert wird, sondern der Trait selbst muss zusätzlich eingebunden werden.

<h3><a href="#why-cant-the-compiler-infer-use-statements" name="why-cant-the-compiler-infer-use-statements">
Warum kann der Compiler <code>use</code>-Deklarationen nicht einfach herleiten?
</a></h3>

Er könnte wahrscheinlich, aber das willst du wahrscheinlich gar nicht. In einfachen Fällen könnte der Compiler wohl das korrekte Modul finden, indem er nach passenden Deklarationen zu einem Bezeichner sucht, das klappt im Allgemeinen aber nicht. Jede Entscheidungsregel bei Namenskonflikten würde in einigen Fällen für Überraschung sorgen, und Rust zieht es vor die Herkunft von Symbolen explizit zu benennen.

So könnte der Compiler etwa festlegen, dass bei einem Namenskonflikt das erste importierte Modul Vorrang hat. Definieren also die beiden Module `foo` und `bar` jeweils den Bezeichner `baz`, `foo` ist aber das erste registrierte Modul, so würde der Compiler ein `use foo::baz;` einfügen.

```rust
mod foo;
mod bar;

// use foo::baz  // wird vom Compiler eingefügt

fn main() {
  baz();
}
```

Wenn du sicher weißt, dass das passieren wird, kann das einige wenige Tastenanschläge einsparen. Dieser Gewinn wird aber mit deutlich höheren Wahrscheinlichkeit an überraschenden Fehlermeldungen erkauft, falls mit `baz()` eigentlich `bar::baz` gemeint war. Auch reduziert diese Logik die Lesbarkeit des Codes, weil ein Funktionsaufruf plötzlich von der Importreihenfolge abhängt. Diesen Trade-Off wollen wir nicht eingehen.

Zukünftig könnten jedoch IDEs die Auflösung von Deklarationen erleichtern: Hilfestellung beim Finden des richtigen Imports, aber explizite Modulpfade im Code.

<!--
### How do I package and archive crates from [https://crates.io](https://crates.io)?

TODO: Write this answer.
-->

<h3><a href="#how-do-i-do-dynamic-rust-library-loading" name="how-do-i-do-dynamic-rust-library-loading">
Wie kann ich in Rust dynamische Bibliotheken laden?
</a></h3>

Dynamische Bibliotheken können mit [libloading](https://crates.io/crates/libloading) importiert werden, das ein plattformübergreifendes System für dynamisches Linken bereitstellt.

<h3><a href="#why-doesnt-crates-io-have-namespaces" name="why-doesnt-crates-io-have-namespaces">
Warum hat crates.io keine Namensräume?
</a></h3>

Übersetzung der [offiziellen Erklärung](https://internals.rust-lang.org/t/crates-io-package-policies/1041) zum Design von [https://crates.io](https://crates.io):

> Im ersten Monat nach der Veröffentlichung von crates.io wurden wir von mehreren Nutzern nach der Möglichkeit gefragt, [Pakete mit Namensräumen](https://github.com/rust-lang/crates.io/issues/58) einzuführen.<br><br>
>
> Auch wenn Namensräume es Autoren einfacher macht, generische Namen für Pakete zu wählen, erhöhen sie die Komplexität, mit der Crates im Rust-Code und in der Kommunikation zwischen Entwicklern referenziert werden. Auf den ersten Blick erlauben sie mehreren Entwicklern, Namen wie `http` zu wählen, das sorgt aber nur dafür, dass diese Pakete als `wycats' http` oder `reem's http` bekannt werden, was keine wirkliche Verbesserung gegenüber längeren Namen wie `wycats-http` oder `reem-http` bringt.<br><br>
>
> Es hat sich herausgestellt, dass Entwickler in Ökosystemen ohne Namensräume dazu tendieren, kreativere Namen (wie `nokogiri` statt `tenderlove's libxml2`) zu wählen. Diese Namen sind meist kurz und gut zu merken, gerade aufgrund der fehlenden Hierarchie. Das macht es einfacher, unmissverständlich über Pakete zu sprechen und erschafft spannende Markennamen. Auch haben wir den Erfolg von Umgebungen mit zigtausenden Paketen wie NPM und RubyGems gesehen, die wunderbar mit einem einheitlichen Namensraum zurechtkommen.<br><br>
>
> Kurz gesagt sind wir nicht der Meinung, dass das das Cargo-Ökosystem davon profitieren würde, wenn Piston einen Namen wie `bvssvni/game-engine` statt dem einfach zu merkenden `piston` bekommen hätte (mit der Möglichkeit, dass ein Anderer Entwickler `wycats/game-engine` veröffentlicht).
>
> Da Namensräume auf verschiedene Arten strikt komplexer ist und sie bei bedarf später hinzugefügt werden können, sollten sie irgendwann nötig werden, werden wir vorerst bei einem gemeinsamen Namensraum bleiben.<br><br>

<h2 id="libraries">Bibliotheken</h2>

<h3><a href="#how-can-i-make-an-http-request" name="how-can-i-make-an-http-request">
Wie kann ich eine HTTP-Anfrage absetzen?
</a></h3>

Die Standardbibliothek stellt keine HTTP-Implementierung zur Verfüguing, deshalb musst du dafür einen externen Crate bemühen.
[reqwest](http://docs.rs/reqwest) ist einer der einfachsten.  Er setzt auf [hyper](https://github.com/hyperium/hyper) auf und ist in Rust geschrieben,
es gibt jedoch [eine Vielzahl an Alternativen](https://crates.io/keywords/http).
Der [curl](https://docs.rs/curl)-Crate ist beispielsweise weit verbreitet und bildet eine Anbindung an die curl-Biblitothek.

<h3><a href="#how-can-i-write-a-gui-application" name="how-can-i-write-a-gui-application">
Wie kann ich in Rust eine grafische Benutzeroberfläche schreiben?
</a></h3>

Es gibt eine große Auswahl von [GUI-Frameworks](https://github.com/kud1ing/awesome-rust#gui) für Rust.

<h3><a href="#how-can-i-parse-json-xml" name="how-can-i-parse-json-xml">
Wie kann ich JSON oder XML parsen?
</a></h3>

[Serde](https://github.com/serde-rs/serde) ist die empfohlene Bibliothek für (De-)Serialisierung von Rust-Datenstrukturen von und in eine Reihe von Datenformaten.

<h3><a href="#is-there-a-standard-2d-vector-crate" name="is-there-a-standard-2d-vector-crate">
Gibt es einen Standard-Crate für 2D-Vektorgrafik?
</a></h3>

Noch nicht! Lust einen zu bauen?

<h3><a href="#how-do-i-write-an-opengl-app" name="how-do-i-write-an-opengl-app">
Wie kann ich in Rust ein OpenGL-Programm schreiben?
</a></h3>

[Glium](https://github.com/tomaka/glium) ist die größte Bibliothek für OpenGL-Programmierung in Rust. [GLFW](https://github.com/bjz/glfw-rs) ist auch eine solide Option.

<h3><a href="#can-i-write-a-video-game-in-rust" name="can-i-write-a-video-game-in-rust">
Kann ich in Rust ein Computerspiel schreiben?
</a></h3>

Ja! Die wichtigste Bibliothek für Spieleprogrammierung in Rust ist [Piston](http://www.piston.rs/), und es gibt sowohl ein [Subreddit für Spieleprogrammierung in Rust](https://www.reddit.com/r/rust_gamedev/), als auch einen IRC-Kanal (`#rust-gamedev` im [Mozilla-IRC](https://wiki.mozilla.org/IRC)) zu diesem Thema.

<h2 id="design-patterns">Design Patterns</h2>

<h3><a href="#is-rust-object-oriented" name="is-rust-object-oriented">
Ist Rust objektorientiert?
</a></h3>

Rust ist eine Mehrparadigmensprache. Viele Konzepte aus OOP-Sprachen können nach Rust übernommen werden, aber nicht alle, und nicht immer mit dem gewohnten Abstraktionsmechanismus.

<h3><a href="#how-do-i-map-object-oriented-concepts-to-rust" name="how-do-i-map-object-oriented-concepts-to-rust">
Wie kann ich objektorientierte Konzepte in Rust abbilden?
</a></h3>

Kommt darauf an. Es _gibt_ Möglichkeiten, um objektorientierte Konzepte wie [Mehrfachvererbung](https://www.reddit.com/r/rust/comments/2sryuw/ideaquestion_about_multiple_inheritence/) nach Rust zu übersetzen, das Ergebnis kann aber aufgrund der nicht objektorientierten Natur von Rust deutlich von seinem Äquivalent in einer OOP-Sprache abweichen.

<h3><a href="#how-do-i-configure-a-struct-with-optional-parameters" name="how-do-i-configure-a-struct-with-optional-parameters">
Wie kann ich einen Struct mit optionalen Parametern konfigurieren?
</a></h3>

Die einfachste Möglichkeit ist es, den Typ [`Option`][Option] als Parameter für Funktionen wie `new` zu verwenden. Alternativ kannst du das [Builder Pattern](https://aturon.github.io/ownership/builders.html) implementieren, mit dem einzelne Attribute durch Funktionsaufrufe an einen Builder belegt werden, bevor der eigentliche Struct konstruiert wird.

<h3><a href="#how-do-i-do-global-variables" name="how-do-i-do-global-variables">
Wie benutze ich globale Variablen in Rust?
</a></h3>

Globale Konstanten werden mit dem Schlüsselwort `const` deklariert, globale Variablen mit `static`. Beachte, dass das Verändern einer `static mut`-Variablen `unsafe`-Code erfordert, da es Data Races erlaubt, deren Absenz von Safe Rust garantiert wird. Ein wichtiger Unterschied zwischen `const` und `static` ist, dass auf `static`-Variablen Referenzen gebildet werden können - `const`-Werte haben keine definierte Speicheradresse. Für weitere Informationen zum Thema `const` vs. `static` sei auf das [Rust Book](https://doc.rust-lang.org/book/const-and-static.html) verwiesen.

<h3><a href="#how-can-i-set-compile-time-constants-that-are-defined-procedurally" name="how-can-i-set-compile-time-constants-that-are-defined-procedurally">
Wie kann ich Compilezeit-Konstanten definieren, die prozedural berechnet werden?
</a></h3>

Rust hat momentan nur eingeschränkte Unterstützung für Compilezeit-Konstanten. Du kannst Werte eines primitiven Typs mittels `const`-Deklarationen definieren (ähnlich zu `static`, aber unveränderlich und ohne eine feste Speicheradresse). Funktionen können ebenfalls `const` sein.

Konstanten, die sich mit diesen Mechanismen nicht beschreiben lassen, können mit dem [`lazy-static`](https://github.com/rust-lang-nursery/lazy-static.rs)-Crate erzeugt werden, der Compilezeit-Berechnung durch Auswertung bei der ersten Benutzung einer globalen Variablen emuliert.

<h3><a href="#can-i-run-code-before-main" name="can-i-run-code-before-main">
Kann ich vor Bereten der `main`-Funktion Initialisierungscode ausführen?
</a></h3>

Rust kennt keine Programmausführung vor `main`. Am nächsten kommt dem Konzept der [`lazy-static`](https://github.com/Kimundi/lazy-static.rs)-Crate, der dieses Verhalten nachbildet, indem globale Variablen bei ihrer ersten Benutzung initialisiert werden.

<!--

This answer needs significant work. Let's revise after the initial posting. --aturon

<h3><a href="#why-doesnt-rust-have-inheritance" name="why-doesnt-rust-have-inheritance">
Why doesn't Rust have inheritance?
</a></h3>

There are two meanings for the word "inheritance": _subtyping_, and _interface sharing_. Both purposes are already handled by traits.

For the first, subtyping exists for polymorphism, which traits already provide.

For the second, interface sharing is handled via trait methods, which define a collection of related functions that must be implemented for any implementation of the trait.

Rust has consistently worked to avoid having features with overlapping purposes, preferring to keep features orthogonal. For this reason, and given that the two major purposes are already handled by traits, Rust has opted not to include inheritance.

-->

<h3><a href="#does-rust-allow-non-constant-expression-values-for-globals" name="does-rust-allow-non-constant-expression-values-for-globals">
Erlaubt Rust Werte für globale Variablen, die keine Compilezeit-Konstanten sind?
</a></h3>

Nein. Globale Variablen können keine nicht-compilezeit-konstanten Konstruktoren und überhaupt keine Destruktoren besitzen. Statische Konstruktoren sind unerwünscht, da bei gegenseitigen Abhängigkeiten eine Initialisierungsreihenfolge nicht ohne weiteres garantiert werden kann. Codeausführung vor Beginn der `main`-Funktion wird weithin als Misfeature gesehen, weswegen es in Rust nicht umgesetzt ist.

Das [C++ FQA](http://yosefk.com/c++fqa/ctors.html#fqa-10.12) hat einen Eintrag zum "static initialization order fiasco", und [Eric Lipperts Blog](https://ericlippert.com/2013/02/06/static-constructors-part-one/) schreibt über die Herausforderungen, die das Feature in C# mit sich gebracht hat.

Nicht-konstante Initialisierer in globalen Variablen können mit dem [lazy-static](https://crates.io/crates/lazy_static/) nachgebildet werden.

<h2 id="other-languages">Andere Sprachen</h2>

<h3><a href="#how-can-i-use-static-fields" name="how-can-i-use-static-fields">
Wie kann ich ein C-Konstrukt wie <code>struct X { static int X; }</code> in Rust implementieren?
</a></h3>

Rust kennt keine `static`-Attribute wie im obigen Programmausschnitt. Stattdessen kannst du eine `static`-Variable auf Modulebene deklarieren, die nur im umgebenden Modul sichtbar ist.

<h3><a href="#how-can-i-convert-a-c-style-enum-to-an-integer" name="how-can-i-convert-a-c-style-enum-to-an-integer">
Wie kann ich einen C-ähnlichen Enum in einen Integer konvertieren und umgekehrt?
</a></h3>

Ein Enum kann mit einem `as`-Cast in einen Integer überführt werden, wie etwa `e as i64` (wobei `e` ein Enum ist). 

Die Gegenrichtung kann mit einem `match`-Statement erreicht werden, das Zahlenwerte auf Enum-Werte abbildet.

<h3><a href="#why-do-rust-programs-have-larger-binary-sizes-than-C-programs" name="why-do-rust-programs-have-larger-binary-sizes-than-C-programs">
Warum erzeugen Rust-Programme größere Binaries als C?
</a></h3>

Mehrere Faktoren tragen dazu bei, dass Rust-Programme standardmäßig größere Binaries erzeugen als funktionell äquivalente C-Programme. Grundsätzlich optimiert Rust die Performance komplexer Anwendungen, nicht die Größe kleiner Beispielprogramme.

__Monomorphisierung__

Rust monomorphisiert seine Generics, was bedeutet, dass eine generische Funktion oder ein generischer Typ für jeden konkreten Typ, mit dem er instanziiert wird, neu übersetzt wird. Das ist ählich zum Verhalten von Templates in C++. Zum Beispiel werden im folgenden Programm

```rust
fn foo<T>(t: T) {
    // ... tu irgendwas
}

fn main() {
    foo(10);       // i32
    foo("hello");  // &str
}
```

zwei unabhängige Versionen von `foo` im fertigen Programm auftauchen, jeweils für `i32` und `&str` spezialisiert. Das erlaubt effiziente frühe Bindung der generischen Funktion, sorgt aber für größere Binaries.

__Debug-Symbole__

Rust-Programme beinhalten auch im Release-Modus einige Debug-Symbole. Diese ermöglichen Backtraces bei Panics und können mit `strip` oder einem ähnlichen Tool aus dem Binary entfernt werden. Der Release-Modus in Cargo ist zum Optimierungslevel 3 in rustc äquivalent. [Mittlerweile](https://github.com/rust-lang/rust/pull/32386) kennt Rust eine alternative Optimierungsstrategie (Level `s` oder `z`),  mit der der Compiler versucht, die Größe statt der Performance des Programms zu optimieren.

__Jemalloc__

Rust benutzt standardmäßig jemalloc als Allokator, was die erzeugten Binaries etwas vergrößert. Jemalloc bietet einen konsistentere Allokation mit günstigerer Performance als viele systemeigenen Allokatoren. In Zukunft wird es auch einfacher sein, [benutzerdefinierte Allokatoren](https://github.com/rust-lang/rust/issues/32838) in Rust einzubinden.

__Link-Time Optimization__

Rust benutzt standardmäßig keine Link-Time-Optimization, kann aber so eingerichtet werden. Das erhöht das Optimierungspotential des Rust-Compilers und kann einen kleinen Effekt auf die Größe der Binaries haben. Dieser Effekt wird vor allem in Kombination mit den oben genannten Optimierungsstrategien sichtbar.

__Standardbibliothek__

Die Standardbibliothek von Rust beinhaltet libbacktrace und libunwind, die in manchen Programmen unerwünscht sein können. Mit dem Crate-Attribut `#![no_std]` können ohne diese Bibliotheken kleinere Binaries erzeugt werden, die aber üblicherweise wesentliche Änderungen am Code nach sich ziehen. Rust-Code, der ohne die Standardbibliothek geschrieben wurde, ist funktionell äquivalentem C-Code ähnlich.

Als Beispiel liest das folgende C-Programm einen Namen ein und begrüßt den Benutzer mit diesem Namen.

```c
#include <stdio.h>

int main(void) {
    printf("Wie heißt du?\n");
    char input[100] = {0};
    scanf("%s", input);
    printf("Hallo %s!\n", input);
    return 0;
}
```

In Rust würde man dieses Programm womöglich wie folgt schreiben:

```rust
use std::io;

fn main() {
    println!("Wie heißt du?");
    let mut input = String::new();
    io::stdin().read_line(&mut input).unwrap();
    println!("Hallo {}!", input);
}
```

Dieses Programm wird übersetzt ein größeres Binary produzieren und mehr Speicher in Anspruch nehmen als das C-Programm. Es ist aber nicht wirklich gleichwertig zum obigen C-Code. Das äquivalente Rust-Programm würde eher so ausehen:

```rust
#![feature(lang_items)]
#![feature(libc)]
#![feature(no_std)]
#![feature(start)]
#![no_std]

extern crate libc;

extern "C" {
    fn printf(fmt: *const u8, ...) -> i32;
    fn scanf(fmt: *const u8, ...) -> i32;
}

#[start]
fn start(_argc: isize, _argv: *const *const u8) -> isize {
    unsafe {
        printf(b"Wie heißt du?\n\0".as_ptr());
        let mut input = [0u8; 100];
        scanf(b"%s\0".as_ptr(), &mut input);
        printf(b"Hallo %s!\n\0".as_ptr(), &input);
        0
    }
}

#[lang="eh_personality"] extern fn eh_personality() {}
#[lang="panic_fmt"] fn panic_fmt() -> ! { loop {} }
#[lang="stack_exhausted"] extern fn stack_exhausted() {}
```

Dieser Code sollte in seinem Speicherverbrauch grob der C-Version entsprechen. Diese Reduktion wird mit zusätzlicher Komplexität und dem Fehlen statischer Garantien erkauft, die Rust üblicherweise gewährt (und die hier mit dem Schlüsselwort `unsafe` umgangen wurden).

<h3><a href="#why-no-stable-abi" name="why-no-stable-abi">
Warum hat Rust keine stabile ABI wie C, und warum muss ich Symbole mit extern annotieren?
</a></h3>

Das Festlegen einer ABI ist eine große Entscheidung, die zukünftige Änderungen an der Sprache behindern könnte. Da Rust erst im Mai 2015 Version 1.0 erreicht hat, ist es noch zu früh, sich an dieser Stelle festzulegen. Das bedeutet nicht, dass es nie eine stabile ABI geben wird (auch wenn C++ es viele Jahre ohne Spezifikation einer ABI geschafft hat).

Committing to an ABI is a big decision that can limit potentially advantageous language changes in the future. Given that Rust only hit 1.0 in May of 2015, it is still too early to make a commitment as big as a stable ABI. This does not mean that one won't happen in the future, though. (Though C++ has managed to go for many years without specifying a stable ABI.)

The `extern` keyword allows Rust to use specific ABI's, such as the well-defined C ABI, for interop with other languages.

<h3><a href="#can-rust-code-call-c-code" name="can-rust-code-call-c-code">
Kann Rust-Code C-Code aufrufen?
</a></h3>

Ja. Rust wurde so entworfen, dass C-Code genauso effizient aufgerufen kann wie aus C++.

<h3><a href="#can-c-code-call-rust-code" name="can-c-code-call-rust-code">
Can C code call Rust code?
</a></h3>

Yes. The Rust code has to be exposed via an `extern` declaration, which makes it C-ABI compatible. Such a function can be passed to C code as a function pointer or, if given the `#[no_mangle]` attribute to disable symbol mangling, can be called directly from C code.

<h3><a href="#why-rust-vs-cxx" name="why-rust-vs-cxx">
Ich kann bereits perfektes C++ schreiben. Welche Vorteile bietet mir Rust?
</a></h3>

Modernes C++ implementiert viele Features, die das Schreiben sicheren und korrekten Codes weniger Fehleranfällig macht. Es ist jedoch immer noch sehr einfach, Speicherfehler zu verursachen. Die C++-Hauptentwickler arbeiten daran die Prävalenz dieser Problematik zu verringern, die Sprache lässt aber durch ihre lange Geschichte und die notwendige Rückwärtskompatibilität nur eingeschränkt Änderungen zu.

Rust wurde vom ersten Tag an mit dem Ziel entworfen, eine sichere Systemprogrammiersprache zu sein. Sie ist damit nicht von historischen Entscheidungen belastet, die das Entwickeln sicheren Codes in C++ so kompliziert machen. In C++ wird Sicherheit durch strenge Selbstdisziplin erreicht und kann leicht verletzt werden. In Rust ist Sicherheit die Vorgabe. Die Sprache eröffnet so die Möglichkeit, mit weniger erfahrenen Entwiklern zusammenzuarbeiten, ohne den Code wieder und wieder auf Sicherheitslücken prüfen zu müssen.

<h3><a href="#how-to-get-cxx-style-template-specialization" name="how-to-get-cxx-style-template-specialization">
Wie lässt sich die Templatespezialisierung aus C++ in Rust umsetzen?
</a></h3>

Rust hat zur Zeit noch kein Äquivalent zu Templatespezialisierung, daran [wird jedoch gearbeitet](https://github.com/rust-lang/rfcs/pull/1210). Ähnliche Effekte können aber mittels [Assoziierter Typen](https://doc.rust-lang.org/stable/book/associated-types.html) erzielt werden.

<h3><a href="#how-does-ownership-relate-to-cxx-move-semantics" name="how-does-ownership-relate-to-cxx-move-semantics">
Was hat das Ownership-System von Rust mit Move Semantics aus C++ zu tun?
</a></h3>

Die zugrundeliegenden Konzepte sind ähnlich, in der Praxis funktionieren die beiden Systeme jedoch grundsätzlich verschieden. In beiden Fällen fungiert das Verschieben (Move) eines Werts als Möglichkeit, den Besitz zugrundeliegender Ressourcen zu übertragen. So überträgt der Move eines Strings etwa den Stringpuffer, anstatt ihn zu kopieren.

In Rust ist Ownership Transfer das Standardverhalten. So wird eine Funktion, die einen `String` als Argument nimmt, den Besitz am übergebenen String-Wert übernehmen:

```rust
fn process(s: String) { }

fn caller() {
    let s = String::from("Hello, world!");
    process(s); // Überträgt den Besitz von `s` an `process`
    process(s); // Fehler: `caller` besitzt `s` an dieser Stelle nicht mehr
}
```

Wie im Codebeispiel oben zu sehen, überträgt der erste Aufruf an `process` den Besitz an der Variablen `s`. Der Compiler führt über den Besitz von Werten Buch, sodass der zweite Aufruf an `process` einen Fehler zur Folge hat - ein gültiges Programm darf den Besitz eines Werts nicht zweimal aufgeben. Rust wird das Verschieben eines Werts auch verhindern, solange noch eine aktive Referenz darauf existiert.

C++ verfolgt einen anderen Ansatz. In C++ werden Werte per Vorgabe kopiert, in dem ihr Kopierkonstruktor aufgerufen wird. Es ist allerdings möglich, Funktionen zu deklarieren, die ihre Argumente als "rvalue-Referenz", wie etwa `string&&` übernehmen. Dies deutet darauf hin, dass die aufgerufene Funktion den Besitz an Ressourcen des Werts übernimmt. Der Aufrufer muss dazu entweder einen temporären Wert übergeben oder einen gebundenen Wert explizit mit `std::move` verschieben. Das obige Beispiel würde in C++ etwa wie folgt ausssehen:

```
void process(string&& s) { }

void caller() {
    string s("Hello, world!");
    process(std::move(s));
    process(std::move(s));
}
```

C++-Compiler müssen über Ownership nicht Buch führen, sodass der obige Code ohne Warnungen oder Fehler übersetzt. In C++ bleibt der Besitz der Variablen `s` weiterhin bei `caller` (nicht aber der interne Puffer des Strings), sodass trotzdem der Destruktor von `s` ausgeführt wird, sobald `caller` zurückkehrt. In Rust wird `drop` dagegen nur durch den neuen Besitzer des Werts aufgerufen. 

<h3><a href="#how-to-interoperate-with-cxx" name="how-to-interoperate-with-cxx">
Wie kann ich aus Rust C++-Funktionen aufrufen und umgekehrt?
</a></h3>

Rust und C++ können C als gemeinsame Schnittstelle benutzen. Sowohl Rust als auch C++ besitzen ein [Foreign Function Interface](https://doc.rust-lang.org/book/ffi.html) nach C über das sie miteinander kommunizieren können. Falls das Schreiben von C-Bindings zu langwierig wird, kannst du jederzeit auf [rust-bindgen](https://github.com/servo/rust-bindgen) zurückgreifen, ein Tool, das dir hilft automatisch funktionierende C-Bindings für Rust zu bauen.

<h3><a href="#does-rust-have-cxx-style-constructors" name="does-rust-have-cxx-style-constructors">
Hat Rust Konstruktoren, wie sie aus C++ bekannt sind?
</a></h3>

Nein. Funktionen erfüllen den gleichen Zweck wie Konstruktoren, ohne die Sprachkomplexität zu erhöhen. Der übliche Name für eine Konstrukorfunktion in Rust ist `new()`, dabei handelt es sich aber lediglich um eine Namenskonvention. `new()` ist tatsächlich eine Funktion wie jede andere. Hier ein Beispiel:

```rust
struct Foo {
    a: i32,
    b: f64,
    c: bool,
}

impl Foo {
    fn new() -> Foo {
        Foo {
            a: 0,
            b: 0.0,
            c: false,
        }
    }
}
```

<h3><a href="#does-rustCopy-K-have-copy-constructors" name="does-rust-have-copy-constructors">
Hat Rust Kopierkonstruktoren?
</a></h3>

Nicht direkt. Typen, die den `Copy`-Trait implementieren, führen eine C-artige, "flache Kopie" ohne zusätzliche Arbeit oder Funktionsaufrufe durch. Das entspricht dem Konzept der *trivially copyable types* aus C++. Es ist nicht möglich, `Copy` mit abweichendem Verhalten zu implementieren. Dazu dient der `Clone`-Trait, dessen Funktionalität durch einen expliziten Aufruf an die `clone`-Methode angesprochen wird. Die benutzerdefininerte Kopieroperation wird absichtlich explizit gehalten um die zugrundeliegende Komplexität und potentiell teure Operationen sichtbar zu machen.

<h3><a href="#does-rust-have-move-constructors" name="does-rust-have-move-constructors">
Hat Rust Move-Konstruktoren?
</a></h3>

Nein. Die Werte aller Typen werden Byte für Byte via `memcpy` verschoben. Das macht das Schreiben generischen `unsafe`-Codes deutlich einfacher, da das Zuweisen, Übergeben und Zurückgeben eines Werts nie Seiteneffekte wie Unwinding zur Folge haben kann.

<h3><a href="#compare-go-and-rust" name="compare-go-and-rust">
Was haben Go und Rust gemeinsam, und wo unterscheiden sich die Sprachen?
</a></h3>

Rust und Go haben grundsätzlich verschiendene Designziele. Alle Unterschiede aufzuzählen wäre zu umfangreich, im Folgenden werden einige der wichtigsten genannt.

- Rust arbeitet auf einer niedrigeren Ebene als Go. So setzt Rust im Gegensaz zu Go beispielsweise keinen Garbage Collector voraus. Allgemein bietet Rust ähnlich viel Kontrolle über das Verhalten eines Programms wie C oder C++.
- Der Fokus von Rust liegt darin, Sicherheit und Effizienz zu gewährleisten, gleichzeitig aber für High-Level-Abstraktionen zugänglich zu sein. Go konzentriert sich daruaf, eine kleine, einfache Sprache zu sein, die schnell kompiliert und gut mit einer großen Auswahl an Tools zusammenzuarbeitet.
- Rust hat im Gegensatz zu Go gute Unterstützung für Generics.
- Rust ist stark von der Welt der Funktionalprogrammierung beeinflusst, was sich etwa im Typsystem äußert, das die Typklassen aus Haskell in der Form von Traits übernimmt. Go hat ein einfacheres Typsystem, das mit Interfaces einfache generische Programmierung ermöglicht.

<h3><a href="#how-do-rust-traits-compare-to-haskell-typeclasses" name="how-do-rust-traits-compare-to-haskell-typeclasses">
Wie lassen sich Traits in Rust mit den Typklassen von Haskell vergleichen?
</a></h3>

Rust-Traits sind ähnlich, aber weniger mächtig als Haskell-Typklassen, da Rust keine typen höherer Ordnung unterstützt. Assoziierte Typen in Rust entsprechen Typfamilien in Haskell.

Einige spezifische Unterschiede zwischen Haskell und Rust:

- Rust-Traits haben einen impliziten ersten Parameter `Self`. `trait Bar` in Rust entspicht damit `class Bar self` in Haskell, und `trait Bar<Foo>` entspricht `class Bar foo self`.
- "Supertraits" oder "Superklassen-Constraints" werden in Rust `trait Sub: Super` geschrieben, in Haskell `class Super self => Sub self`.
- Rust erlaubt keine verwaisten Instanzen (orphan instances), d.h. Trait-Implementierungen, die weder im Modul des Traits noch im Modul des Typs liegen. Haskell erlaubt dies, was zu abweichenden Kohärenzregeln führt.
- Die Auflösung von `impl`-Blöcken berücksichtigt die relevanten `where`-Klauseln, um zwischen `impl`-Instanzen zu wählen oder Überlappungen festzustellen. Haskell berücksichtigt dabei nur die Bedingungen der `instance`-Deklaration und vernachlässigt Einschränkungen, die an anderen Stellen angegeben wurden.
- Eine Teilmenge der Traits in Rust ([Object Safe Traits](https://github.com/rust-lang/rfcs/blob/master/text/0255-object-safety.md)) können für späte Bindung mittels Traitobjekten benutzt werden. Das selbe ist in Haskell mit dem `ExistentialQuantification`-Feature von GHC verfügbar.

<h2 id="documentation">Dokumentation</h2>

<h3><a href="#why-are-so-many-rust-answers-on-stackoverflow-wrong" name="why-are-so-many-rust-answers-on-stackoverflow-wrong">
Warum gibt es so viele falsche Antworten zu Rust auf Stack Overflow?
</a></h3>

Rust hatte bis zur Veröffentlichung von Version 1.0 im Mai 2015 eine lange Entwicklungsgeschichte hinter sich. Währenddessen hat sich die Sprache signifikant geändert, und einige Antworten auf Stack Overflow beziehen sich auf Sprach- und Bibliothekskonstrukte, die sich mittlerweile geändert haben.

Mit der Zeit werden immer mehr Antworten für die aktuelle Version von Rust enstehen, sodass der Anteil der veralteten Antworten abnehmen wird.

<h3><a href="#where-do-i-report-issues-in-the-rust-documentation" name="where-do-i-report-issues-in-the-rust-documentation">
Wie kann ich die Entwickler auf Fehler in der Rust-Dokumentation hinweisen?
</a></h3>

Probleme in der Dokumentation kannst du im Rust Compiler [Issue Tracker](https://github.com/rust-lang/rust/issues) melden. Lies vorab unsere [Richtlinien](https://github.com/rust-lang/rust/blob/master/CONTRIBUTING.md#writing-documentation), um effektiv mitwirken zu können.

<h3><a href="#how-do-i-view-rustdoc-documentation-for-a-library-my-project-depends-on" name="how-do-i-view-rustdoc-documentation-for-a-library-my-project-depends-on">
Wo finde ich die rustdoc-Dokumentation für eine Bibliothek, von der mein Projekt abhängt?
</a></h3>

Wenn du `cargo doc` aufrufst, um Dokumentation für dein Projekt zu generieren, wird automatisch auch die Dokumentation für aktiven Versionen aller Abhängigkeiten erzeugt. Diese landet im Unterverzeichnis `target/doc` deines Projekts. Um die Dokumentation nach der Erstellung zu öffnen, kannst du `cargo doc --open` benutzen oder einfach direkt `target/doc/index.html` in deinem Browser öffnen.

[Vec]: https://doc.rust-lang.org/stable/std/vec/struct.Vec.html
[HashMap]: https://doc.rust-lang.org/stable/std/collections/struct.HashMap.html
[Into]: https://doc.rust-lang.org/stable/std/convert/trait.Into.html
[From]: https://doc.rust-lang.org/stable/std/convert/trait.From.html
[Eq]: https://doc.rust-lang.org/stable/std/cmp/trait.Eq.html
[PartialEq]: https://doc.rust-lang.org/stable/std/cmp/trait.PartialEq.html
[Ord]: https://doc.rust-lang.org/stable/std/cmp/trait.Ord.html
[PartialOrd]: https://doc.rust-lang.org/stable/std/cmp/trait.PartialOrd.html
[f32]: https://doc.rust-lang.org/stable/std/primitive.f32.html
[f64]: https://doc.rust-lang.org/stable/std/primitive.f64.html
[i32]: https://doc.rust-lang.org/stable/std/primitive.i32.html
[i64]: https://doc.rust-lang.org/stable/std/primitive.i64.html
[bool]: https://doc.rust-lang.org/stable/std/primitive.bool.html
[Hash]: https://doc.rust-lang.org/stable/std/hash/trait.Hash.html
[BTreeMap]: https://doc.rust-lang.org/stable/std/collections/struct.BTreeMap.html
[VecMacro]: https://doc.rust-lang.org/stable/std/macro.vec!.html
[String]: https://doc.rust-lang.org/stable/std/string/struct.String.html
[to_string]: https://doc.rust-lang.org/stable/std/string/trait.ToString.html#tymethod.to_string
[str]: https://doc.rust-lang.org/stable/std/primitive.str.html
[str__find]: https://doc.rust-lang.org/stable/std/primitive.str.html#method.find
[str__as_bytes]: https://doc.rust-lang.org/stable/std/primitive.str.html#method.as_bytes
[u8]: https://doc.rust-lang.org/stable/std/primitive.u8.html
[char]: https://doc.rust-lang.org/stable/std/primitive.char.html
[Weak]: https://doc.rust-lang.org/stable/std/rc/struct.Weak.html
[IntoIterator]: https://doc.rust-lang.org/stable/std/iter/trait.IntoIterator.html
[Rc]: https://doc.rust-lang.org/stable/std/rc/struct.Rc.html
[UnsafeCell]: https://doc.rust-lang.org/stable/std/cell/struct.UnsafeCell.html
[Copy]: https://doc.rust-lang.org/stable/std/marker/trait.Copy.html
[Clone]: https://doc.rust-lang.org/stable/std/clone/trait.Clone.html
[Cell]: https://doc.rust-lang.org/stable/std/cell/struct.Cell.html
[RefCell]: https://doc.rust-lang.org/stable/std/cell/struct.RefCell.html
[Cow]: https://doc.rust-lang.org/stable/std/borrow/enum.Cow.html
[Deref]: https://doc.rust-lang.org/stable/std/ops/trait.Deref.html
[Arc]: https://doc.rust-lang.org/stable/std/sync/struct.Arc.html
[Box]: https://doc.rust-lang.org/stable/std/boxed/struct.Box.html
[Option]: https://doc.rust-lang.org/stable/std/option/enum.Option.html
[Fn]: https://doc.rust-lang.org/stable/std/ops/trait.Fn.html
[FnMut]: https://doc.rust-lang.org/stable/std/ops/trait.FnMut.html
[FnOnce]: https://doc.rust-lang.org/stable/std/ops/trait.FnOnce.html
[Result]: https://doc.rust-lang.org/stable/std/result/enum.Result.html
[RandomState]: https://doc.rust-lang.org/stable/std/collections/hash_map/struct.RandomState.html
[Add]: https://doc.rust-lang.org/stable/std/ops/trait.Add.html
[AddAssign]: https://doc.rust-lang.org/stable/std/ops/trait.AddAssign.html
[Sub]: https://doc.rust-lang.org/stable/std/ops/trait.Sub.html
[SubAssign]: https://doc.rust-lang.org/stable/std/ops/trait.SubAssign.html
[Mul]: https://doc.rust-lang.org/stable/std/ops/trait.Mul.html
[MulAssign]: https://doc.rust-lang.org/stable/std/ops/trait.MulAssign.html
[Div]: https://doc.rust-lang.org/stable/std/ops/trait.Div.html
[DivAssign]: https://doc.rust-lang.org/stable/std/ops/trait.DivAssign.html
[Neg]: https://doc.rust-lang.org/stable/std/ops/trait.Neg.html
[Rem]: https://doc.rust-lang.org/stable/std/ops/trait.Rem.html
[RemAssign]: https://doc.rust-lang.org/stable/std/ops/trait.RemAssign.html
[BitAnd]: https://doc.rust-lang.org/stable/std/ops/trait.BitAnd.html
[BitAndAssign]: https://doc.rust-lang.org/stable/std/ops/trait.BitAndAssign.html
[BitOr]: https://doc.rust-lang.org/stable/std/ops/trait.BitOr.html
[BitOrAssign]: https://doc.rust-lang.org/stable/std/ops/trait.BitOrAssign.html
[BitXor]: https://doc.rust-lang.org/stable/std/ops/trait.BitXor.html
[BitXorAssign]: https://doc.rust-lang.org/stable/std/ops/trait.BitXorAssign.html
[Not]: https://doc.rust-lang.org/stable/std/ops/trait.Not.html
[Shl]: https://doc.rust-lang.org/stable/std/ops/trait.Shl.html
[ShlAssign]: https://doc.rust-lang.org/stable/std/ops/trait.ShlAssign.html
[Shr]: https://doc.rust-lang.org/stable/std/ops/trait.Shr.html
[ShrAssign]: https://doc.rust-lang.org/stable/std/ops/trait.ShrAssign.html
[Deref]: https://doc.rust-lang.org/stable/std/ops/trait.Deref.html
[DerefMut]: https://doc.rust-lang.org/stable/std/ops/trait.DerefMut.html
[Index]: https://doc.rust-lang.org/stable/std/ops/trait.Index.html
[IndexMut]: https://doc.rust-lang.org/stable/std/ops/trait.IndexMut.html
[read__read_to_string]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#method.read_to_string
[Read]: https://doc.rust-lang.org/stable/std/io/trait.Read.html
[std-io]: https://doc.rust-lang.org/stable/std/io/index.html
[File]: https://doc.rust-lang.org/stable/std/fs/struct.File.html
[read__read]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#tymethod.read
[read__read_to_end]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#method.read_to_end
[read__bytes]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#method.bytes
[read__chars]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#method.chars
[read__take]: https://doc.rust-lang.org/stable/std/io/trait.Read.html#method.take
[BufReader]: https://doc.rust-lang.org/stable/std/io/struct.BufReader.html
[Args]: https://doc.rust-lang.org/stable/std/env/struct.Args.html
[TryMacro]: https://doc.rust-lang.org/stable/std/macro.try!.html
[unwrap]: https://doc.rust-lang.org/stable/core/option/enum.Option.html#method.unwrap
[Mutex]: https://doc.rust-lang.org/stable/std/sync/struct.Mutex.html
[AtomicUsize]: https://doc.rust-lang.org/stable/std/sync/atomic/struct.AtomicUsize.html
[Sync]: https://doc.rust-lang.org/stable/std/marker/trait.Sync.html
[Drop]: https://doc.rust-lang.org/stable/std/ops/trait.Drop.html
[clone_from_slice]: https://doc.rust-lang.org/stable/std/primitive.slice.html#method.clone_from_slice
[copy]: https://doc.rust-lang.org/stable/std/ptr/fn.copy.html
[copy_nonoverlapping]: https://doc.rust-lang.org/stable/std/ptr/fn.copy_nonoverlapping.html
[clone]: https://doc.rust-lang.org/stable/std/clone/trait.Clone.html#tymethod.clone
