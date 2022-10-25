
## Initial Setup 

0. Prerequisite

  1. Connect pi@dwc2Mesh to wifi (internet provider)
      - The local computer/laptop at the site should be connected to dwc2Mesh, so that remote developers can access.
      - pi@weather will connect to dwc2Mesh as well
  2. Turn on pi@lichen, pi@weather (pi@moss, pi@mushroom)
  3. Choose dwc2Mesh internet on your laptop
  4. Open a browser, enter 192.168.0.1, you will see iptime manager website (id, pw)
      - **Advanced Setup** menu => **LAN Setup** list => `192.168.0.102` (lichen), `192.168.0.105` (weather) pi networks.
  5. Open a terminal and type `ping` commands to check pi networks
      ```
        ping 192.168.0.102
        ping 192.168.0.105
      ```
  6. Troubleshoot pi@weather
      - connect HDMI from pi@weather to digital screen
      - connect keyboard to pi@weather
      - Turn on pi@weather, Ctrl+C or Command+C twice
          ```
          ip a
          sudo vi /etc/wpa~~~~
          ```
      - how we solved in 2022.10.19
        - dwc2Mesh only had 5G network, but pi@weather couldn't use 5G.
        - donghoon opened 2G network from dwc2Mesh, then pi@weather connected to dwc2Mesh via 2G network.
  7. Troubleshoot and access to pi@creatures
      - Connect your laptop wifi to pi@lichen or pi@moss or pi@mushroom (NOT dwc2Mesh)
      - in your terminal `> ssh pi@192.168.100.1 -p 22` (check pw)
