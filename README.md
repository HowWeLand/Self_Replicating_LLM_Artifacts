[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18582001.svg)](https://doi.org/10.5281/zenodo.18582001)

# Self_Replicating_LLM_Artifacts
Research note on a self‑replicating LLM failure mode discovered in a real-world shell bootstrap installer, and its implications for code-assistant supply chains.

## Project overview

This repository contains a short research paper and supporting materials documenting the accidental creation and discovery of a code artifact that induces recursive logic failures in large language models. The artifact’s output is self‑replicating across model instances and, for a period, was publicly available in a GitHub repo, raising supply‑chain concerns for AI coding assistants.

The work grew out of a very practical goal: building nuts‑and‑bolts automation and educational lab infrastructure around a popular security‑focused Linux distribution. The intent was to give beginners reproducible virtual lab environments, clear documentation of design trade‑offs, and enough epistemic transparency to make their own informed decisions about system hardening and configuration.

As a team of one, I leaned heavily on LLMs as a force multiplier: for code correction, research into Linux “plumbing,” brainstorming around Debian/Devuan packaging and init systems, and—critically—for transforming dense, sometimes rant‑y inline comments into documentation that beginners could actually read. I also live with significant executive dysfunction as part of a disability, and LLMs helped me get past motivational and organizational bottlenecks that would otherwise stall this kind of project.

Over time, the project evolved from a thin scripting layer on top of an existing repo into a shell‑based bootstrap installer intended to take a system from bare metal to a graphical Devuan desktop with built‑in security features. That work led me into init‑system archaeology, installer logic, and experiments with semantic tagging of packages and configuration using `aptitude` and shell tooling.

Along the way, I noticed a pattern: commercial LLMs strongly prefer to render configuration as heredocs, and that style began to bleed into my own code. I started using here‑documents extensively to generate configuration and “finishing” scripts inside a chroot, including scripts written into `/etc/skel` so that new users would inherit a consistent environment. While thinking about Ken Thompson’s “Reflections on Trusting Trust” and playing with quine‑like ideas for self‑documenting installers that could carry themselves forward, the system crossed an invisible line—what had been a useful pattern turned into something that reliably degraded multiple LLMs in normal, non‑adversarial use.

This repository documents:

- How that recursive structure emerged in ordinary development workflows.
- How different commercial LLMs reacted to the resulting artifact.
- Why this pattern looks less like a one‑off glitch and more like a “logical prion” for code‑assistant ecosystems.
- Planned experiments with open‑weights code models to probe how far the behavior generalizes.

## Motivation and ethics

I am an independent security researcher currently dealing with housing instability and unemployment. This work began as an attempt to build a serious portfolio piece and a genuinely useful resource for newcomers to security and Linux, not as a red‑team stunt.

I am publishing these findings despite the political and commercial inconvenience because I hold myself to a code of professional conduct that goes beyond the industry’s often‑abused notion of “ethics.” If a pattern I stumbled into can cause real failures in tools that non‑experts are being encouraged to trust, I consider it a fiduciary duty to document and disclose that behavior as clearly as I can.

My responsibility is to the people who will rely on these systems and cannot afford catastrophic failures in the field, not to the short‑term comfort of vendors or my own career prospects.

## Contents

- `self-replicating_llm_artifacts.tex` – LaTeX source of the paper.
- `self-replicating_llm_artifacts.pdf` – Compiled PDF for easier reading.
- (Future) Experimental code and scripts for reproducing and probing the behavior in open‑weights models.

## How to Cite

If you use this research or the "Logical Prion" framework in your own work, please cite it as follows:

**APA:**
Myint Jr., J. D. (2026). *Self-Replicating LLM Artifacts & Accidental Supply-Chain Contamination*. Zenodo. https://doi.org/10.5281/zenodo.18582001

**BibTeX:**
```
latex
@misc{myint2026logical,
  author    = {Myint Jr., James Duncan},
  title     = {Self-Replicating LLM Artifacts \& Accidental Supply-Chain Contamination},
  year      = {2026},
  month     = {January},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.18582001},
  url       = {https://doi.org/10.5281/zenodo.18582001}
}
```
## License

This work is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0). See the `LICENSE` file for details.

If this research helped you and you want to say thanks, you can toss a few bucks toward my “buy Sneakers, the superior 90s hacker movie” fund:
https://paypal.me/JMyintJr
