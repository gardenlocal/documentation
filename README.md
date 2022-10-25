
## Initial Setup 

### Prerequisite

1. Connect pi@dwc2Mesh to wifi (internet provider)
    - The local computer/laptop at the site should be connected to dwc2Mesh, so that remote developers can access.
    - pi@weather will connect to dwc2Mesh as well
2. Turn on pi@lichen, pi@weather (pi@moss, pi@mushroom)
3. Choose dwc2Mesh internet on your laptop
4. Open a browser, enter 192.168.0.1, you will see iptime manager website (id, pw)
    - **Advanced Setup** menu => **LAN Setup** list => `192.168.0.102` (lichen), `192.168.0.105` (weather) pi networks.
5. Open a terminal and type `ping` commands to check pi networks
    ```
      $ ping 192.168.0.102
      $ ping 192.168.0.105
    ```
6. Troubleshoot pi@weather
    - connect HDMI from pi@weather to digital screen
    - connect keyboard to pi@weather
    - Turn on pi@weather, Ctrl+C or Command+C twice
        ```
        $ ip a
        $ sudo vi /etc/wpa~~~~
        ```
    - how we solved in 2022.10.19
      - dwc2Mesh only had 5G network, but pi@weather couldn't use 5G.
      - donghoon opened 2G network from dwc2Mesh, then pi@weather connected to dwc2Mesh via 2G network.
7. Troubleshoot and access to pi@creatures
    - Connect your laptop wifi to pi@lichen or pi@moss or pi@mushroom (NOT dwc2Mesh)
    - in your terminal `$ ssh pi@192.168.100.1 -p 22` (check pw)

### Test Run
If you're running or installing the codes on a brand new pi, make sure you install libraries in this ref: https://github.com/CezarMocan/dwc-v2#first-time-setup-frontend

1. Connect your laptop to `dwc2Mesh` wifi
2. In termial, type `ssh pi@192.168.0.102` with password.
    - Let's assume we're connecting to lichen pi.
    - If you want to work on pi@moss, it's `ssh pi@192.168.0.101`
    - For pi@mushroom, it's `ssh pi@192.168.0.103`
3. Let's find the repository, deploy and run client-side (`canvas`)
      ```
        $ cd works
        $ cd dwc-v2
        $ cd canvas
        $ npm run deploy
        $ sudo service nginx restart
      ```
   You would see something like this.
   
   ![run client-side codes](https://user-images.githubusercontent.com/17012862/197684896-5e4c0aaa-d327-482e-8ab6-8cf7cd6ecc79.png)

4. Let's check if any server is running or stopped.
      ```
        $ pm2 list
      ```
      
      If there is any server already running, you would see something like below.
      
      ![pm2 list server](https://user-images.githubusercontent.com/17012862/197684911-cd0e91dd-ce2a-41ab-9b6a-6b610af787d1.png)

5. If any server shows `stopped` status, run this command
    - `$ pm2 start {name}`
    - ![example](https://user-images.githubusercontent.com/17012862/197685263-61a0a21d-96db-45fa-944a-f698ed381669.png)

6. If you want, you can stop and re-start the server
    ```
      $ pm2 stop {name}
      $ pm2 start {name}
    ```
7. Open your internet browser. Type the url of according pis
    - lichen: `192.168.0.102`
    - moss: `192.168.0.101`
    - mushroom: `192.168.0.103`
    - weather: `192.168.0.105:3005/weather`
        - you can open weather url whenever as long as your computer is connected to `dwc2Mesh` wifi.
    - To check the admin view, just add `/admin` at the end of creature urls.
        - ex) `192.168.0.102/admin`




