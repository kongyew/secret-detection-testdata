===========
secret-detection-testdata
===========

-------------------------------------------------------------------------------------------
This repository provides test data for secret detection while using different tools.
-------------------------------------------------------------------------------------------

.. contents:: :depth: 2

Synopsis
--------

::

 ./build-docker-images.sh 


Description
-----------

``build-docker-images.sh`` build those docker images with pre-created secrets


Test secret detection with GitGuardian (ggshield)
----------------------

``./scan-with-ggshield.sh`` is executed.



::

     % ./scan-with-ggshield.sh
    Warning: Using `ggshield scan (...)` is deprecated. Use `ggshield secret scan (...)` instead.
    Saving docker image... OK
    Scanning  [####################################]  100%
    Error scanning. Results may be incomplete.
    The following chunk is affected:
    Dockerfile or build-args
    403:Quota limit reached.


    No secrets have been found

    Warning: Using `ggshield scan (...)` is deprecated. Use `ggshield secret scan (...)` instead.
    Saving docker image... OK
    Scanning  [####################################]  100%
    Error scanning. Results may be incomplete.
    The following chunk is affected:
    Dockerfile or build-args, b549e1edf56bc36573d990b89970af0334df94c9e70b33bad81f0be069cd4673:/aws-keys.txt
    403:Quota limit reached.


Test secret detection with GitGuardian (ggshield)
----------------------

::

    % ./scan-with-trivy_files.sh
    2022-06-21T20:24:53.236-0700	INFO	Vulnerability scanning is enabled
    2022-06-21T20:24:53.237-0700	INFO	Secret scanning is enabled
    2022-06-21T20:24:53.238-0700	INFO	If your scanning is slow, please try '--security-checks vuln' to disable secret scanning
    2022-06-21T20:24:53.238-0700	INFO	Please see also https://aquasecurity.github.io/trivy/v0.29.1/docs/secret/scanning/#recommendation for faster secret detection
    2022-06-21T20:24:53.293-0700	INFO	Number of language-specific files: 0

    data/accesskey.txt (secrets)

    Total: 2 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 2)

    ┌──────────┬───────────────────┬──────────┬─────────┬──────────────────────┐
    │ Category │    Description    │ Severity │ Line No │        Match         │
    ├──────────┼───────────────────┼──────────┼─────────┼──────────────────────┤
    │   AWS    │ AWS Access Key ID │ CRITICAL │    3    │ AccesskeyID=>*****   │
    │          │                   │          ├─────────┼──────────────────────┤
    │          │                   │          │    5    │ AccesskeyID\=>\***** │
    └──────────┴───────────────────┴──────────┴─────────┴──────────────────────┘

    data/aws-keys.txt (secrets)

    Total: 1 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 1)

    ┌──────────┬───────────────────┬──────────┬─────────┬───────┐
    │ Category │    Description    │ Severity │ Line No │ Match │
    ├──────────┼───────────────────┼──────────┼─────────┼───────┤
    │   AWS    │ AWS Access Key ID │ CRITICAL │    1    │ ***** │
    └──────────┴───────────────────┴──────────┴─────────┴───────┘
    2022-06-21T20:24:53.635-0700	INFO	Vulnerability scanning is enabled
    2022-06-21T20:24:53.635-0700	INFO	Secret scanning is enabled
    2022-06-21T20:24:53.635-0700	INFO	If your scanning is slow, please try '--security-checks vuln' to disable secret scanning
    2022-06-21T20:24:53.635-0700	INFO	Please see also https://aquasecurity.github.io/trivy/v0.29.1/docs/secret/scanning/#recommendation for faster secret detection
    2022-06-21T20:24:53.698-0700	INFO	Number of language-specific files: 0
    2022-06-21T20:24:54.023-0700	INFO	Vulnerability scanning is enabled
    2022-06-21T20:24:54.023-0700	INFO	Secret scanning is enabled
    2022-06-21T20:24:54.023-0700	INFO	If your scanning is slow, please try '--security-checks vuln' to disable secret scanning
    2022-06-21T20:24:54.023-0700	INFO	Please see also https://aquasecurity.github.io/trivy/v0.29.1/docs/secret/scanning/#recommendation for faster secret detection
    2022-06-21T20:24:54.106-0700	INFO	Number of language-specific files: 0

    data/cloud-key (secrets)

    Total: 1 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 1, CRITICAL: 0)
