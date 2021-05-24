# Sudoku_solver
Project Description: 
Sudoku is one of the most popular puzzles of all time. The goal of Sudoku is to Vill a 9x9 grid  such that each row, each column and 3x3 grid contains all of the digits between 1 to 9.In this  project we aim to create a real time Sudoku solver which recognizes the elements of Sudoku  puzzles and provides a digital solution using Computer vision.Sudoku Solver is the collection  of  very  basic  image  processing  techniques.  A  very  good  way  to  start  is  the  OpenCV  library  which can be compiled on almost all the platforms.  
Problem Statement: 
The  intuition  and  knowledge  of  increasing  your  mental  strength  of  this  new  generation  is  decreasing  day  by  day  to  overcome  one  such  problem  and  to  provide  answers  instantly  to  users. We have made a Real-Life Sudoku Solver.  It can be used  to solve Sudoku in a smarter  and more easy way with the help of Image processing and solve sudoku problems instantly for  the enthusiasts, beginners and even professionals who consider this challenging. The need of  the hour  to make  this project was due  to  the  fact  that in  India most  of  the people who play  sudoku use the newspaper platform to play it and eventually they have to wait for a whole day  to get  the answers of  the previous day sudoku which  they solved. But not anymore with  the  help  of  Computer  vision  we  have  created  a  way  for  them  to  get  their  answers  instantly  by  using our technology.  
Analysis: 
3.1 Hardware Requirements  
Unsolved Sudoku (9*9)  from a sheet of Paper or phone screen .  
3.2 Software Requirements  
We have used OpenCV for image processing. Therefore Basic knowledge of opencv regarding  use  applications  and  syntax  are  essential  here.  It  is  a  library  in  python  that  helps  with  computer  vision  and  is  more  convenient  as  it  provides  a  large  number  of  functions  for  conversions and processing. It can be learned on opencv.org.  
Numpy for numeric handling. Basic knowledge of numpy including syntax and computational  parts  are  essential  to  form  image  arrays.  It  is  a  library  in  python  used  to  perform  mathematical computation. it can be learned from numpy.org.  
Tersseract for Python used in image to text conversion. This is also known as pytersseract and  is used for object recognition. Python-tesseract is an optical character recognition (OCR) tool  for python. That is, it will recognize and "read" the text embedded in images. It can be learned  from pype.org.  
STEP 1: Grab the Sudoku grid from Webcam Image.  
• Capture the video frame continuously(cv2.videoCapture)   
• We take the input frame and convert it to gray scale(cv2.cvtColor).  
• Blur the Image using Gaussian Blurring (cv2.gaussianBlur).  
• Apply Adaptive Thresholding (cv2.adaptiveThreshold).  
• We get a binary Image.  
• Then we Find all contours(cv2.findContours).  
• Extract the contour with the biggest area (cv2.contourArea).  
• Locate  4  corners  of  the  contour  and  determine  the  upper  left,  upper  right,  bottom  left,  bottom right corners.   
• We have used 2 Criteria for Qualifying a Sudoku grid i.e. 4 angles must be approximately 90  degrees and  4 sides must have approximately equal lengths .  
• If the biggest contour is a square(required),  from 4 corners, we apply cv2.wrapPerspective  to get a nice and able Sudoku Grid Image. 

STEP 2: Extract and Detect Digits.  
• 
• This  Step  will  begin  by  Image  processing  and  chopping  Sudoku  create  images  into  9x9  Square blocks .  
• As there is so much noise in these images and if we feed them into Model now the accuracy  will be about 10% (which is random).  
• So Before feeding them into for Digit Recognition we need to clean them up first .  • Remove Black lines near 4 edges  (if any) .  
• Take  only  the  largest  connected  component  (cv2.connectedComponentWithStats)  ,  which  should correspond to digit and turn the rest into white pixels .  
• Resize these images to 28 x 28  
• We leave out any white cells  
• Criteria 1: The image has too little black pixels (sum of all pixels are too big)   • Criteria 2: The image has a huge white area in the centre .   
• After applying these two criteria we should be able to remove all white cells  • Now we centred upon  - empty images by its centre of mass we will do the same thing on  the training data set to make sure the image structure is similar .  
• To get the best result I centred train image by Centre of Mass. I did the same thing (as we  mentioned before)  to our Sudoku digital images. This improve  the accuracy  to more  than  99% . 
• Finally , let's recognise those digits !  
• With the advanced technology we have today , this was a simple task .  • We wanted to use Convolutional Neural Network (CNN) but were not able to feed in images  so we have used pytesseract  .  
• Python-tesseract is an  optical  character  recognition  (OCR)  tool  for  python.  That is, it will  recognize  and  “read”  the  text  embedded  in  images.Python-tesseract  is  a  wrapper  for  Google’s Tesseract-OCR Engine. Additionally, if used as a script, Python-tesseract will print  the recognized text instead of writing it to a Vile.

STEP 3: Solve the puzzle and Print the solution.  
• The third  step is to solve the Sudoku puzzle and print the solution back on the warp image.  • After the Digits are being Recognised as Text , in the Solving part we have used Breadth First  Search as our sudoku algorithm.  
• The simplest way to solve a Sudoku puzzle would be to simply search for the answer one cell  at  a  time.  The  two  most  basic  methods  of  search  are Depth  First(DFS)  and Breadth  First  Search(BFS).  From  which  we  have  Chosen  BFS  to  solve  .This  algorithms  make  use  of  backtracking once  they have explored a branch in  their search path sufViciently  to go back  and expand other paths.  
• Then  we  just  Print  the  solved  Sudoku  that  we  got  as  an  output  on  warp  image  using  result=write_solution_on_image() function .  

Conclusion and Future Scope:  
We have made a Real-Time Sudoku solver to instantly solve and provide answers to people making  them learn and check their knowledge of sudoku solving . As most of the people in India play  sudoku on the newspapers and eventually have to wait for a whole day to get the answers this  software will help them getting the Solution Instantly .We have created this with the Help of  Computer vision. When we play and solve sudoku problem in front of the camera it detects the  image and with the image filtering techniques convert the image into greyscale and then apply  Gaussian blurring and Thresholding so that we get a binary image. We then find all the contours at  them to get the biggest area which is the sudoku grid . The main task then is to extract and detect  digits which we have done using pytesseract , it recognises and read the text in images . After the  extraction of digits we apply the solving algorithm to get the solution of the sudoku problem and  then print and on the warp image .  
For Future scope we can develop an application based on this which will be user-friendly and also  provide better user experience .
