# CE Marking for Connected Devices: A Practical Step-by-Step Guide to CRA and RED Compliance

You built a connected device. Now you want to sell it in the EU. Somewhere in your research you've run into the term "CE marking" and assumed it's one stamp, one process, one box to tick.

It isn't. CE marking is the *visible outcome* of several separate compliance processes running in parallel - each with its own rules, its own documentation, and its own declaration. For most connected hardware today, that means two regulations at once: the **Cyber Resilience Act (CRA)** and, if your device has a radio module, the **Radio Equipment Directive (RED)**. Understanding how they fit together - and what you actually need to do, in what order - is the point of this guide.

We're going to walk through the realistic path most manufacturers will take: **self-assessment**, meaning you evaluate your own product's compliance without paying a notified body to do it for you. This route is available for the majority of connected devices. We'll flag clearly where it isn't.

## Step 0: Does This Even Apply to You?

Before anything else, work out which rules are actually in scope for your product.

- **Does your product have "digital elements"** - software, firmware, or the ability to connect to a network or another device? If yes, the **CRA applies**.
- **Does your product have a radio module** (Wi-Fi, Bluetooth, cellular, LoRa, anything using the radio spectrum)? If yes, the **RED applies too** - specifically its cybersecurity provisions.

Most IoT and connected hardware products will find themselves under both. That's not a mistake in the law - it's a temporary overlap that's about to be resolved (more on that below).

## Step 1: The Big Picture - Why Two Laws at Once

Here's the part that confuses almost everyone, including manufacturers already established in the EU with years of CE marking experience: RED and CRA aren't competing regulations. They're the same regulatory intent, arriving in two waves.

- The **RED's cybersecurity requirements** (Delegated Regulation 2022/30, covering network protection, data privacy, and fraud prevention) have applied since **1 August 2025**. If your device has a radio module that connects to the internet, processes personal data, or handles financial transactions, these rules are already live.
- The **CRA** is broader - it covers cybersecurity for *any* product with digital elements, radio or not. It entered into force in December 2024, but its main obligations phase in over several years: vulnerability reporting duties start **11 September 2026**, and the full regime - secure-by-design requirements, conformity assessment, CE marking - becomes mandatory on **11 December 2027**.
- Once the CRA is fully in force, the RED's separate cybersecurity delegated act is expected to be repealed. The CRA absorbs it. Its essential cybersecurity requirements already cover everything the RED's Article 3(3)(d), (e) and (f) require.

In practical terms: right now, in 2026, a radio-connected product needs to satisfy RED's cybersecurity rules. From December 2027 onward, the CRA becomes the single framework covering the same ground. You're not choosing between them - you're living through a handover period, and for now, both apply.

## Step 2: Classify Your Product

Not every product faces the same level of scrutiny. The CRA sorts products into four risk tiers, and the tier determines whether self-assessment is even available to you:

- **Default category** (most IoT devices, smart home products, general connected hardware): self-assessment is allowed, no restrictions.
- **Important Class I** (routers, password managers, smart home hubs, browsers, and similar): self-assessment is allowed *if* you fully apply a recognized harmonized standard; otherwise a notified body gets involved.
- **Important Class II** (hypervisors, firewalls, intrusion detection/prevention systems, and tamper-resistant microprocessors/microcontrollers - a short, fixed list): third-party assessment is mandatory - self-assessment isn't an option.
- **Critical** (smart cards, secure elements, smart meter gateways): the highest level of scrutiny, potentially requiring formal cybersecurity certification.

Most connected consumer and industrial hardware falls into the default or Important Class I tiers, where self-assessment is realistic. Figuring out exactly where your product sits is worth doing early, because it decides the entire rest of your path.

## Step 3: Build the Technical Documentation

This is the substantive work, and it's the part that has the most overlap with what your engineering team is already doing (or should be doing). Regulators expect a file that includes:

- A general product description and its intended use
- The security architecture and design concept
- A documented risk assessment and its results
- A complete **Software Bill of Materials (SBOM)** - a structured, machine-readable list of the software components in your product, covering at minimum the top-level dependencies
- A description of your vulnerability management process
- Test results and examination reports
- A description of your update mechanism

On the SBOM specifically: the law itself only requires a "commonly used and machine-readable format" - it doesn't name a specific one. In practice, the market has converged on two: **CycloneDX** and **SPDX**. Neither is legally mandatory, but both are purpose-built for this, widely tooled, and make it far easier to automatically cross-reference your dependencies against vulnerability databases like the CISA KEV or OSV.dev - something a prose PDF or an unstructured spreadsheet makes much harder to do reliably. If you don't already have tooling in place for this, building it now, well before any deadline forces your hand, will save you a scramble later.

This documentation isn't a one-time deliverable, either. It needs to be kept up to date, and retained for at least 10 years (or your product's support period, if longer - see below).

## Step 4: Run the Conformity Assessment (Self-Assessment / "Module A")

This is where the actual evaluation happens. Under the CRA's internal control procedure - commonly called Module A - you check your own product against the essential cybersecurity requirements, on your own responsibility, without an external body reviewing your work.

This is genuinely a case of "no one checks your homework before you submit it" - which is exactly why the documentation from Step 3 matters so much. If something goes wrong later, that file is your evidence that you did the work properly.

If a relevant harmonized standard exists and you apply it fully, your product benefits from a "presumption of conformity" for the parts of the product that standard covers. Two things to keep in mind here: first, this presumption is often partial - a standard covering, say, network protection doesn't automatically cover privacy or fraud-prevention requirements too. Second, applying a standard never removes your obligation to carry out your own risk assessment. The responsibility for your product's security always stays with you, standard or no standard.

## Step 5: Address RED Separately (If You Have Radio)

If your product has a radio module, don't assume Step 4 covers you completely - RED's cybersecurity requirements (Article 3.3 d/e/f) need their own assessment, currently running in parallel with CRA.

Since August 2025, self-declaration is available here too, through harmonized standards (the EN 18031 series). But there's a catch worth knowing before you count on it: these standards were published *with restrictions*. Self-declaration only works cleanly for products that fall within those restrictions. Outside them, a notified body still needs to be involved. Check this carefully rather than assuming the "simple path" is automatically open to you.

One more thing worth flagging if you're building on a third-party radio module or System-on-Module (SOM): the module itself is typically *not* subject to these cybersecurity requirements when shipped as a bare component requiring integration - module vendors will often mark this "N/A" in their own declaration of conformity. That doesn't mean you're off the hook. Responsibility shifts to whoever integrates the module into a finished product. Buying a "certified" radio module does not certify your final device.

## Step 6: Write the EU Declaration of Conformity

Once your assessment is complete, you draw up a signed EU Declaration of Conformity (DoC) - a formal written statement, under your own responsibility, that your product meets the requirements. It identifies the product, references the regulations it complies with, states which assessment module you used, and carries a signature with a name, role, date, and place.

There's also a simplified version available for situations where space is limited (product packaging, a user manual), consisting of a short statement plus a stable URL pointing to the full declaration online.

## Step 7: Affix the CE Mark

Only after the declaration is signed can the CE mark actually go on the product. This is the visible signal to the market - and to enforcement authorities - that everything behind it has been done.

## Step 8: Your Job Isn't Over - Post-Market Obligations

This is the step manufacturers most often underestimate. CE marking isn't a finish line; it's the start of an ongoing set of duties:

**Vulnerability and incident reporting.** From 11 September 2026, manufacturers must report actively exploited vulnerabilities and severe incidents through a central reporting platform, on a fixed clock: a 24-hour early warning, a 72-hour detailed report, and a 14-day (or 30-day, for incidents) final report. This applies to every in-scope product already on the market too - not just new ones.

**The support period.** You must commit to a period during which you'll handle vulnerabilities and provide security updates. Five years is commonly treated as a default benchmark, but it isn't automatic or one-size-fits-all in either direction: if your product is reasonably expected to stay in use longer (common for industrial or embedded hardware), your support period should reflect that, and for genuinely short-lived products, it can legitimately be shorter too - the regulation itself gives the example of an app built to support a time-limited public health campaign. Either way, you need to document your reasoning for whatever length you choose, and the end date has to be clearly stated to buyers at the point of purchase.

## What Should You Actually Do Right Now, in 2026?

Given the staggered deadlines, here's a realistic order of operations if you're starting today:

1. **Now:** Start building your SBOM process and vulnerability-handling policy. Don't wait for a deadline to force this - it takes longer to build properly than most teams expect.
2. **Before 11 September 2026:** Have a working incident and vulnerability reporting process in place. This deadline doesn't care whether your product is brand new or five years old.
3. **Through 2026-2027:** Watch for harmonized standards being published (most are expected through late 2026 and into 2027) and fold them into your development process as they become available.
4. **By 11 December 2027:** Full conformity - technical documentation, conformity assessment, EU Declaration of Conformity, CE marking - needs to be in place for anything newly placed on the market.

There's no general grace period built into any of these dates. The practical runway is the time between now and each deadline - not the time after it.

## Common Questions That Come Up

**"I don't manufacture the hardware myself - I white-label an OEM product. Does this still apply to me?"**
Yes. What matters under the CRA isn't who physically built the device - it's whose name or brand is on it. If you sell it under your own brand, you're the manufacturer, with the full set of obligations, even if someone else designed and built it.

**"I already have this product on the market. Do I need to redo everything?"**
Mostly no, for full conformity - products already placed on the market before 11 December 2027 are largely grandfathered, as long as nothing "substantial" changes about them afterward. Routine bug fixes and security patches don't count as substantial changes. But there's one exception: vulnerability and incident reporting duties apply to *all* in-scope products from September 2026, including ones already sold.

**"How much could this actually cost me if I get it wrong?"**
Penalties are tiered by severity. The most serious violations - non-compliance with essential security requirements - can reach up to €15 million or 2.5% of global annual turnover, whichever is higher. Less severe violations top out at €10 million (2%) or €5 million (1%) depending on the nature of the breach. Authorities can also order products withdrawn from the market on top of any fine. There's a narrow exception for very small businesses, but it only covers missed *reporting deadlines* - not general non-compliance. Note this penalty structure is specific to the CRA - RED leaves penalty amounts to each Member State's own national law (see [`penalties-enforcement.md`](red/penalties-enforcement.md)).

---

*This guide covers the general self-assessment path for connected devices under CRA and RED. It's not legal advice - for products in higher risk categories, or if you're unsure where your product falls, get advice specific to your situation. For the full detail behind each step, see [`overview.md`](cra/overview.md), [`product-risk-classes.md`](cra/product-risk-classes.md), [`essential-requirements.md`](cra/essential-requirements.md), [`red/overview.md`](red/overview.md), [`red/essential-requirements.md`](red/essential-requirements.md), and [`penalties-enforcement.md`](cra/penalties-enforcement.md).*
