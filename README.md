
# CURRICULUM VITAE
## Luca Fontanili


```python
import pandas as pd
pd.set_option('max_colwidth', 1000)
from IPython.core.display import display, HTML
import matplotlib.pyplot as plt
import numpy as np

import matplotlib.pyplot as plt
%matplotlib inline

display(HTML("""
<style>
.output {
    display: flex;
    align-items: center;
    text-align: center;
}
</style>
"""))
```



<style>
.output {
    display: flex;
    align-items: center;
    text-align: center;
}
</style>



## PERSONAL INFORMATION


```python
def load_map_frame():
    with open('map_frame.html') as f:
        return f.read()

import sqlite3
conn = sqlite3.connect('cv.db')
lf = pd.read_sql_query('SELECT * FROM users WHERE id="luca fontanili"', conn)
lf = lf.set_index('id')
display(HTML('<center><table><tr><td><img src="profile.jpg" width=200/>{}</td><td>{}</td></table></center>'
             .format(lf.T.to_html(escape=False), load_map_frame())))
```


<center><table><tr><td><img src="profile.jpg" width=200/><table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>id</th>
      <th>luca fontanili</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>email</th>
      <td>luca.fontanili93@gmail.com</td>
    </tr>
    <tr>
      <th>skype</th>
      <td>luca.fontanili</td>
    </tr>
    <tr>
      <th>sex</th>
      <td>Male</td>
    </tr>
    <tr>
      <th>birthdate</th>
      <td>22/01/1990</td>
    </tr>
    <tr>
      <th>nationality</th>
      <td>Italian</td>
    </tr>
  </tbody>
</table></td><td><iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2831.1517727885257!2d10.327056116089658!3d44.798095479098734!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47806ae0cec03315%3A0x63674c9ddee412c0!2sBorgo+Riccio+da+Parma%2C+34%2C+43121+Parma+PR!5e0!3m2!1sen!2sit!4v1544393049528" width="600" height="450" frameborder="0" style="border:0" allowfullscreen></iframe></td></table></center>


[![GitHub](https://img.shields.io/badge/GitHub-lucafon-blue.svg)](https://github.com/lucafon)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-lucafontanili-green.svg)](https://www.linkedin.com/in/luca-fontanili/)

[![Pypi](https://img.shields.io/badge/Pypi-lucafon-orange.svg)](https://pypi.org/user/lucafon/)

_______________
## WORK EXPERIENCE



```python
def plot_working_experience(employee=None, size=700):
    if employee is None:
        raise Exception('Do you work on your own?')
    from bokeh.plotting import figure, output_notebook, show
    from bokeh.models import ColumnDataSource, LabelSet

    output_notebook()

    work_experiences = pd.read_sql_query('SELECT * FROM work_experiences where employee="{}"'.format(employee), conn)

    keywords = work_experiences.keyword
    randoms = np.random.random_sample((len(keywords),))
    source = ColumnDataSource(data=dict(
        x=np.random.random_sample((len(keywords),))*2,
        y=np.random.random_sample((len(keywords),)),
        keywords=keywords,
        descriptions=work_experiences.description

    ))

    TOOLTIPS = """
        <div style="width:300px">
            <span style="font-size: 17px;"><b>@keywords</b></span>
            <span style="font-size: 15px;">@descriptions</span>
        </div>
    """

    p = figure(plot_width=size, plot_height=size, tooltips=TOOLTIPS, toolbar_location=None)
    p.y_range.start = -0.1
    p.y_range.end = 1.1
    p.x_range.start = -0.2
    p.x_range.end = 2.2

    p.circle('x', 'y', size=15, source=source, color="#480968")

    labels = LabelSet(x="x", y="y", text="keywords", y_offset=-30, text_font_size="10pt", text_color="#555555",
                      source=source, text_align='center')
    p.add_layout(labels)

    show(p)
```

### March 2015 - Present, Computer Engineer – Software Development Leader
<img src="https://www.sia.eu/sites/all/themes/sia/logo.png" width=50 align="right">
#### Ubiq S.R.L. - SIA Group, Parma/Milan
**Business or sector** Computer Engineering, Big Data, Machine Learning


```python
plot_working_experience('Ubiq')
```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="43203">Loading BokehJS ...</span>
    </div>











  <div class="bk-root" id="1b73c399-5a1c-4875-8c6e-beb9ee98cd53"></div>





_________________
### August 2014 - February 2015, Software Engineering Intern
<img src="https://www.datalogic.com/images/logo.png" width=90 align="right">
#### Datalogic ADC Inc, 55 W Del Mar Blvd, Pasadena (CA)

**Business or sector** Computer Vision


```python
plot_working_experience('Datalogic', 500)
```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="49307">Loading BokehJS ...</span>
    </div>











  <div class="bk-root" id="79f82ace-248d-4989-8d3a-506e77210367"></div>





__________________
## EDUCATION AND TRAINING
### September 2012 - March 2015, Master's Degree in Computer Engineering QEQ7
<img src="https://www.unibo.it/it/logo-unibo.png" width=90 align="right">
#### University of Bologna, Bologna

* Computer vision, data mining, use of Hadoop framework, information security, artificial intelligence, computer networks, mobile systems, OpenCV, Java, C/C++, VHDL, IT, Real-Time systems.

**Thesis** *Development of parallel processing approach to compute Zero-mean Normalized Cross- Correlation. CUDA framework has been used to develop fast approach to detect characters in images, using Template Matching approach, based on Zero-mean Normalized Cross-Correlation measure.*

**Final Grade** 110/110 with Honours
______________
### September 2009 - July 2012, Bachelor's Degree in Computer Engineering QEQ6
<img src="https://www.unipr.it/sites/default/files/styles/paragrafo/public/contenuto_generico/immagini/unipr_centrato_1riga_pos_rgb.jpg?itok=SkbDQ2gI" width=90 align="right">
#### University of Parma, Parma
* Computer science, mathematics, physic, industrial robotics, web programming, electronics, automatics, computer graphics, software engineering, Java, C/C++, OpenGL

**Thesis** *A Machine Learning project based on arm gesture recognition and humanoid imitation. Arm gestures are acquired by inertial motion sensors and modelled in an OpenGL 3D virtual space. A new method based on Functional Principal Component Analysis is used in MATLAB for both a supervised clustering of training data and gesture recognition. Recognized gestures are imitated by a small humanoid robot*

**Final grade** 107/110

______________
## PERSONAL SKILLS
### LANGUAGES

  
| Language | Listening | Reading | Spoken Interacion | Spoken Production | Writing |
| -------- | --------- | ------- | ----------------- | ----------------- | ------- |
| Italian | MT | MT | MT | MT| MT |
| English | C2 | C2 | C2 | C2 | C1 |
| German | A1 | A1 | A1 | A1 | A1 |

*Levels: A1/2: Basic user - B1/2: Independent user - C1/2 Proficient user - MT Mother Tongue*

### COMMUNICATION SKILLS
I gained good communication skills speaking and interacting with customers and clents. I'm also part of the Data Science and Artificial Intelligence Group in Parma, and I hold a speeck about Machine Learning topics once every few months, usually in front of dozens of peoples.

### ORGANISATIONAL/MANAGERIAL SKILLS
Excellent social/organisational skills acquired during my experience as Team Leader. During my time in Ubiq I had to completely manage different projects with many clients, organizing work packages and distributing them across the team members.

### JOB-RELATED SKILLS


```python
def show_skills_plot(x_label, skills=None):
    if skills is None:
        raise Exception("you should have at least one skill, shouldn't you?")
    from bokeh.io import show, output_notebook
    from bokeh.plotting import figure
    from bokeh.palettes import RdPu9
    from bokeh.transform import factor_cmap
    from bokeh.models import HoverTool, ColumnDataSource
    output_notebook()

    
    source = ColumnDataSource(skills)

    p = figure(plot_width=800, plot_height=400, title="Experise level",
               x_range=list(skills.description), toolbar_location=None)

    index_cmap = factor_cmap('type', palette=RdPu9, factors=sorted(skills.type.unique()), end=1) 
    p.vbar(x='description', top='level', width=1, source=source,
           line_color="white", fill_color=index_cmap)

    p.y_range.start = 0
    p.y_range.end = 10
    p.x_range.range_padding = 0.1
    p.xgrid.grid_line_color = None
    p.xaxis.axis_label = x_label
    p.xaxis.major_label_orientation = 1.2
    p.outline_line_color = None

    hover = HoverTool()
    hover.tooltips = [
        ('Name', '@description'),
        ('Type', '@type'),
        ("Details", "@tooltip")
    ]
    p.tools.append(hover)


    show(p)

job_skills = pd.read_csv('job_skills.csv', sep=';')
```

**Programming Languages**


```python
show_skills_plot('Programming Languages', job_skills[job_skills.type == 'Programming Language'])
```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="3356">Loading BokehJS ...</span>
    </div>











  <div class="bk-root" id="19d7299b-2ada-4368-84d0-4a707c5b2d20"></div>





**Other job-related skills**


```python
show_skills_plot('Skills grouped by type', job_skills[job_skills.type != 'Programming Language'])
```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="2938">Loading BokehJS ...</span>
    </div>











  <div class="bk-root" id="828f7d01-4e2e-4f41-9768-cb1be1fdcbcb"></div>





### OTHER SKILLS
**Sport**: 
* American Football, 4 years’ experience in the Parma Panthers, interaction with American staff and players. Participation in European Championship with the Italian National American Football team
* Development of projects of personal interest using latest mobile and web programming languages (Android, HTML, CSS, SQL, JavaScript, Python) and tools (Nutch crawler, SonarQube, Tesseract).

**Driving License**: B (own car)
______________
## ADDITIONAL INFORMATION
**Publications**

Arm Gesture Recognition and Humanoid Imitation Using Functional Principal Component Analysis,<br>
J. Aleotti, A. Cionini, L. Fontanili, S. Caselli,<br>
IEEE/RSJ International Conference on Intelligent Robotics and Systems (IROS),<br>
Tokyo, November 2013

**Honours and awards**

Bronze medal of sporting merit given by CONI

**Certifications**

* Machine Learning, Stanford University, [Coursera, #FGYRSK7XD8XG](https://www.coursera.org/account/accomplishments/verify/FGYRSK7XD8XG)
* Using Python for Research, Harvard University, [edX, #f079493d7801420388179e219e2a9d63](https://courses.edx.org/certificates/f079493d7801420388179e219e2a9d63)

**Projects**

* Ti Frutta – The very first "cash back" app in Italy that allows the customer to earn by shopping
* F Abbigliamento – development of the Fontanili Abbigliamento website using Wordpress CRM.
* CV – Eye Detector: development of an eye detector in C++ based on Normalized Cross Correlation, robust to light variation
* DSS – Hadoop: implementation in Apache Hadoop environment of the Distributed Solving Set algorithm for outlier detection in large distributed data sets, using the MapReduce model
* Parma Panthers Official:  development of the Android official application of the Parma Panthers, the American Football team 4 times champion of Italy in the main championship
* PicoPic: VHDL project of a Peripheral Interface Controller for a stereo vision system on FPGA, with a 8 bit RISC microprocessor PicoBlaze
* Wikiquote Search Engine: implementation of a web crawler for Wikiquote based on Apache Nutch and development of a Java search engine based on Apache Solr
* [pysqoop](https://pypi.org/project/pysqoop/): a Python package that lets you sqoop into HDFS data from RDBMS using Apache Sqoop (installable via pip)
* Member & Speaker of the Data Science & AI Group in Parma

______________
## LATEST STUDIES


```python
pd.read_sql_query('SELECT * FROM books order by status desc, author asc', conn)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>author</th>
      <th>status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mastering Java Machine Learining</td>
      <td>Kamath, Uday</td>
      <td>reading</td>
    </tr>
    <tr>
      <th>1</th>
      <td>The Art of Computer Programming, Fundamental Algorithms</td>
      <td>Knuth, Donald</td>
      <td>reading</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Test-Driven Development</td>
      <td>Beck, Kent</td>
      <td>read</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Effective Java</td>
      <td>Bloch, Josua</td>
      <td>read</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Design Patterns</td>
      <td>Gamma, Helm, Johnson, Vlissides</td>
      <td>read</td>
    </tr>
    <tr>
      <th>5</th>
      <td>97 Things Every Programmer Should Know</td>
      <td>Henney, Kevlin</td>
      <td>read</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Clean Code</td>
      <td>Martin, Robert C.</td>
      <td>read</td>
    </tr>
    <tr>
      <th>7</th>
      <td>The Clean Coder</td>
      <td>Martin, Robert C.</td>
      <td>read</td>
    </tr>
  </tbody>
</table>
</div>



______________
## MY DAY


```python
from math import pi

import pandas as pd

from bokeh.io import output_notebook, show
from bokeh.palettes import Category20
from bokeh.plotting import figure
from bokeh.transform import cumsum

output_notebook()

x = {
    'Sleep': 6.5/24,
    'Work': 9/24,
    'Gym': 1.5/24,
    'Study': 2/24,
    'Other': 5/24
}

data = pd.Series(x).reset_index(name='value').rename(columns={'index':'country'})
data['angle'] = data['value']/data['value'].sum() * 2*pi
data['color'] = Category20[len(x)]

p = figure(plot_height=350, title="Pie Chart", toolbar_location=None,
           tools="hover", tooltips="@country: @value%", x_range=(-0.5, 1.0))

p.wedge(x=0, y=1, radius=0.4,
        start_angle=cumsum('angle', include_zero=True), end_angle=cumsum('angle'),
        line_color="white", fill_color='color', legend='country', source=data)

p.axis.axis_label=None
p.axis.visible=False
p.grid.grid_line_color = None

show(p)

```



    <div class="bk-root">
        <a href="https://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
        <span id="2090">Loading BokehJS ...</span>
    </div>











  <div class="bk-root" id="20b2e138-7099-4e07-8004-293183f4b477"></div>




