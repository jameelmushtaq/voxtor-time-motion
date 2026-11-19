# AVT Time and Motion Recorder

A web app for observers timing clinical consultations in a time and motion study of ambient voice technology (AVT). It compares documentation time at baseline (no AVT) with documentation time using AVT. It was built for the Moorfields Eye Hospital AVT pilot (City Road, ED and clinics) as part of the NHS Fellowship in Clinical AI.

Author: Dr Jameel Mushtaq. Current version: 1.4 (19 Nov 2026).

Live copy: https://voxtor.netlify.app

## What it records

- **Arm:** baseline (no AVT) or AVT. If the patient declines AVT, the encounter stays in the AVT arm and is flagged.
- **Timers:** consultation start, a documentation timer that can be started and stopped any number of times, and an AVT set-up timer for logging in and linking the patient.
- **Interruptions:** colleagues asking for advice or the clinician being called away. All timers pause and the time is excluded from every duration.
- **Paused patients:** a patient who leaves for tests can be paused while the next patient is seen, then resumed when they return. Time out of the room is excluded.
- **AVT output errors:** hallucinations, omissions, wrong laterality and similar, with clinical significance and whether each was caught before filing.
- **Clinician questionnaire:** NASA-TLX for documentation workload in both arms, plus the System Usability Scale in the AVT arm.
- **Patient survey:** a built-in standard version and AVT version, completed on the device or read aloud. A QR code can also link to an external survey, set in Settings.

## Data handling

- Everything is stored in the browser of the device it is used on. Nothing is sent to a server.
- Observers export an `.xlsx` workbook with these sheets: Encounters, Events, Output_errors, Clinician_surveys, Patient_surveys, Patient_linkage and Data_dictionary.
- The hospital number is the only patient identifier. It appears only on the Patient_linkage sheet, which should be removed before the workbook is shared with raters or analysts.
- Send exports by NHS email only, then delete the data from the device under Settings.

## Files

- `index.html`: the app. It loads SheetJS and qrcodejs from cdnjs, so it needs an internet connection on first load.
- `offline/AVT-Time-and-Motion-Recorder.html`: the same app with both libraries built in, so it works without internet access. This is the file to upload to Netlify Drop.

## Using it on a phone or tablet

1. Open the hosted link in Safari on iOS or Chrome on Android.
2. Add it to the home screen (Share, then Add to Home Screen).
3. Always open it from the home screen icon, so the data stays in the same place.
4. Run one encounter in practice mode before collecting real data. Practice encounters are left out of the export.

## Third-party libraries

- [SheetJS Community Edition](https://sheetjs.com) 0.18.5, Apache License 2.0
- [qrcodejs](https://github.com/davidshimjs/qrcodejs) 1.0.0, MIT License

## Licence and citation

Released under the MIT Licence (see `LICENSE`). To cite the recorder, use the "Cite this repository" button on GitHub or the details in `CITATION.cff`.
