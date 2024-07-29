## Executing ABS Simulations

The simulation can be executed via docker. First, you need to start a container containing the ABS code with:

```bash
docker run --entrypoint="/bin/bash" -i --rm -t lorenzobacchiani/teastoregs
```
The container is initially in abs-simulations/.
To change the simulation parameters (e.g., inbound workload, predicted workload, enable proactivity and/or reactivity), you need to go in [param.abs](globalScaling/param.abs) (for global scaling) and 
[param.abs](localScaling/param.abs) (for local scaling) and comment/uncomment the parameters you want to discard/use, using vim as editor (it is already installed within the container).

### Global Scaling
To compile the ABS code for global scaling (from abs-simulations/):

```bash
cd globalScaling/
```
```bash
./compile.sh
```

To run the ABS code for global scaling:

```bash
gen/erl/run
```

If you want to test our mixing technique go to [workload_mixer.abs](abs-simulations/globalScaling/workload_mixer.abs) and [monitor.abs](abs-simulations/globalScaling/monitor.abs) and uncomment everything tagged with '//OUR MIXING TECHNIQUE' and comment everything tagged with '//LITERATURE MIXING TECHNIQUE'.

If you want to use the mixing technique from [1] do viceversa.

### Local Scaling
To compile the ABS code for local scaling (from abs-simulations/):

```bash
cd localScaling/
```
```bash
./compile.sh
```

To run the ABS code for local scaling:

```bash
gen/erl/run
```
