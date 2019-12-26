# Compact2012

## DAC

## Calibration Extension

This extensions may be assembled on the XY-BCP.
The software used to use this extensions uses the prefix `calib_`.

## Workflow

### `calib_raw_`: Measure the DAC

- Write Program onto SD-Card:
  - Copy these files from this directory to the sdcard:
    - main.py
    - config_serial.py
    - calib_raw_create_empty_files.py
    - micropython_portable.py
    - micropython_logic.py
    - micropython_ads1219.py
  - Copy `config_serial_template.py` to `config_serial.py`.
  - Make sure the serial number of `config_serial.py` pyboard corresponds to the Compact_2012
  - You may create empty files using `calib_raw_create_empty_files.py`. Delete the files you want to measure.

- Power on first Compact_2012, then the pyboard.
  - Green LED blinks: Measuring
  - Green LED steady: Done
  - Red LED: Error

  The progress may be observed by opening a putty-console to COMxx.

- Wait for "Green LED steady'.
- Remove SD-Card and copy file to the folder `calibration_raw`.

### `calib_prepare_`: Run calibration algorithmus

- Place files into folder `compact_2012\calibration_raw`.
- Add serial number into `calib_prepare_run.py`.
- Run `calib_prepare_run.py`
- Add the resulting files in `calibration_correction\20190606_99\xx` to git.
- Update serial port in `calib_correction_test_endtest.py` (compact_2012_driver.Compact2012('COM?'))
- Run `calib_correction_test_endtest.py`.
- Take `calib_correction_test_endtest_out.txt` and update OpenOffice Calc TODO and verify result.
- Trash `calib_raw_`-files.

### `calib_correction_`: Apply calibration data

- Delete all files from pyboards flashdrive.
- Copy `config_serial_template.py` to `config_serial.py`.
- Make sure the serial number of `config_serial.py` pyboard corresponds to the Compact_2012
