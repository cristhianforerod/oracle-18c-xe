# Docker build for Oracle Database 18c Express Edition (XE)

## Prerequisites

- [Download](https://drive.google.com/file/d/1P4tGL1IJq_NPtlZs8KvX_nxCbWeYkkvI/view?usp=sharing) the RPM from Oracle Technology Network and     save to folder. We will assume it is in *Downloads Folder*
- Install [Docker](https://docs.docker.com/engine/install/) (Windows - Install Docker Desktop and activate Linux containers)
- Install [Docker compose](https://docs.docker.com/compose/install/) (Only Linux)
- For Windows:  
  - Use **Windows Powershell**
  - Run as administrator `Set-ExecutionPolicy -ExecutionPolicy AllSigned`

## Container settings

- To change the password, modify the `ORACLE_PASSWORD` environment variable in the `docker-compose.yaml` file.

## Install container

- Clone repository: `git clone https://github.com/cristhianfdx/oracle-18c-xe.git`
- `cd oracle-18c-xe`
- Execute:
  - Linux: `./install.sh`
  - Windows `./install_windows.ps1` (**Use Windows Powershell**)

### Available commands

**Linux**
- Run container: `oraclestart`
- Stop container: `oraclestop`
- Run sqlplus: `sqlplus`

**Windows**
- Run container: `docker start oracledb`
- Stop container: `docker stop oracledb`
- Run sqlplus: `sqlplus`

### APEX Install

An example to install APEX into the default container is available [here](docs/apex-install.md).

### SSH into Container

In some cases you may need to login to the server to modify or test something on the file system.

```bash
docker exec -it oracledb bash -c "source /home/oracle/.bashrc; bash"

# Once connected to run sqlplus:
$ORACLE_HOME/bin/sqlplus

# Listener start/stop
$ORACLE_HOME/bin/lsnrctl stop
$ORACLE_HOME/bin/lsnrctl start
```

### Oracle Enterprise Manager

_Note: Flash is required_</br>

https://localhost:35518/em

### Uninstall Container

Execute:
  - Linux: `./uninstall.sh`
  - Windows `./uninstall_windows.ps1`

