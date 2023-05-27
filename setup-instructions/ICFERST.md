# [ICFERST](https://imperialcollegelondon.github.io/multifluids_icferst/index.html) setup instructions

These instructions assume you are installing ICFERST on `WSL2 on Windows 11 -- Ubuntu 20.04`.
** Note: For Ubuntu 22/04 please contact p.salah@imperial.ac.uk

## Installation of ICFERST
The very first step is to deactivate any conda environment in your terminal (even base).
```
conda deactivate
conda deactivate
```

### 1. Download from Github
First you need to clone/download ICFERST from its Github repo:

Open your ubuntu `terminal` and navigate to a folder you wish to install ICFERST.

```
mkdir ICFERST && cd ICFERST && git init && git clone https://github.com/ImperialCollegeLondon/multifluids_icferst.git
```

### 2. Install dependencies

```
sudo apt-add-repository ppa:fluidity-core/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install fluidity-dev
```

You may need to explicitly define FCFLAG:
```
nano ~/.bashrc

```
After opening the bashrc go to the end and copy paste:

```
export FCFLAGS="-I/usr/include"
```

### 3. Install ICFERST

Once installed dependencies and clone the repo, for ICFERST, you can install it by navigating to the `multifluids_icferst` folder:

```
cd multifluids_icferst/
```
```
./configure --enable-2d-adaptivity --enable-sam && sudo make install
```
This will take a couple of minutes.

## Installation of Diamond

The input files for your simulations are `EXAMPLE.mpml`. This files can be either manipulated using diamond a GUI, or a text file. To open the diamond GUI for ICFERST in wsl you need to install below dependencies.

```
sudo apt-get update

sudo apt-get install gir1.2-gtksource-3.0

sudo apt-get install gir1.2-gtk-3.0
```


## Make your life easier
Finally there are two scripts to be modified and copied (manually) into /usr/bin to make the use of Diamond and ICFERST much easier.

```
cd ICFERST/tools/scripts_to_make_life_easier/
```
Change the path in the Diamond.sh and RunICFERST.sh with your favourit editor!

```
nano Diamond.sh
```
```
nano RunICFERST.sh
```
then you need to manualy copy these two file into  `/usr/bin`
```
sudo cp Diamond.sh /usr/bin
```
```
sudo cp RunICFERST.sh /usr/bin
```
All done!
Now you can easily open your input files with `Diamond.sh Example.mpml` and run it with `RunICFERST.sh Example.mpml`.

## Post-processing

ICFERST generates two types of outputs: a `.csv` file and `.vtu`. You can either write python code to read and interpret your outputs or use [Paraview](https://www.paraview.org/). Paraview is an open source visualisation application and you can download it from [here](https://www.paraview.org/download/). After you download the latest version for Windows 11 open the `exe` file and follow the instructions.

You can find some useful tutorial videos [here](https://www.paraview.org/tutorials/)

