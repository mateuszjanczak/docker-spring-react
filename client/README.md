# React
## Docker Scripts

In the project directory, you can run:

### Development

```
docker build --tag client-dev .
docker run -p 3000:3000 client-dev
```

### Production

```
docker build --tag client-prod -f Dockerfile.prod .
docker run -p 80:80 client-prod
```