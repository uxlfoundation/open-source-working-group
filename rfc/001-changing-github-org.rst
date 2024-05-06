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
   * - onednn
     - Vadim Pirogov
     - 
     - onednn-project
     - oneDNN
   * - onedal
     - Nikolay Petrov
     - 
     - onedal-project
     - oneDAL
   * - oneccl
     - Joel Rosenzweig
     - 
     - oneccl-project
     - oneCCL
   * - onemkl
     - Irina Topinskaia
     - 
     - onemkl-project
     - oneMKL-sycl-interfaces
   * - onedpl
     - Timmie Smith
     - Q4 2024
     - onedpl-project
     - oneDPL
   * - onetbb
     - Ekaterina Semenova
     - Q4 2024
     - onetbb-project
     - oneTBB
   * - oneapi-spec
     - Robert Cohn
     - 5/2/2024
     - uxlfoundation
     - oneapi-spec

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
