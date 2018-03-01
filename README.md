# Project

## docker
	sudo apt-get install docker.io

	sudo docker pull ianchen/openface

	sudo docker images

	sudo docker run -t -i -v /home/ian/trans/:/root/trans/ ianchen/openface /bin/bash
	/trans/	為共享資料夾

	sudo docker exec -ti 889dd1c80687 bash

	sudo docker ps -a

container
	sudo docker stop 889dd1c80687
sudo docker start 889dd1c80687

主機-->container
	sudo docker cp test.jpg 4ffb102a8fcc:/root/openface/test-images/test.jpg
container-->主機 （用trans資料夾）
cp -a /root/openface /root/trans
	
放上dockerhub
sudo docker images
sudo docker push ianchen/openface

##squared L2 distance
./demos/compare.py images/examples/{betty1*,betty2*}

## note
放圖片: (obama, trump, hillary)
cd /root/openface
mkdir training-images
mkdir ./training-images/obama/

複製檔案到conainer (檔案放在home
查container ID:
sudo docker ps

http://www.yaru.news/index.php/docker/1-docker-copy-file-from-container-to-host
sudo docker cp Obama.jpg 4ffb102a8fcc:/root/openface/training-images/obama/Obama.jpg
（另ㄧ個terminal）

再開啟已經存在的container
https://philipzheng.gitbooks.io/docker_practice/content/container/enter.html
sudo docker exec -ti 889dd1c80687 bash
sudo docker ps -a
sudo docker stop 889dd1c80687
sudo docker start 889dd1c80687

Run the openface scripts: (build
	
	刪cache
	~/openface/aligned-images# rm cache.t7
	rm -r aligned-images
	mkdir aligned-images

到openface路徑:

./util/align-dlib.py ./training-images/ align outerEyesAndNose ./aligned-images/ --size 96

./batch-represent/main.lua -outDir ./generated-embeddings/ -data ./aligned-images/

./demos/classifier.py train ./generated-embeddings/
run:
	mkdir test-images
	照片放入test-images
	sudo docker cp test.jpg 4ffb102a8fcc:/root/openface/test-images/test.jpg

去openface
./demos/classifier.py infer ./generated-embeddings/classifier.pkl ./test-images/test.jpg

拿出來
	cp -a /root/openface /root/trans

放進去
	sudo docker cp training-images 4ffb102a8fcc:/root/openface/
sudo docker cp obama2.jpg 4ffb102a8fcc:/root/openface/images/examples

