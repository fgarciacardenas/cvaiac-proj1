# CVAIAC2025 - Proj 1: Notes

## 0) Credentials
Username: ac_course_04

Password: -VY5ixukO:1T

SSH into server:
```bash
ssh ac_course_04@hades.ee.ethz.ch
```

Connect to VPN: 
```bash
sudo openconnect -u gfacundo@student-net.ethz.ch --useragent=AnyConnect -g student-net sslvpn.ethz.ch
```


## 1) Information
Course data: `/srv/beegfs-benderdata/scratch/ac_course/data`

Work dir: `/srv/beegfs-benderdata/scratch/ac_course_04/data`
	- Store python env

Final dir: `/srv/beegfs-data/projects/ac_course_04/data`


## 2) Log into GPU node
Start interactive session:
```bash
srun --time 300 --gres=gpu:1 --cpus-per-task=4 --pty bash -i
```

Activate the Conda environment:
```bash
conda activate py39
```

Setup python environment form the root directory of the cloned repo:
```bash
PIP_CACHE_DIR=/srv/beegfs-benderdata/scratch/$USER/data pip install -r requirements.txt
```


## 3) Setup Conda

- Setup Conda
```bash
cd /srv/beegfs-benderdata/scratch/ac_course/data
./install_conda.sh /srv/beegfs-benderdata/scratch/$USER/data
```

- Add conda and slurm to /bashrc:
```bash
echo '[[ -f /srv/beegfs-benderdata/scratch/$USER/data/conda/bin/conda ]] && eval
"$(/srv/beegfs-benderdata/scratch/$USER/data/conda/bin/conda shell.bash hook)"' >>
/home/$USER/.bashrc
echo 'export SLURM_CONF=/home/sladmcvl/slurm/slurm.conf' >> ~/.bashrc
source ~/.bashrc
```

- Start a 5h interactive session with 1 gpu:
```bash
srun --time 300 --gres=gpu:1 --pty bash -i
```

- Create an conda environment:
```bash
conda create -y --name py39 python=3.9.4
conda activate py39
```

- For each project (will be reminded) install the required packages with:
```bash
PIP_CACHE_DIR=/srv/beegfs-benderdata/scratch/$USER pip install -r requirements.txt
```

- End interactive session with:
```bash
ctrl + d
```

# Exercise 1
Setup environment in GPU node
```bash
srun --time 300 --gres=gpu:1 --cpus-per-task=4 --pty bash -i
conda activate py39
cd /srv/beegfs-benderdata/scratch/ac_course_04/data/cvaiac25
PIP_CACHE_DIR=/srv/beegfs-benderdata/scratch/$USER/data pip install -r requirements.txt
bash shell_train.sh
```

