The latest image for Arcade Analytics on Docker  Hub doesn't work out of the box. I figured out this workaround to obtain and run a working Arcade Analytics container. 

**Step 1:** download the files available on github, unzip, rename folder and remove zip:
```bash
curl -LJO http://github.com/ArcadeData/arcadeanalytics/archive/master.zip 
unzip arcadeanalytics-master.zip
mv arcadeanalytics-master arcadeanalytics
rm arcadeanalytics-master.zip
```

**Step 2:** download the 'recipe' files
```bash
curl -LJO https://github.com/ArcadeData/arcadeanalytics-recipes/archive/master.zip 
unzip arcadeanalytics-recipes-master.zip
mv arcadeanalytics-recipes-master arcadeanalytics-recipes
rm arcadeanalytics-recipes-master.zip
```

**Step 3:** Move the orientdb3 yml in the arcade analytics docker folder
```bash
mv arcadeanalytics-recipes/recipes/orientdb3.yml arcadeanalytics/src/main/docker/orientdb3.yml
```

**Step 4:** point to the orientdb3 yml in the app.yml. To do that, open the app.yml by typing
```bash
nano arcadeanalytics/src/main/docker/app.yml
```
Modify the line 43 replacing `file: orientdb2.yml` by `file: orientdb3.yml` (ie. erase 2 and write 3 instead). On the next line, replace `service: arcadeanalytics-orientdb` by `service: arcadeanalytics-orientdb3`(ie. write 3 at the end of the line)
Type `Ctrl+x` to exit nano text editor, and then `y` and press `Enter` to save the changes.

**Step 5:** run orientdb3. Docker will automatically pull it first from Docker Hub if orientdb is not already present on the machine, which will take a few more minutes 
```bash
 docker run arcadeanalytics/orientdb3
```
This will keep the current terminal busy (using the -d options to run in the background fails).

**Step 6:** Launch arcadeanalytics in another terminal
Open a new terminal without closing the other one and type:
``` bash
docker-compose -f src/main/docker/app.yml up
```

Then open your browser and type http://localhost:8080 and login as user with password user. The terminal also displays another IP to access the application from other machines. See the official [Arcade Analytics readme](https://github.com/ArcadeData/arcadeanalytics/blob/master/README.md)  for further instructions.

I can't believe it has to be so complicated. There must be a much simpler way, but I'm not very familiar with docker. Any suggestion to make this more straightforward (using only docker hub for instance) would be most welcome.
