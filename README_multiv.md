
# Workflow for multivariate Time Series
1. Preprocess the data like in [HTM_anomaly_multiv](https://github.com/pizzatakeaway/HTM_anomaly_multiv), `notebooks/Data_ECG_for_NAB.ipynb`
1. Copy data from [HTM_anomaly_multiv](https://github.com/pizzatakeaway/HTM_anomaly_multiv) `data/interim/NAB/` to `NAB/data/HTM_anomaly_multiv`.
1. Don't forget to import the updated `data/interim/NAB/combined_windows_HTM_multiv.json` to `NAB/labels/`
1.   
    ```
    $ python run.py -d skyline,numenta --detect --optimize --windowsFile labels/combined_windows_HTM_multiv.json
    ```
 1.   Then execute in `R` the `nab/detectors/nab/detectors/twitter_ad_vec/nab_anomaly_detection.R`  
    More info in the [wiki](https://github.com/numenta/NAB/wiki/Twitter-Anomaly-Detector).

 1.   Finally:
    ```
    # $ python scripts/create_new_detector.py --detector twitterADVec`
    $ python run.py -d twitterADVec --optimize --windowsFile labels/combined_windows_HTM_multiv.json

    ```
1.    All results are stored in:  
        - `results/numenta/HTM_anomaly_multiv/`  
        - `results/skyline/HTM_anomaly_multiv/`  
        - `results/twitterADVec/HTM_anomaly_multiv/`