# EX01 Developing a Simple Webserver
## Date:25.03.2024

## AIM:
To develop a simple webserver to serve html pages.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```
from http.server import HTTPServer,BaseHTTPRequestHandler

content='''
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home - Saveetha (Autonomous)</title>
    <link rel="icon" href="c:\Users\usera\OneDrive\Desktop\logo.jpg" type="image/x-icon">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
    <style>
        .icon {
            color: #cc324b;
            font-size: 14px;
            padding: 8px;
        }

        a {
            color: #cc324b;
        }

        a:hover {
            color: rgb(160, 157, 157);
        }

        .main {
            color: #cc324b;
        }

        .main:hover {
            color: rgb(160, 157, 157);
            display: block;
        }

        i:hover {
            color: rgb(160, 157, 157);
        }

        .bg {
            background-color: gainsboro;
        }

        .but {
            background-color: white;
            color: #cc324b;
            border: none;
            padding-top: 5px;
            padding-bottom: 5px;
            padding-left: 15px;
            padding-right: 15px;
            font-size: large;
            border-radius: 8%;
        }

        .but:hover {
            background-color: #bd7b86;
        }

        .im {
            padding-left: 15px;
            padding-top: 15px;
            padding-bottom: 15px;
            padding-right: 15px;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            z-index: 1;
        }
    </style>
    <link rel="stylesheet" href="c:\Users\usera\OneDrive\Desktop\WEB\web_pages\style.css">
</head>

<body>
    <div class="row border border-2 bg" style="height:65px; display: flex;">
        <div style="width: 6%;">
        </div>
        <div style="width: 26%;padding-top: 15px;">
            <i class="bi bi-twitter icon"></i>
            <i class="bi bi-youtube icon"></i>
            <i class="bi bi-facebook icon"></i>
            <i class="bi bi-linkedin icon"></i>
            <i class="bi bi-pinterest icon"></i>
            <i class="bi bi-whatsapp icon"></i>
            <i class="bi bi-instagram icon"></i>
        </div>
        <div style="text-align: right;width: 47%;padding-top: 15px;">
            <a href="" style="text-decoration: none;">Alumni </a><i class="bi bi-three-dots-vertical icon"></i>
            <a href="" style="text-decoration: none;"> Events </a><i class="bi bi-three-dots-vertical icon"></i>
            <a href="" style="text-decoration: none;"> Career </a><i class="bi bi-three-dots-vertical icon"></i>
            <a href="" style="text-decoration: none;"> Login </a><i class="bi bi-three-dots-vertical icon"></i>
            <a href="" style="text-decoration: none;"> SEC Portal</a>
        </div>
        <div style="width: 15%;padding-top: 15px;">
            <div class=" border border-0.1px rounded-4 border-black" style="height: 30px;">
                <form>
                    <i class="bi bi-search" style="padding-left: 6%;font-size: 14px;"></i><input type="text" name="name"
                        style="font-size: 14px; background-color:gainsboro;height: 25px;width: 160px; border:none;"
                        class="border=0" placeholder=" search...">
                </form>
            </div>
        </div>
        <div style="width: 6%;">
        </div>
    </div>
    <div class="row border border-3 bg" style="height: 100px;">
        <div style="width: 6%;">
        </div>
        <div class="im" style="width:26%;background-color: white;">
            <img src="c:\Users\usera\OneDrive\Desktop\WEB_LOGO-01.png" style="width: 360px;padding-top: 10px;">
        </div>
        <div style="width:54%;text-align: right; background-color: white; padding-top: 20px; font-size:large;">
            <nav class="navbar navbar-expand-lg ">
                <div class="container-fluid">
                    <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                        data-bs-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false"
                        aria-label="Toggle navigation">
                        <span class="navbar-toggler-icon"></span>
                    </button>
                    <div class="collapse navbar-collapse" id="navbarNavDropdown">
                        <ul class="navbar-nav">
                            <li class="nav-item">
                                <a class="nav-link main" aria-current="page" href="https://www.saveetha.ac.in/">Home</a>
                            </li>
                            <li class="nav-item dropdown">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    About
                                </a>
                                <ul class="dropdown-menu">
                                    <li><a class="dropdown-item"
                                            href="https://www.saveetha.ac.in/index.php/about/about-sec">About SEC</a>
                                    </li>
                                    <li><a class="dropdown-item"
                                            href="https://www.saveetha.ac.in/index.php/about/vision-mission">Vision &
                                            Mission</a></li>
                                    <li><a class="dropdown-item"
                                            href="https://www.saveetha.ac.in/index.php/about/president-s-message">President's
                                            Message</a></li>
                                    <li><a class="dropdown-item" href="#">Principal's Message</a></li>
                                    <li><a class="dropdown-item" href="#">Governing Council</a></li>
                                    <li><a class="dropdown-item" href="#">Facts and Highlights</a></li>
                                </ul>
                            </li>
                            <li class="nav-item dropdown">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    Departments
                                </a>
                                <ul class="dropdown-menu ">
                                    <li><a class="dropdown-item" href="#">Agricultral Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Artificial Intelligence & Data Science</a>
                                    </li>
                                    <li><a class="dropdown-item" href="#">Artificial Intelligence & Machine Learning</a>
                                    </li>
                                    <li><a class="dropdown-item" href="#">Bio Medical Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Chemical Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Civil Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Computer Science & Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Computer Science & Engineering (Cyber
                                            Security)</a></li>
                                    <li><a class="dropdown-item" href="#">Computer Science & Engineering (Internet of
                                            Things)</a></li>
                                    <li><a class="dropdown-item" href="#">Electrical & Electronics Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Electronics & Instrumentation Engineering</a>
                                    </li>
                                    <li><a class="dropdown-item" href="#">Electronics & Communication Engineering</a>
                                    </li>
                                    <li><a class="dropdown-item" href="#">Information Technology</a></li>
                                    <li><a class="dropdown-item" href="#">Master of Business Administration</a></li>
                                    <li><a class="dropdown-item" href="#">Mechanical Engineering</a></li>
                                    <li><a class="dropdown-item" href="#">Medical Electronics</a></li>
                                    <li><a class="dropdown-item" href="#">Science and Humanities</a></li>
                                    <li><a class="dropdown-item" href="#">Saveetha Consortium for Future Technologies
                                            (SCoFT)</a></li>
                                    <li><a class="dropdown-item" href="#">Saveetha Teaching Learning Centre</a></li>
                                    <li><a class="dropdown-item" href="#">Saveetha Centre for Foreign Languages</a></li>
                                    <li><a class="dropdown-item" href="#">Training</a></li>
                                </ul>
                            </li>
                            <li class="nav-item dropdown ">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    Life at SEC
                                </a>
                                <ul class="dropdown-menu ">
                                    <li>
                                        <a class="dropdown-item" href="#">
                                            Academic Life
                                        </a>
                                    </li>
                                    <li>
                                        <a class="dropdown-item" href="#">
                                            Student Life
                                        </a>
                                    </li>
                                </ul>
                            </li>
                            <li class="nav-item dropdown">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    Admissions
                                </a>
                                <ul class="dropdown-menu">
                                    <li><a class="dropdown-item" href="#">Admission Procedure</a></li>
                                    <li><a class="dropdown-item" href="#">Courses Offered</a></li>
                                </ul>
                            </li>
                            <li class="nav-item dropdown">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    Placements
                                </a>
                                <ul class="dropdown-menu">
                                    <li><a class="dropdown-item" href="#">Overview</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2024</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2023</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2022</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2021</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2020</a></li>
                                    <li><a class="dropdown-item" href="#">Placement 2019</a></li>
                                </ul>
                            </li>
                            <li class="nav-item dropdown main">
                                <a class="nav-link dropdown-toggle main" href="#" role="button"
                                    data-bs-toggle="dropdown" aria-expanded="false">
                                    Research
                                </a>
                                <ul class="dropdown-menu">
                                    <li><a class="dropdown-item" href="#">Saveetha Intramural</a></li>
                                    <li><a class="dropdown-item" href="#">Research Scheme</a></li>
                                    <li><a class="dropdown-item" href="#">Research Centre</a></li>
                                    <li><a class="dropdown-item" href="#">Research Advisory Board</a></li>
                                    <li><a class="dropdown-item" href="#">Research Faculty & Facilities</a></li>
                                    <li><a class="dropdown-item" href="#">Research Recognitions & Focus</a></li>
                                    <li><a class="dropdown-item" href="#">Incubation Centre</a></li>
                                    <li><a class="dropdown-item" href="#">Research Project Sanctioned</a></li>
                                    <li><a class="dropdown-item" href="#">Ongoing Research Projects</a></li>
                                    <li><a class="dropdown-item" href="#">Consultancy Projects</a></li>
                                    <li><a class="dropdown-item" href="#">Students Projects</a></li>
                                    <li><a class="dropdown-item" href="#">Hackathon Funding</a></li>
                                    <li><a class="dropdown-item" href="#">Downloads</a></li>
                                    <li><a class="dropdown-item" href="#">Remuneration

                                        </a></li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                </div>
            </nav>
        </div>
        <div style="width: 8%;background-color: #aaaaaacf;text-align: center;color: white;padding-top: 12px;">
            FOR<br>
            ADMISSION<br>
            89399902737
        </div>
        <div style="width: 6%;">
        </div>
    </div>
    <div style="display: flex;background-color: aliceblue;padding-top: 20px;">
        <div style="width: 6%;"></div>
        <div
            style="width: 20%; background-color:#cc324b;color: white; padding-left: 2%;padding-top: 2%;padding-bottom: 2%;font-size: x-large;">
            <p>ADMISSION ENQUIRY<br>
                <a href="">
                    <input type="button" class="but" value="APPLY NOW">
                </a>
                <br><br><br>Chat with Student<br>Ambassador<br>
                <a href="">
                    <input type="button" class="but" value="KNOW MORE">
                </a>
                <br><br><br>BLOGS<br>
                <a href="">
                    <input type="button" class="but" value="KNOW MORE">
                </a>

        </div>
        <div style="width: 2%;"></div>
        <div style="width: 66%;">
            <div id="carouselExampleInterval" class="carousel slide" data-bs-ride="carousel">
                <div class="carousel-inner">
                    <div class="carousel-item active" data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i1.jpeg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i2.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i3.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i4.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i5.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i6.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item " data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i7.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item" data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i8.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item" data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i9.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item" data-bs-interval="100">
                        <img src="c:\Users\usera\OneDrive\Desktop\i10.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item" data-bs-interval="1000">
                        <img src="c:\Users\usera\OneDrive\Desktop\i11.jpg" class="d-block w-100" alt="...">
                    </div>
                    <div class="carousel-item">
                        <img src="c:\Users\usera\OneDrive\Desktop\i12.jpg" class="d-block w-100" alt="...">
                    </div>
                </div>
                <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleInterval"
                    data-bs-slide="prev">
                    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                    <span class="visually-hidden">Previous</span>
                </button>
                <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleInterval"
                    data-bs-slide="next">
                    <span class="carousel-control-next-icon" aria-hidden="true"></span>
                    <span class="visually-hidden">Next</span>
                </button>
            </div>
        </div>
        <div style="width: 6%;"></div>
    </div>
    <div style="display: flex;background-color: aliceblue;padding-top: 25px;">
        <div style="width: 8%;"></div>
        <div class="im" style="width: 16%;background-color: #2b3333;"><img src="c:\Users\usera\OneDrive\Desktop\t1.jpg"
                alt="" width="210px"></div>
        <div style="width: 1%;"></div>
        <div class="im" style="width: 16%;background-color: #cc324b;"><img src="c:\Users\usera\OneDrive\Desktop\t2.jpg"
                alt="" width="210px"></div>
        <div style="width: 1%;"></div>
        <div class="im" style="width: 16%;background-color: #c59369;"><img src="c:\Users\usera\OneDrive\Desktop\t3.jpg"
                alt="" width="210px"></div>
        <div style="width: 1%;"></div>
        <div class="im" style="width: 16%;background-color: #cc324b;"><img src="c:\Users\usera\OneDrive\Desktop\t4.jpg"
                alt="" width="210px"></div>
        <div style="width: 1%;"></div>
        <div class="im" style="width: 16%;background-color: #2b3333;"><img src="c:\Users\usera\OneDrive\Desktop\t5.jpg"
                alt="" width="210px"></div>
        <div style="width: 8%;"></div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
        crossorigin="anonymous"></script>

</body>

</html>
'''

class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200) 
        self.send_header("content-type", "text/html")       
        self.end_headers()
        self.wfile.write(content.encode())

print("This is my webserver") 
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()
```
## OUTPUT:
![output1](<Screenshot 2024-03-25 153221.png>) 
![output2](<Screenshot 2024-03-25 153245.png>) 
![output3](<Screenshot 2024-03-25 153341.png>) 
![output4](<Screenshot 2024-03-25 153353.png>) 
![output5](<Screenshot 2024-03-25 160314.png>)

## RESULT:
The program for implementing simple webserver is executed successfully.
