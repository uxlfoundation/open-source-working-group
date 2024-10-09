==========================================
Moving Projects to UXL GitHub Organization
==========================================

Moving UXL projects from `oneapi-src`_ to an organization owned
by UXL.

Background
==========

All 6 of the original UXL projects are in the `oneapi-src`_ GitHub
organization. The org is owned by Intel and also contains projects that are not
part of UXL. We need to transfer ownership of the repos to UXL by moving them
to a new org.

We considered various options:

1. Move all the repos to the `uxlfoundation`_ org.
2. Move the oneapi-src org to UXL.
3. Move the repos to a project-specific org.

We do not recommend (1) and (2) because they are a shared org. A shared org has
the following drawbacks:

* Must share GitHub runners, permissions, and integrations
* Repo and team naming conflicts
* Community confusion. DPL and DNN have different communities and goals.
* Requires central management, and UXL does not have the resources to manage
  the org

Furthermore, (2) requires redefining the purpose of oneapi-src, which will lead
to confusion about the projects that go and stay.

A shared org does have some advantages:

* Central management can be more efficient and secure
* Sharing team definitions across projects when there are shared teams
* Provides more visibility for UXL as the host of the projects

We recommend (3) because it is the common practice for large complex open
source projects. Projects will have the freedom to manage their org as they see
fit and not be affected by requirements or preferences of other projects.

Repo Information
================

.. list-table::
   :header-rows: 1

   * - Current Repo
     - Primary Contact
     - Migration Date
     - New Org
     - New Repo
   * - onednn_
     - Vadim Pirogov
     - Q4 2024
     - onednn-project_
     - oneDNN
   * - onedal_
     - Nikolay Petrov
     - Q4 2024
     - onedal-project_
     - oneDAL
   * - oneccl_
     - Joel Rosenzweig
     - Q4 2024
     - oneccl-project_
     - oneCCL
   * - onemkl_
     - Irina Topinskaia
     - Q4 2024
     - onemkl-project_
     - oneMKL-sycl-interfaces
   * - onedpl_
     - Timmie Smith
     - Q4 2024
     - onedpl-project_
     - oneDPL
   * - onetbb_
     - Ekaterina Semenova
     - Q4 2024
     - onetbb-project_
     - oneTBB
   * - oneapi-spec
     - Robert Cohn
     - 5/2/2024
     - uxlfoundation_
     - oneapi-spec_

.. _onednn-project: https://github.com/onednn-project
.. _onedal-project: https://github.com/onedal-project
.. _oneccl-project: https://github.com/oneccl-project
.. _onetbb-project: https://github.com/onetbb-project
.. _onedpl-project: https://github.com/onedpl-project
.. _onemkl-project: https://github.com/onemkl-project
.. _uxlfoundation: https://github.com/uxlfoundation

.. _onednn: https://github.com/oneapi-src/onednn
.. _onedal: https://github.com/oneapi-src/onedal
.. _oneccl: https://github.com/oneapi-src/oneccl
.. _onetbb: https://github.com/oneapi-src/onetbb
.. _onedpl: https://github.com/oneapi-src/onedpl
.. _onemkl: https://github.com/oneapi-src/onemkl
.. _oneapi-spec: https://github.com/uxlfoundation/oneapi-spec


Org Administration
==================

The projects will have ownership of their org. To ensure continuity, select at
least 2 people to have the org ``owner`` role. It is not recommended to broadly
share ownership permissions. Prepare a basic set of recommended configurations
(e.g. 2fa) for the org or perhaps the org can be configured before handover of
the project. Each org will have Linux Foundation and UXL admins who are there
for emergency maintenance only. Need to share some guides on how to manage an
org.

Process
=======

This is a sketch of the activity. Each project should prepare its own schedule
and plan. Robert Dower, the maintainer of oneapi-src org will help with the
move by preparing the new org, transferring the teams, and moving the repos.

Preparation:

1. Create the new org and teams
2. Prepare a project specific test plan
3. Prepare a project specific communication plan
4. Identify URLs that are not redirected and prepare PR's to update them.

Execution:

1. Communicate the change to the community.
2. Move the repos to the new org.
3. Merge the PR's to update the URLs
4. Testing

Cleanup:

1. Update URLs that are redirected

Moving the Repo
---------------

The recommended way to move the repo is to use the GitHub web interface to move
it to the new org. This will preserve the issues, PR's, and stars. The repo URL
will change, but GitHub will redirect the old URL to the new URL. Another
option is to fork the repo into the new org, but it will not do forwarding and
will not preserve the issues, PR's, and stars.

It may be convenient to initially fork the repo to the new org for the purpose
of testing. I believe you can rename the repo in the new org to avoid confusion
about the active repo. Another possibility it to make the new repo private. In
either case, the fork would be deleted and the original repo moved.

Robert Cohn has experience writing python scripts that use the GitHub APIs so
if there is some aspect of the move that you would like to automate, please let
him know.

Project Web Sites
-----------------

Most project web sites are hosted on GitHub pages. The URL is based on the org
and repo name. The URL will change when the repo is move. GitHub pages URLs are
not automatically forwarded, but we can manually forward individual URLs.

Projects may want to consider moving their web site to a new URL that is not
based on the org and repo name. This will avoid the need to manually forward
URLs if the repo or org changes in the future. It also makes it possible to
change the web hosting provider without changing URLs. GitHub Pages is
preferred, but other providers allow dynamic content and bigger web sites.
Contact Robert Cohn to discuss web hosting if you want alternate hosting.


Risks and Mitigations
=====================

This section includes some generic risks. Each project should identify its own
risks.

Community confusion
  Communicate the change to the community and ensure that they understand the
  new org structure and schedules.
Community disruption
  Ensure that the new org has the same teams, permissions, and integrations as
  the current org. Leverage GitHub repo URL redirect and provide website
  redirects.
Maintainer disruption
  Ensure that maintainers are aware of the change and have the necessary
  permissions to continue their work.
CI/CD disruption
  Test plan. Ensure the CI/CD maintainers are available to address problems.
Unexpected breakage
  Test the new org before the move. Have a rollback plan in case of unexpected
  breakage. Search the repos for references to the old org.
Release disruption
  Schedule moves during a time when releases are not planned.

.. _`uxlfoundation`: https://github.com/uxlfoundation
.. _`oneapi-src`: https://github.com/oneapi-src
