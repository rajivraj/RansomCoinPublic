# RansomCoin
Extracting metadata and hardcoded Indicators of Compromise from ransomware, in a scalable, efficient, way with cuckoo integrations. Ideally, is run during cuckoo dynamic analysis, but can also be used for static analysis on large collections of ransomware. Designed to be fast, with false positive limited to emails, urls, onions, and domains. In short, this is initial triage if you only want monetisation.

---Installation instructions---

From the tools folder:
```
sudo apt-get install build-essential libpoppler-cpp-dev pkg-config python-dev python3-tlsh
python3 -m pip install -r requirements.txt
```

---Usage instructions---

```
python3 coinlector.py
```

This will run the code across all files in the directoy and provide feedback on the estimated time to completion via TQDM. You will need write access for a file called Ransomware.csv in the directory you are working in (which contains the results). It should be possible to run the code across read only malware files though, so only Ransomware.csv need write access.

Currently we are testing for:
```
+Bitcoin Addresses
+Bitcoin Cash Addresses
+Bitcoin Private Keys
+Ethereum addresses
+Ripple addresses
+LTC addresses
+DOGECOIN addresses
+NEO addresses
+DASH addresses
+Domains
+Email Addresses
+Onion Addresses
```

chaisingcoin.py gathers basic info on amounts recieved in BTC, by accounts gathered, based on the output of coinlector.py.
eventcoin.py make IoCs of BTC addresses for a MISP instance, based on the output of coinlector.py. Can easily be extended to include other IoCs such as URLs or XMR accounts.
