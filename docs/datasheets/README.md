# Datasheets

Downloaded July 5, 2026.

## Current KiCad PCB

| Part | File | Source | Why it matters |
|---|---|---|---|
| TI DRV8701ERGER / DRV8701 | `TI_DRV8701ERGER_DRV8701_datasheet.pdf` | https://www.ti.com/lit/ds/symlink/drv8701.pdf | Main brushed DC full-bridge gate driver. Use for supply limits, gate-drive current, current-sense amplifier, charge pump, fault behavior, and layout requirements. |
| ST STM32G474RETx | `ST_STM32G474RE_datasheet.pdf` | https://www.st.com/resource/en/datasheet/stm32g474re.pdf | MCU currently used by the CubeMX project and KiCad schematic. Use for pinout, package, clocks, ADC/timer/CAN electrical limits, and power requirements. |
| ST STM32G4 reference manual | `ST_STM32G4_reference_manual_RM0440.pdf` | https://www.st.com/resource/en/reference_manual/rm0440-stm32g4-series-advanced-armbased-32bit-mcus-stmicroelectronics.pdf | Register-level reference for STM32G4 peripherals. Use for timer, ADC, FDCAN, DMA, clock tree, boot, and debug bring-up. |
| ST STM32G4 hardware getting started | `ST_STM32G4_hardware_getting_started_AN5345.pdf` | https://www.st.com/resource/en/application_note/an5345-getting-started-with-the-stm32g4-series-mcu-hardware-development-stmicroelectronics.pdf | Hardware checklist for STM32G4 power, reset, clock, boot, decoupling, and debug connections. |
| TI SN65HVD230DR | `TI_SN65HVD230DR_datasheet.pdf` | https://www.ti.com/lit/ds/symlink/sn65hvd230.pdf | 3.3 V CAN transceiver on the PCB. Use for CAN bus pinout, termination/stub guidance, common-mode range, and standby/slope-control behavior. |
| Advanced Monolithic Systems AMS1117-3.3, LCSC C6186 | `LCSC_AMS1117-3.3_C6186_datasheet.pdf` | https://datasheet.lcsc.com/datasheet/pdf/e6935943fc6b1bbf350a1a0f3e90dc4a.pdf?productCode=C6186 | Current PCB LDO. Check dropout, output-cap ESR/stability, thermal dissipation, and the SOT-223 tab connection. |
| TI CSD18540Q5B, LCSC C86513 | `TI_CSD18540Q5B_datasheet_LCSC_C86513.pdf` | https://www.ti.com/lit/ds/symlink/csd18540q5b.pdf | LCSC C86513 resolves to this MOSFET. Use for RDS(on), gate charge, SOA, thermal limits, and footprint/stencil data. |
| TI CSD18532Q5B | `TI_CSD18532Q5B_datasheet_KiCad_part_name.pdf` | https://www.ti.com/lit/ds/symlink/csd18532q5b.pdf | KiCad imported symbol/footprint text names this MOSFET. Keep until the BOM mismatch is resolved. |
| TI DRV8701EVM | `TI_DRV8701EVM_user_guide_SLVUAG3.pdf` | https://www.ti.com/lit/pdf/SLVUAG3 | Relevant because the PCB appears derived from the DRV8701EVM Altium import. Includes reference schematic and BOM context. |

## Layout And Motor-Driver References

| Topic | File | Source | Why it matters |
|---|---|---|---|
| Motor-driver PCB layout | `TI_Motor_Driver_Board_Layout_Best_Practices_SLVA959.pdf` | https://www.ti.com/lit/pdf/slva959 | High-current H-bridge layout, bypassing, current loops, ground strategy, and thermal layout. |
| Smart gate drive | `TI_Understanding_Smart_Gate_Drive_SLVA714.pdf` | https://www.ti.com/lit/pdf/slva714 | Explains gate-drive strength, switching behavior, protection, and EMI tradeoffs. |
| Current regulation | `TI_Current_Regulation_Brushed_Stepper_SLOA170.pdf` | https://www.ti.com/lit/pdf/sloa170 | Useful for DRV8701 VREF, sense resistor, chopping/current-limit design. |
| Short-to-battery/ground detection | `TI_Gate_Driver_Short_To_Battery_Ground_SLVAEV8.pdf` | https://www.ti.com/lit/pdf/slvaev8 | Useful for reviewing motor-output fault protection assumptions. |

## Design-Note Candidates

These parts are mentioned in `docs/design.md`, but are not all present in the current KiCad PCB.

| Part | File | Source | Status |
|---|---|---|---|
| Diodes AP2112K-3.3 | `Diodes_AP2112K_3.3_datasheet_design_note_candidate.pdf` | https://www.diodes.com/assets/Datasheets/AP2112.pdf | Candidate isolated IMU LDO from design notes. Current PCB uses AMS1117-3.3 instead. |
| Diodes AP63203 | `Diodes_AP63203_buck_datasheet_design_note_candidate.pdf` | https://www.diodes.com/assets/Datasheets/AP63200-AP63201-AP63203-AP63205.pdf | Candidate 24 V to 5 V buck from design notes. Not clearly present in the current PCB. |

## Open Item

The MOSFET identity needs cleanup: KiCad properties name `CSD18532Q5B`, while the LCSC code `C86513` resolves to `CSD18540Q5B`. Both are TI 60 V NexFETs in a 5 mm x 6 mm SON-style package, but they are not the same part. Pick one and update the KiCad part properties, BOM fields, and datasheet reference together.
