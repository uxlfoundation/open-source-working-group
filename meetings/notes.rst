===============
 Meeting Notes
===============

This file contains all the meeting notes from the Open Source Working Group Meetings. 

1/24/2024
=========

Attendees:
----------

* Andrew Wafaa, Arm (Open Source Working Group chair)
* Abhishek Jain, Fujitsu
* Alex Pim, Imagination Technologies
* Alexey Kukanov, Intel
* Ankit Manerikar, Intel
* Denis Samoilov, Intel
* Igor Safanov, Intel
* Steve Capper, Arm
* Maria Kraynyuk, Intel
* Masahiro Doteguchi, Fujitsu
* Nikolay Petrov, Intel
* Pavel Kumbrasev, Intel
* Penporn Koanakatool, Google
* Ragesh Hajela, Fujitsu
* Robert Cohn, Intel
* Sarah Knepper, Intel
* Timmie Smith, Intel
* Vadim Pirogov, Intel

Agenda:
-------

* Present priorities for the Open Source Working Group
* Discuss issues and areas for work

Notes
-----

The first meeting of the UXL Foundation Open Source Working Group was led by Andrew Wafaa from Arm.

The group went through a set of priorities that have been provided by the UXL Steering Committee.

* Build Infrastructure
  * The intention of this is to bring independent builds of the projects and infrastructure in place that facilitates community contributions to the projects.

* Open Source Best Practice
  * The intention of this is to ensure that the projects follow the best practices of open source development so that there is a clear and frictionless way for the community to contribute to the projects.

* Open Source Kernels
  * The intention of this is to bring more open source code to the projects where there are opportunities to add new kernel code particularly to help target more vendors and architectures.

* Architecture
  * Identify opportunities to simplify projects or make it easier to support more vendor and architecture targets and also to simplify the integration of the projects with other frameworks and software, for example TensorFlow or PyTorch.

* Compatibility Testing
  * In order to ensure that a developer using the projects has a consistent and good experience, compatibility tests could be made available so that they can be run on different vendors and architectures.


* Build Infrastructure Discussion
Due to the history of the projects the infrastructure is mostly hosted by Intel but we would like to integrate CI, build and testing for different vendor and architecture targets.
Penporn from Google shared information about how this is done with the TensorFlow project:
  * `Official Builds (maintained by Google)`_
  * `Community Builds (maintained by 3rd parties)`_

A similar model could be adopted for UXL Foundation projects.
Options for using public cloud infrastructure for the projects include:
 
* The foundation funding infrastructure (this is unlikely due to the 
  costs involved)
* Obtaining donations of credits from public cloud infrastructure 
  providers (note that donations cannot be used in lieu of membership cost)
* Organisations providing infrastructure in a similar way to how Intel
  currently does this

Some points to note from the discussions:
* TensorFlow has a dedicated team looking after build and CI
* The build machines needed is dictated by the volume of Pull Requests 
  made so can increase as contributions increase otherwise the process 
  can get backed up
* Some organisations require security scanning when builds are done, 
  some of these would be difficult to do in public
* A big improvement for projects would be to move infrastructure or 
  build logs in public so that the community can see this, but some 
  infrastructure can still live inside the corporate network
* Here is a link to an example of the infrastructure TensorFlow uses 
  `with Arm`_
* The best solution is to find maintainers for specific target devices 
  and enable them to do this through the GitHub projects

Penporn passed on the details of some Intel people working on CI for 
TensorFlow who may have some advice or help.

Ragesh from Fujitsu is engaging with the oneDAL team to add an Arm 
target. They have discussed modifications and changes needed to make 
the external contributions work and it will be good to share this 
with other projects.

Discussions will continue on the Slack channel and at the next 
Working Group meeting.

The group agreed that the Working Group will initially focus on 
specific projects, with oneDAL and oneDNN the focus for the next 
meeting.

.. _`Official Builds (maintained by Google)`: https://github.com/tensorflow/tensorflow?tab=readme-ov-file#official-builds
.. _`Community Builds (maintained by 3rd parties)`: https://github.com/tensorflow/build#community-supported-tensorflow-builds
.. _ `with Arm`: https://github.com/tensorflow/tensorflow/actions/workflows/arm-ci.yml

