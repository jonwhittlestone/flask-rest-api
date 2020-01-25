# Simple Flask REST API

## Steps to Run Locally

0. Activate python3 `virtualenv` and install deps
1. Run flask dev server
    `python run.py`
2. View products in a browser - [http://localhost:5000/products](http://localhost:5000/products)
3. Create a product with CURL

    ```
    curl -X POST \
    http://localhost:5000/product-create \
    -F 'name=Google Pixel 2' \
    -F price=300.0
    ```
4. View the products


    ```
    curl -X GET \
    http://localhost:5000/api/product \
    -H 'Accept: application/json' \
    -H 'cache-control: no-cache'

    [
    {
        "category": null,
        "name": "Google Pixel 2",
        "price": 300
    },
    ]
    ```

## Steps to build and run with Docker container

1. Build it


        docker build -t howapped-products .

2. Run it on port 8000 forwarded to 5000


        docker run -d -p 8000:5000 howapped-products:latest

3. Create a product with CURL

    ```
    curl -X POST \
    http://localhost:8000/product-create \
    -F 'name=Nokia 3210' \    
    -F price=1500.0
    ```

4. View product


        curl -X GET \
        http://localhost:8000/api/product \
        -H 'Accept: application/json' \
        -H 'cache-control: no-cache'

        [
        {
            "category": null,
            "name": "Google Pixel 2",
            "price": 300
        },
        ]
