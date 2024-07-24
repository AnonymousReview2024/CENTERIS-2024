**#CENTERIS 2024**
Application described in the article submitted to CENTERIS 2024.

This repository contains the docker compose file required for local execution of the application and the presentation of the Process Element Tagger tool.

**Process Element Tagger**

To revitalize Rosa’s solution, we started by analyzing the code available on GitHub, a laborious task given the low documentation. A few modifications were necessary to make the program operable again, such as updating discontinued methods and libraries. The Stanford NLP initialization was also changed to be performed as a separate command instead of part of the main script.
In pursuing a flexible and scalable architecture, we implemented a system employing two containers: one dedicated to processing the natural language text descriptions identifying BPMN elements (back-end) and the other to web functionalities. This design allows the application to be initiated easily using a docker compose file. It also ensures independence between the two containers, allowing the use of the developed interface with other identification algorithms. The requisites for doing so are listening for requests at the appropriate port and producing responses following the adequate object format shown in Fig. 5.
The interaction between these containers is limited to a single communication instance when a new description needs to be marked. The website makes an asynchronous call to the back end, sending the process description to the body of the HTTP request and receiving the processed object as a response.
The original proposed interface, delivered in the prototype stage, comprised three main components: The Participants List; The Elements Menu; And the Text Box. Although completely refactored, this structure was kept in our version, and our focus was on adding new functionalities to these components instead of engaging in their design.
The application is built in a single page format using React. We used CSS to define a 3x3 grid where components are displayed according to the state of a variable called "InputPage". When set as true, it exhibits the title "Process Element Tagger" centralized in the first row of the grid, the center space is occupied by the Input Box component, and the bottom row contains a button named "Mark" that, when pressed send the process description to be analyzed by the back-end and change the InputPage variable state if a valid response is obtained. This page can be seen on the left side of Figure.

![Prints from the tool waiting for input (left), and after receiving a response and select some of the tag options (right).](https://github.com/AnonymousReview2024/CENTERIS-2024/blob/main/prints%20tool.png)
 
After processing the description, an object is returned as metadata, and once the variable is false, the page passes through several changes: The title is substituted by the Elements Menu component, responsible for concatenating all the BPMN elements types available and if it should or should not be highlighted. The input box gives space to the text box, where the description text is displayed in an environment that enables users to interact with each word individually and supports the native taggings of the tool. The left side of the middle row is occupied by the Process Participants List, which presents all the automatically detected process participants in the given description and allows the highlight of all its related elements. The "Mark" button became a return button, responsible for resetting the InputPage variable and reverting the changes.
Some functionalities of the tool remain unchanged from the previous version. These include the automatic identification of elements, which receives an object containing the descriptive text and the elements identified by the algorithm; the "Mouse Hover" functionality, which opens a popup with information about the participant and the type relative to the element when the mouse cursor is over the element text; the ability to highlight elements by type, allowing selected element types to be highlighted in desired colors; and the show/hide icons functionality, which controls the display of the element type icon before the elements in the text.
Other functionalities have been modified. The "Participants List" now allows the insertion of new participants and the option to highlight elements by participant. The "Elements Type Menu" has been enhanced to group elements of the same category in dropboxes, making navigation easier. Additionally, new functionalities have been added, including the option to "Highlight Elements by Participant," which highlights all elements associated with a specific participant, the "Click to Edit Element" functionality, allowing users to change attributes of elements, and the "Select to Add New Element" functionality, which enables the creation of new elements by selecting texts with the mouse.
Free hosting services don’t deliver enough computer power necessary for the correct operation of the back-end part of the application. During the evaluation period, we kept the Tagger running in a cloud computing service, using free credits provided by them for students. Once the credits were over, the online distribution was no longer available, but it is still possible to run it locally following the steps presented on this GitHub.


**Instructions for installing Process Element Tagger**

You only need to clone the .compose file to a folder on a computer with docker installed and run the "docker-compose up" command in the folder.

**References**

L. Silva Rosa, T. Soares Silva, M. Fantinato, e L. Thom, “A visual approach for identification and annotation of business process elements in process descriptions”, Comput. Stand. Interfaces, vol. 81, p. 103601, nov. 2021, doi: 10.1016/j.csi.2021.103601.
