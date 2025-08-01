# PhotonConv
Photon conversion dielectron analysis for sPHENIX 2024 pp data

- Compile analysis module
```
cd module
mkdir build
cd build
../autogen.sh --prefix=$MYINSTALL
make -j 4
make install
```

- Grab DST file list by using CreateDstList.pl:
```
cd macro/filelist
./create.sh
```
Trkr Tracks, Trkr Cluster, Calo DST lists are generated

- Sync different types of DST by segment ID
```
./sync.sh
```
Trkr Tracks/Cluster DST 10000 events/segment, Calo DST 50000 events/segment

- Submit jobs in condorJob
```
condor_submit condor-data-seed-53877.job
```
**Do not forget to change Initialdir!!!**

- When job running, output root file temporarily stored in inReconstruction/[runnumber]

- When job finished, output root file saved in Reconstructed/[runnumber]

- Offline analysis code in analysis/

``utilities.h``: for const variables, utility functions

``analysis.C``: for Track-EMCal matching association, generate a smaller root file

``plot.C``: for 1D/2D distribution plotting

``EvtDisplay2D.C``: for event display
