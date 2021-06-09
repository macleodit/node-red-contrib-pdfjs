A node to help extract text contents from a pdf. Uses the Mozilla library found at [https://github.com/mozilla/pdfjs-dist](https://github.com/mozilla/pdfjs-dist) to extract text data.

## Inputs
#### payload
Either a buffer object that corresponds to a pdf file or a filepath leading to a pdf file to be decoded.	

## Config
#### filename
If a file path/object is not provided in the payload, A file path to a pdf file should be provided here to be decoded.

#### Order text
Check this option to force the text to be ordered top down using the y value if 'from top to bottom' is selected, or ordered left to right by it's x value if 'from left to right' is selected. If both options are selected, it will order from top to bottom, then left to right.

#### Merge text with next text
When inserting text into output payload array, if the previous text inserted has the same x value (are in the same column), or same y value (are in the same row), it will concatenate the string to be inserted with the previous string with a space instead.

## Outputs
#### payload
Results of the parsing will be returned as an array with each element in the array corresponding to a page in the pdf. Each page in the array is stored as an array of objects which can be seen below.
```
[
	{
		"p": 1, // order on the page
		"x": 328.78, // distance away from the right edge
		"y": 1175.676, // distance away from the bottom of the page
		"t": "Survey Responses 1/02/19 - 31/04/19" // text content
	},
	{
		"p": 2, 
		"x": 428.78, 
		"y": 1175.676, 
		"t": "Survey Responses 1/05/19 - 31/07/19"
	}
]
