Questions to the moodle are submitted as a xml files, the documentation of the xml format
and types of questions could be found [here](https://docs.moodle.org/38/en/Moodle_XML_format).

You can write an xml file, or you can use `quizzes_xml.py` script to convert a text file to the 
xml file. The script does not support all types of qestions, but it should work well for single 
choice questions,  multi choice question and True/False type of question. 

This directory contains the example of questions in txt file, and the xml file, that is an output of the
python script: 


* `questions.xml` - the xml file with all the questions (the file was created from the txt file using python script `quizzes_xml.py`)


* `questions.txt` - contains all the questions, using format:

      qst| What is your question?

      A| your answer A

      B| your answer B

      C| your answer C

      D| your answer D

      Answer| correct answers, e.g. "a, c"

      type| "multi" (or "single", optional the default is "single" if one answer provided, and "multi" otherwise)

* `quizzes_xml.py` - python script that converts txt file to xml using the moodle spec.
