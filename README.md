# MAXiBMS Edge

## Deploy

Clone the deploy project to MAXiCom

``` bash
git clone https://github.com/NTM3110/maxicom-bms.git
```


Move to the directory and start the docker service

```bash
cd maxicom-bms
docker compose up -d openmuc --build
```


Clone the autostart and open app at desktop to MAXiCom

```bash
git clone https://github.com/NTM3110/maxicom-bms-setup-deploy.git
```

Run to activate the service

```bash
sudo chmod +x install.sh
sudo ./install.sh
```


Reboot device to check

```bash
sudo reboot
```


## Coding Instruction

Build the app

```bash
cd maxicom-bms
./framework/bin/openmuc build_openmuc
```

> [!CAUTION]
> 
>  
>

The code of build_openmuc is as follows:
```bash
  

./gradlew :openmuc-lib-rest1:clean :openmuc-lib-rest1:build -x test

cp ./build/libs-all/openmuc-lib-rest1-0.20.0.jar ./framework/bundle/

./gradlew :openmuc-server-restws:clean :openmuc-server-restws:build -x test

cp ./build/libs-all/openmuc-server-restws-0.20.0.jar ./framework/bundle/

  

./gradlew :openmuc-driver-modbus:clean :openmuc-driver-modbus:build -x test

cp ./build/libs-all/openmuc-driver-modbus-0.20.0.jar ./framework/bundle/

....................
```

I build all the components to file jar and cp the .jar to the bundle in framework to be active.
-> If adding a new component that needs to be update frequently need to add it to build_openmuc function in openmuc bash file.


Start the app

```bash
./framework/bin/openmuc start -fg
```



