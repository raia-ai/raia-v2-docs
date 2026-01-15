# Repairing Coin and Bill Acceptors (CBA) for LPT:One Print Release Stations

This guide helps staff diagnose, repair, and maintain EnvisionWare Coin and Bill Acceptors (CBA) connected to LPT:One Print Release Terminals. It covers quick checks, jam clearing, cleaning, configuration, connectivity, and when to escalate.

### Safety, Tools, and Preparation

* Power off the CBA before removing or reseating internal components.
* Use anti-static precautions when handling boards and cables.
* Recommended tools:
  * Soft brush, lint-free swabs, and 70%+ isopropyl wipes for sensors
  * Compressed air (short bursts)
  * Flashlight
  * Small Phillips screwdriver
  * Replacement tubes/coins for float testing
* Keep keys for the rear door and bypass key accessible.

### Identify Your Hardware

* Coin acceptors commonly used: CoinCo Guardian 6000 (6-tube), MEI CF7000.
* Bill/note acceptors commonly used: CoinCo Vantage, MEI Note Validator.

### Quick-Triage Decision Guide

* Symptom: Accepts coins/bills and shows escrow, but no print job is released
  * Likely causes: Printer not ready/offline, serial cable issue, or control board state. Action: Verify the printer works outside of LPT:One; check serial interface cable; press the RESET on the CBA main board.
* Symptom: Bills/notes are not accepted
  * Likely causes: Insufficient change in tubes (“No Change” light), Max Escrow setting, “Disabled by System” state, dirty sensors, or stuck notes. Actions below.
* Symptom: Coins drop straight through or are rejected
  * Likely causes: Dirty coin path/sensors, float enabled, payout cassette not latched, coin path error, payout motor cable issue. Actions below.
* Symptom: “Payout motor error” on Guardian 6000
  * Likely cause: Ribbon cable not fully seated. Action: Reseat ribbon cable at both ends.
* Symptom: CBA not communicating with the PC (COM port)
  * Likely cause: COM port mismatch or USB re-enumeration. Action: Align Windows COM port with the PRT config and reseat USB.

### Step-by-Step Repair Procedures

#### 1) Power Cycle and Board RESET

1. Power off the CBA, wait \~30 seconds, power on.
2. If a bill validator shows “Disabled by System” flashes even after ensuring tubes have sufficient change, tap the RESET on the main board briefly; if needed, perform a press-and-hold reset until “Check Vendor: Comms Error” appears on the validator LCD, then allow full reboot until the top LCD resumes normal scrolling (e.g., copy prices).

#### 2) Verify Change Levels and Indicators

* Ensure change tubes have sufficient coins; the unit will reject bills if it cannot make change. If “No Change” is lit, refill tubes before further testing.

#### 3) Clear Jams (Coins and Bills)

* Indicators: Coins dropping through, “Unknown Slug Rejected,” whirring noises, or flash codes on the bill cassette.
* Coins (Guardian 6000, MEI CF7000): Follow jam-clearing procedures and staff training videos; incorrect handling can damage components.
* Bills/Notes (CoinCo Vantage, MEI Note Validator): Clear foreign objects and stuck notes per jam-clearing procedures/videos.

#### 4) Clean Sensors and Paths

* Use compressed air (short bursts) and ISO wipes to clean the coin path and validator sensors.
* Refer to MEI Note Validator and CoinPro 3 cleaning instructions for model-specific steps.

#### 5) Check Configuration States (Modes, Escrow, Float)

* Exit any non-vending modes:
  * Bypass Mode: Turn bypass key off and remove; ensure the unit returns to vending mode.
  * Setup/Configuration menus, Meter report screens, Dispense mode: Exit to return to vending.
* Max Escrow: Ensure the Max Escrow value allows acceptance of the inserted denomination.
* Guardian 6000 Float: If coins are not retaining, disable float by pressing D + F simultaneously on the acceptor; look for “Float Disabled,” then verify coin tube amounts.

#### 6) Reseat Mechanical Components and Cables

* Payout cassette: Swing out, then reinsert until it positively latches and indicator light goes out; the unit will not accept coins if not latched.
* Sort door: Verify it is fully closed (red latch area).
* Guardian 6000 ribbon cable: Reseat to resolve payout motor diagnostics failures.

#### 7) Confirm PC Connectivity and COM Port

* In Windows Device Manager, note the COM port assigned to the CBA.
* Match the COM port to your Print Release Terminal configuration (Vending: COM Port in the terminal’s config).
* If mismatched or unstable: Power off CBA, unplug USB, wait 30 seconds, power on, then reconnect USB. Update config if the COM port changed.

#### 8) Validate the Print Path (Rule Out Printer Issues)

* Print a test page directly to the printer (outside LPT:One). If the printer fails here, fix the printer first.
* If printing is fine, try placing the CBA in Bypass mode, make one copy/print, then return to normal mode and test again.
* Ensure the LPT:One Job Queue Engine runs under an admin or fully privileged account on supported OS versions to release jobs properly.

### Parts Replacement and Reinstallation

#### Replace a Coin Acceptor (Overview)

* Follow the model-specific replacement instructions (Guardian 6000 for Series I/II vs Series V/VX). Videos are available; printed guides detail mounting and reconnection.
* Mounting tips: Use correct spacers on studs; ensure no cables are pinched behind the changer; verify coin return cup flap alignment to prevent jams. Power on and test after reassembly.

### Diagnostics Reference

* Bill cassette flash codes: Use the label table on the cassette to interpret flashes. “Disabled by System” can indicate non-vending modes, Max Escrow reached, active escrow deduction, or change being dispensed. Exit those states, ensure change is sufficient, and retry.
* Common on-screen messages:
  * “Unknown Slug Rejected” suggests a coin jam near the insertion point; clear jam and clean sensors.
  * “Payout motor error” on Guardian 6000 suggests a loose ribbon cable; reseat the cable and re-test.

### Preventive Maintenance

* Weekly: Blow out coin and bill paths; wipe exposed sensors; confirm payout cassette latch; check tube coin levels.
* Monthly: Run full jam-clear practice; verify float/escrow settings; confirm COM port alignment after Windows updates or USB changes.
* After every jam: Inspect for coin path damage, bent flaps, or misalignment before returning to service.

### When to Escalate

Escalate to technical support when:

* Repeated “payout motor” or “Disabled by System” errors persist after reseating cables, exiting non-vending modes, and resetting.
* Bills/coins still not accepted after cleaning, clearing jams, replenishing change, and verifying escrow/max settings.
* Communications failures persist after COM port alignment and USB reseat.

Document what you’ve tried (cleaning, resets, configuration states, cables reseated, COM port values, printer test results) before contacting support to speed resolution.

### Appendix: Model-Specific Notes

* Guardian 6000: “Float Disabled” toggle with D + F; ensure payout cassette latch and sort door are fully seated; ribbon cable must be firmly connected.
* MEI Note Validator: After a full reset cycle, wait for solid red LED when the CBA completes boot before testing acceptance. Keep the note path clean.

Troubleshooting videos and printable procedures are available for jam clearing and component replacement; ensure staff are trained with these materials before performing service.
