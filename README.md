# DTNtuples
Ntuples for the analysis of the CMS drift tubes detector performance

## Preliminary instructions
**Note**: 
In the present days this code is evolving fast, hence the installation recipe may change often. Please keep an eye on this page to check for updates.

### Installation:
```bash
cmsrel CMSSW_12_2_1
cd CMSSW_11_2_1/src/
cmsenv
git cms-init
git cms-merge-topic oglez:Phase2_DTAB7Unpacker_v11.2
git cms-merge-topic dtp2-tpg-am:AM_12_2_1_v1
# Calibration part yet to be updated
# git cms-merge-topic swiedenb:DTCalibOfflineSlice_11_2_X 
git clone https://github.com/battibass/DTNtuples.git DTDPGAnalysis/DTNtuples
scramv1 b -j 5
```

### Ntuple prduction:
```
cd DTDPGAnalysis/DTNtuples/test/
cmsRun dtDpgNtuples_slicetest_cfg.py nEvents=10000
# or
cmsRun dtDpgNtuples_phase2_cfg.py nEvents=10000
```

### Analysis:
```
root -b
root [0] .x loadExampleAnalysis.C

root [1] DTNtupleExampleAnalyzer analysis("DTDPGNtuple_run333510.root","results.root")
// or
root [1] DTNtupleExampleAnalyzer analysis("DTDPGNtuple_11_0_2_Phase2_Simulation.root","results.root")

root [2] analysis.Loop()
```
