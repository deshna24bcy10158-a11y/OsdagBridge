
# OsdagBridge – Software Testing Summary

## 1. Project Overview

This repository contains testing work performed on OsdagBridge as part of the Software Testing & Issue Reporting assignment.

The testing focused on:
- Basic and additional input customization.
- Custom material selection.
- Consecutive design execution.
- Persistence of input values.
- 3D model and structural output verification.
- Source-code inspection of input and output dictionary handling.

## 2. Test Environment

- Operating System: Windows 11
- Application: OsdagBridge
- Python Environment: osdagbridge-env (Conda)
- Design Code: IRC 6 (2017)

## 3. Design Test Runs

Three consecutive design runs were completed successfully.

| Parameter | Run 1 | Run 2 | Run 3 |
|---|---:|---:|---:|
| Span | 30 m | 31 m | 32 m |
| Carriageway width | 5 m | 5 m | 5 m |
| Median | No | No | No |
| Footpath | None | None | None |
| Skew angle | 0° | 0° | 0° |
| Design type | Optimized | Optimized | Optimized |

### Material Configuration

- Girder: E250C
- Cross Bracing: E300A
- End Diaphragm: E275A
- Concrete Deck: M30

### Custom Location Configuration

- Basic Wind Speed: 50 m/s
- Seismic Zone: III
- Zone Factor: 0.16
- Minimum Temperature: 10
- Maximum Temperature: 45

## 4. Test Results

| Test | Description | Result |
|---|---|---|
| TC-01 | Run 1 design execution | PASS |
| TC-02 | Run 2 with span changed to 31 m | PASS |
| TC-03 | Run 3 with span changed to 32 m | PASS |
| TC-04 | 3D model generation | PASS |
| TC-05 | Design summary checks | PASS |
| TC-06 | Structural plots generation | PASS |
| TC-07 | Result table and report generation | PASS |
| TC-08 | Deck thickness changed from 250 mm to 260 mm and retained after design | PASS |

## 5. Output Verification

The following outputs were inspected:
- 3D bridge model.
- Bending Moment Diagram (BMD).
- Shear Force Diagram (SFD).
- Deflection diagram.
- Analysis and Design Results Summary.
- Design Summary.
- Generated result tables and PDF reports.

The design summaries displayed PASS for the three main runs.

Run 2 showed updated analysis values compared with Run 1, indicating that the changed span affected the displayed results.

## 6. Input Persistence Observations

The concrete deck thickness was changed from 250 mm to 260 mm.

The value remained 260 mm after:
1. Saving the additional inputs.
2. Closing and reopening the Additional Inputs section.
3. Executing the design again.

Some steel member property sections displayed default values after execution. Girder and stiffener fields inspected during testing were not editable. Further investigation is needed to establish whether this is intended application behaviour or a defect.

## 7. Source-Code Inspection

The following source files were inspected:

- `plategirderbridge.py`
- `template_page.py`
- `connect.py`

Key observations:

- Input values are normalized through `_normalize_input_dict()`.
- Basic and additional inputs are separated.
- The bridge layout pipeline copies the input dictionary into the output dictionary.
- The GUI transfers input data to the backend before design execution.
- The backend validates inputs and invokes `_get_output_dictionary()`.
- The GUI refreshes result selections, plots, and 3D CAD parameters after design completion.

The internal dictionaries were inspected through source code, but a complete runtime field-by-field comparison against the generated reports was not performed.

## 8. Defect and Issue Status

No confirmed software defect, crash, or calculation error was established during the completed tests.

No GitHub issue was created because an unverified issue should not be reported as a genuine bug.

## 9. Testing Limitations

- Runtime Input Dictionary and Output Dictionary values were not captured for a complete field-by-field comparison.
- Exact custom steel member property values were not recorded.
- Run 3 numerical output values were not transcribed.
- Cross-bracing and end-diaphragm property editability requires further verification.

## 10. Conclusion

Three consecutive design runs were completed successfully with changing span values. The application generated 3D models, structural plots, design summaries, result tables, and reports.

The concrete deck thickness persistence test also passed. Source-code inspection provided an understanding of the input-to-backend and output-refresh workflow.

Further testing is recommended for steel member property persistence and direct runtime dictionary-to-report verification.

