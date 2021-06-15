# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

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