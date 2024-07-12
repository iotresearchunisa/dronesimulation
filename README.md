
# Synthetic threat Dataset Generation by UAV fleet Simulation
It is anticipated that the utilisation of drone fleets for the purposes of inspection, logistics and surveillance will become a commonplace occurrence in the future. The creation or enhancement of machine learning-based models necessitates the availability of a substantial quantity of data. This repository, in conjunction with the associated paper, proposes an open-source software stack for the generation of synthetic standard missions, attacks and component failures, as well as the creation of scenarios and data.
## Documentation
Install [PX4](https://docs.px4.io/main/en/sim_gazebo_gz/) and [Ardupilot](https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html#sitl-simulator-software-in-the-loop) following the guidelines on the respective  instroduction guides.

Copy the merge.sdf file into Gazebo's assets world directory.
```
cp ./merge.sdf ~/PX4-gazebo-models/worlds/merge.sdf
```

Run Gazebo
```
gz sim -r merge.sdf
```

Run PX4
```
cd ~/PX4-Autopilot/build/px4_sitl_default/bin

PX4_GZ_STANDALONE=1 PX4_SYS_AUTOSTART=4001 PX4_GZ_WORLD=merge PX4_SIM_MODEL=gz_x500 PX4_GZ_MODEL_POSE="0,2" ./px4 -i 1
```

Run Ardupilot
```
mkdir ~/simX

cd ~/simX

sim_vehicle.py -v ArduCopter -f gazebo-iris --model JSON -l 40.77458134144056,14.788466494464313,0,0

```

Inject Failure using [Mavsdk](https://mavsdk.mavlink.io/main/en/cpp/api_reference/classmavsdk_1_1_failure.html)
## Mention our work
```
@inproceedings{Rimoli2024,
  series = {DHSS 2024},
  title = {Synthetic threat Dataset Generation by UAV fleet Simulation},
  booktitle = {Proceedings of the 14TH International Defense and Homeland Security Simulation Workshop,  DHSS 2024},
  author = {Gennaro Pio Rimoli, Francesco Palmieri, and Massimo Ficco},
  year = {2024},
  month = sep,
  collection = {DHSS 2024}
}
```
## Authors

- [@Gennaro Pio Rimoli](https://github.com/gprimoli)
- [@Francesco Palmieri](https://docenti.unisa.it/026587/home)
- [@Massimo Ficco](https://docenti.unisa.it/058291/home)


## Acknowledgements

This work is part of the research activities realized within the projects SERICS (CUP  PE00000014, under the NRRP MUR program funded by the EU - NGEUm) and FLEGREA (Federated Learning for Generative Emulation of Advanced Persistent Threats - CUP E53D23007950001, Bando PRIN 2022).

