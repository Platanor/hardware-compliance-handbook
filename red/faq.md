**Practical FAQ on RED's cybersecurity requirements for hardware/IoT manufacturers**

**Does RED apply to my product at all?**
Only if it meets the Article 2(1) definition of "radio equipment": an electrical or electronic product that intentionally emits and/or receives radio waves for radio communication or radiodetermination, or a product that needs an accessory (like an antenna) to do so. Wi-Fi, Bluetooth, cellular, LoRa, Zigbee — all of these make a product "radio equipment." A purely wired device with no radio interface at all is outside RED's scope, though it may still fall under the CRA if it has digital elements.

**My device has Bluetooth. Does RED's cybersecurity requirement automatically apply?**
Not automatically for all three points. It depends on what the device does: point (d) (network protection) applies if it's internet-connected (directly or via another device). Point (e) (privacy) applies to internet-connected equipment that processes personal data, plus childcare/toy/wearable equipment regardless of internet connectivity, if it processes personal or traffic/location data. Point (f) (fraud protection) applies only if the equipment enables transferring money, monetary value, or virtual currency. A Bluetooth device with no internet connectivity, that doesn't process personal data, and doesn't handle payments may not trigger any of the three activated points — check against the specific triggers in [`essential-requirements.md`](essential-requirements.md) rather than assuming.

**Is this the same thing as the Cyber Resilience Act?**
No, though they cover overlapping ground and will eventually merge. RED's activated cybersecurity requirements (Art. 3(3)(d)(e)(f)) have applied since 1 August 2025. The CRA's essential requirements (Annex I) don't become mandatory until 11 December 2027, and are structured differently — broader in scope (applies to any product with digital elements, not just radio equipment) and organised around a risk-based chapeau rather than RED's category-gated activation mechanism. Until the CRA's transition provisions repeal RED's cybersecurity delegated act, a radio-connected product with digital elements needs to satisfy both.

**I applied EN 18031-1. Am I done with point (d)?**
Not necessarily. EN 18031-1 confers presumption of conformity for point (d) *except* where the "rationale" and "guidance" sections are relied on (they confer nothing), and *except* where the manufacturer implements the standard's clause 6.2.5.1/6.2.5.2 option that lets a user skip setting a password. If either exception applies to how the standard was actually implemented, self-declared presumption of conformity isn't available for that part, and third-party assessment is needed instead.

**Can I self-assess, or do I need a notified body?**
Depends on whether a relevant harmonised standard exists and has been fully applied. If yes (and none of the EN 18031 restrictions apply to how it was implemented), Module A (self-assessment/internal production control) is available even for the Article 3(2)-(3) requirements. If no relevant standard exists, or it's only partially applied, or one of the restrictions bites, the manufacturer must use EU-type examination (Module B+C) or full quality assurance (Module H) — both of which require a notified body.

**What happens to RED once the CRA is fully in force?**
The CRA's essential requirements already cover everything RED's Article 3(3)(d)(e)(f) address. The plan is for RED's cybersecurity delegated act to be repealed once the CRA reaches full application on 11 December 2027, so that manufacturers stop having to satisfy two parallel frameworks for the same ground. That repeal has not happened as of this repository's last verification date — check current Commission guidance before assuming the transition is complete.

**What's the fine if I get this wrong?**
There's no single EU-wide number — unlike the CRA, RED leaves penalty amounts to national transposing law (Article 46 only requires penalties to be "effective, proportionate and dissuasive," and permits criminal penalties for serious infringements). The actual figure depends on which Member State's law applies. See [`penalties-enforcement.md`](penalties-enforcement.md).

**I bought a "CE-certified" radio module from a supplier. Does that cover my finished product?**
No. A bare radio module or System-on-Module (SOM) that requires integration is typically not itself in scope for these requirements — the module vendor often marks this "N/A" in its own declaration of conformity. Once you integrate the module into a finished product, you become the manufacturer of that product for RED purposes, and the compliance obligation is yours, not the module vendor's.

**Where do I find the actual legal text?**
[`primary-sources/red-directive-2014-53-eu.md`](../primary-sources/red-directive-2014-53-eu.md) (the directive itself — note this is the original 2014 text, not consolidated), [`primary-sources/red-delegated-regulation-eu-2022-30.md`](../primary-sources/red-delegated-regulation-eu-2022-30.md) (activates points (d)(e)(f)), [`primary-sources/red-delegated-regulation-eu-2023-2444-amending.md`](../primary-sources/red-delegated-regulation-eu-2023-2444-amending.md) (moves the application date to 1 August 2025), and [`primary-sources/red-implementing-decision-eu-2025-138-en-18031.md`](../primary-sources/red-implementing-decision-eu-2025-138-en-18031.md) (publishes EN 18031-1/-2/-3 with restrictions).
