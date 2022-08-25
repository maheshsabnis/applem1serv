# Build Image
docker build --pull --build-arg ARCH=arm64v8 -t aspnetapp .

# Run Image
docker run --rm -p 8000:80 aspnetapp