Ansible Geant
=============

[![Build Status](https://travis-ci.org/jbzdak/ansible-geant.svg?branch=master)](https://travis-ci.org/jbzdak/ansible-geant)

A role that installs (compiles) Geant 4 simulation framework.
 
By default it installs Geant 4.9.6.4. 

This role is idempotent --- if you run it again, it won't re-compile geant. 

Role Variables
--------------

There are a lot of variables to set:
 
User for geant and install folder 

    GEANT_USER: geant
    GEANT_ROOT_DIR: /home/{{ GEANT_USER }}/4.9.6.4

System dependencies for geant (these are probably right, no need to change. 

For Debian: 

    GEANT_DEPENDENCIES_DEBIAN:
      - build-essential
      - git
      - cmake
      - libexpat1-dev

For CentOs    
    
    GEANT_DEPENDENCIES_CENTOS:
      - "@Development Tools"
      - "@Development Libraries"
      - expat
      - expat-devel

Geant package sources, these are hosted on my cloud infrastructure, so I can 
have repeatable builds ;) (plus download speeds are way faster than from CERN). 
Feel free to change it if you need it. 

    GEANT_SOURCE:
      # Must be a tar.gz file
      url: https://storage.googleapis.com/kaskady/resources/geant4.9.6.p04.tar.gz
      sig: sha256:997220a5386a43ac8f533fc7d5a8360aa1fd6338244d17deeaa583fb3a0f39fd
    
    GEANT_DATA_FILES:
        # Must be a tar.gz file
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4NDL.4.2.tar.gz
         sig: sha256:173f60a506b9176d7ff531d6a5f6195dcec74df30ffafc09644f47f979bd641b
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4EMLOW.6.32_permissions.tar.gz
         sig: sha256:738361fe9f1ce164aa22e460c1b68941457e4160b8da86dcba576e873c5cc293
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4PhotonEvaporation.2.3.tar.gz
         sig: sha256:60449df933794aa0ad3938886c8c023e3093ff59ad6c752923390d5c550f34cb
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4RadioactiveDecay.3.6.tar.gz
         sig: sha256:3502ed4be04d694115a3acf59d7a3593725a2d79f3adad0ffa135ff653f89d1d
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4NEUTRONXS.1.2.tar.gz
         sig: sha256:9ce488505b4c3623e2d98209f708a30e3f213a1371a9110d289257a02b2d7d5c
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4PII.1.3.tar.gz
         sig: sha256:6225ad902675f4381c98c6ba25fc5a06ce87549aa979634d3d03491d6616e926
      -  url: https://storage.googleapis.com/kaskady/resources/data/RealSurface.1.0.tar.gz
         sig: sha256:3e2d2506600d2780ed903f1f2681962e208039329347c58ba1916740679020b1
      -  url: https://storage.googleapis.com/kaskady/resources/data/G4SAIDDATA.1.1.tar.gz
         sig: sha256:a38cd9a83db62311922850fe609ecd250d36adf264a88e88c82ba82b7da0ed7f

HOWTO
-----

How to install another geant version: 

1. Change ``GEANT_ROOT_DIR`` to point to better version
2. Download geant sources and all required data files to you computer, and 
   calculate sha256 sums for all the files. 
3. Either upload these files somewhere or not. 
4. Update ``GEANT_SOURCE`` and  ``GEANT_DATA_FILES`` with new files and new 
   checksums. 
5. Now it should work.    
   
TODO
----

1. It would be good to test Geant installation, maybe compile some examples? 
2. It would be good to have version specified in a single place. 


Dependencies
------------

None

License
-------

BSD

Author Information
------------------

Jacek Bzdak
