# BDS_YOLO_on_NCS2

### To run the flask api server
1. pip install Flask (prefered in virtualenv) https://flask.palletsprojects.com/en/1.1.x/installation/
2. check your device ip with `ifconfig |grep inet`
3. run `python3 app.py`
4. POST request format:

address: `http://{device ip}:5000/detect_objects`

request body:
```Json
{ 
	"image": "Base 64 encoded image, as a string",
    "mode": "“parallel” or “ensemble”",
    "models": "one or more model names, as an array"
}
```

Example response:

with 'mode' == 'parallel'
```Json
{
    "model1": [
        {
            "bbox": [
                1,
                0,
                200,
                200
            ],
            "class": "person",
            "score": 0.838
        }
    ],
    "model2": [
        {
            "bbox": [
                1,
                0,
                200,
                200
            ],
            "class": "person",
            "score": 0.838
        }
    ],
    "model3": [
        {
            "bbox": [
                1,
                0,
                200,
                200
            ],
            "class": "person",
            "score": 0.838
        }
    ]
}
```

with 'mode' == 'ensemble'
```Json
{
    "all": [
        {
            "bbox": [
                1,
                0,
                200,
                200
            ],
            "class": "person",
            "score": 0.838
        }
    ]
}
```
