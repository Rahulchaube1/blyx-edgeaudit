<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin inspecting repeated arrows and a self-loop on a pegboard.">

# EdgeAudit

Audit exact repeated directed edges and self-loops. This Blyx library is part of the geospatial and scientific computing collection.

Duplicated edge rows and loops change degree in a multigraph. Surface those counts before downstream graph analysis. [NetworkX, graph degree](https://networkx.org/documentation/stable/reference/classes/generated/networkx.Graph.degree.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-edgeaudit.git
cd blyx-edgeaudit
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-edgeaudit) · [Package page](https://www.blyx-lang.space/packages/edgeaudit) · [Handbook](https://doc.blyx-lang.space/guide/tanager)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-edgeaudit.git vendor/edgeaudit
```

```blyx
use vendor::edgeaudit::edgeaudit;

fn main() {
    let starts = [1, 1, 2];
    let ends = [2, 2, 2];
    let result = edgeaudit_duplicates(starts, ends);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
1
2
```

## API

`edgeaudit_duplicates(starts, ends)`

Returns [duplicate occurrences beyond the first, self-loop occurrences, unique directed edges]. Reversed edges are distinct. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| starts | Vector of values, each a exact signed integer |
| ends | Vector of values, each a exact signed integer |

## In use

[Tanager](https://github.com/Rahulchaube1/blyx-tanager) uses this module to audit a directed edge list before interpreting a vertex's degree.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-edgeaudit/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
