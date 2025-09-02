Clone the repo 

docker build -t dbimage database/
docker build -t authimage auth/
docker build -t bookimage book/
docker build -t borrowimage borrow/
docker build -t appimage .


docker network create mynet


docker run -d --name db -p 3306:3306 --network mynet dbimage
docker run -d --name auth_service --network mynet  -p 5001:5001 authimage
docker run -d --name book_service -p 5002:5002 --network mynet bookimage
docker run -d --name borrow_service  -p 5003:5003 --network mynet borrowimage
docker run -d --name frontend  -p 5000:5000 --network mynet  appimage

 
