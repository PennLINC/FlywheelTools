# Methods

Flywheel tools is a multiple purpose toolkit for interacting with the Flywheel platform. The toolkit allows users to follow a reproducible workflow for BIDS curation and audit of their data, that includes 1) inspection of sequences; 2) design of a curation heuristic; 3) heuristic testing and implementation; 3) curated data inspection and export; and finally 4) audit of data and analyses.

## Programming Languages & Technologies

Flywheel Tools is built primarily in Python 3.6 **[CITE]()** due to its ease of use in interfacing with the Flywheel SDK. Additionally, R 3.4.1, with its extensive variety of libraries for creating high-quality data analysis reports, is used for HTML report generation **[CITE]()**. The majority of SDK users on the Flywheel platform utilise Python as their programming language of choice, allowing members of the community to view and contribute to the open-source codebase. For reprodicibility and workflow management, Flywheel Tools' modules are packaged in version controlled software containers built and managed in Docker **[CITE]()**. Lastly, the Flywheel Tools package assumes its users adhere to the Brain Imaging Data Structure (BIDS) paradigm to store and process their data. BIDS is a paradigm for reproducible and collaborative data storage and is growing rapidly in the neuroimaging community **[CITE]()**, and hence BIDS compatibility is included on the Flywheel platform.

## Flywheel

Flywheel is a big data management and analysis platform for research, which lends itself well to neuroimaging. The platform focuses heavily on collaborative and reproducible science. User-facing components of the platform itself are the Web User Interface (UI), the Software Development Kit (SDK), and the Application Programming Interface (API) ([IMAGE HERE]()).

### Flywheel Web UI

The web UI is accessible through any web browser and is the primary method of interacting with Flywheel data. Through this point-and-click interface, users are able to upload, view, download, and analyse data with ease and simplicity. However, accomplishing tasks with many repetitive steps or a large number of subjects/sessions to iterate over can be tiresome and error-prone. Alongside knowledge of navigating the web UI, many users also make use of the SDK to munge and analyse data programmatically.

### Flywheel API & SDK

Flywheel's database utilises MongoDB for data storage and access, meaning that all Flywheel data is represented by hierarchical relationships between document objects. This has allowed developers to create and store complex structures with ease, and query data rapidly **[CITE]()**. In order to access this data, Flywheel uses a RESTful Application Programming Interface (REpresentational State Transfer) **[CITE]()**, and hence each document or data object is accessible through a a specific URL that a web browser or SDK can access by requesting the data and waiting for a response from the server. The Flywheel Python SDK provides a powerful interface for inspecting, munging, and manipulating data through this API, by standardising this underlying data model into Pythonic Object Oriented Programming (OOP). Programming with the Python SDK involves objects and methods that any user with Python programming experience can quickly pick up.

### Flywheel Data Model

Once abstracted in Python, Flywheel's data model is relatively simple and may be familiar to neuroimaging researchers. Objects follow a specific hierarchical structure **([IMAGE]())** — at the top level is a group (for example, a University), under which there are projects. Each project object can have one or many subjects (i.e. participants), and each subject can have one or many sessions (i.e. scanning visits). Within a session, there may be one or many acquisition objects which describe the scanning sequence collected during a particular or examination (e.g. rs-fMRI, DWI, PET), and under each acquisition is *attached* the data file associated with the sequence (e.g. a NIfTI file). Note that a file can be attached to any object type, and each object can have metadata associated with it. Hence, a subject object may have de-identified demographic metadata associated to that participant, and the object may also have a self-report scale attached to it as a text file. A notable exception to the hierarchical structure rule is the analysis object, which behaves in much the same way as others but can be a child object of any other object, allowing researchers to create analyses of entire projects, for example, each with their own associated metadata and files (such as inputs and outputs).

Abstracting this data model in Python results in simple hierarchical objects, each with setter's and getter's for handling metadata and files, and methods for accomplishing object-specific tasks like traversing the hierarchical structure or running analyses. Flywheel Tools' modules make use of this data model to accomplish a wide range of tasks.

### Flywheel Gears

Flywheel encourages the use of pre-packaged analysis workflows called *gears*. These gears are run by virtual machines using Docker and hence are version-controlled and software/platform agnostic **[CITE]()**. In addition to the multitude of gears available on the platform, users are able to package their own software in a gear and use it for running analysis workflows on their Flywheel data, via the web UI or SDK. Deciding on whether to accomplish a task using the web UI, programmatically using the SDK, or by wrapping it as a workflow into a gear, depends on the complexity and frequency of the task **[IMAGE]()**.

# Results

We implemented the Flywheel Tools package using the Flywheel SDK to enable easy inspection, curation, validation, and audit of Flywheel data through a handful of user-friendly gears and command-line tools.

The first module of the package is called `fw-heudiconv`, and is largely inspired by the popular HeuDiConv Python package **[CITE]()**. `fw-heudiconv` is a multi-part toolbox for reprodicible curation of neuroimaging data into BIDS on Flywheel. The second module, `flaudit`, is a tool for accomplishing a complete audit of a Flywheel project, giving users a view of their dataset from 10,000 feet.

## `fw-heudiconv`

### Architecture & Design

### Curation Workflow

## `flaudit`

### Architecture & Design
