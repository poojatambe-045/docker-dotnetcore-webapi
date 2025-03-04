docker build -t demo-image .

docker run -d --name demo-c -p 8080:8080 demo-image

start "http://localhost:8080/WeatherForecast/" 