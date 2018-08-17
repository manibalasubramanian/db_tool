Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\balasman> minishift start
-- Starting profile 'minishift'
-- Check if deprecated options are used ... OK
-- Checking if https://github.com is reachable ... OK
-- Checking if requested OpenShift version 'v3.9.0' is valid ... OK
-- Checking if requested OpenShift version 'v3.9.0' is supported ... OK
-- Checking if requested hypervisor 'virtualbox' is supported on this platform ... OK
-- Checking if VirtualBox is installed ... OK
-- Checking the ISO URL ... OK
-- Checking if provided oc flags are supported ... OK
-- Starting the OpenShift cluster using 'virtualbox' hypervisor ...
-- Starting Minishift VM ...................................... OK
-- Checking for IP address ... OK
-- Checking for nameservers ... OK
-- Checking if external host is reachable from the Minishift VM ...
   Pinging 8.8.8.8 ... OK
-- Checking HTTP connectivity from the VM ...
   Retrieving http://minishift.io/index.html ... OK
-- Checking if persistent storage volume is mounted ... OK
-- Checking available disk space ... 1% used OK
-- OpenShift cluster will be configured with ...
   Version: v3.9.0
-- Pulling the Openshift Container Image ............................................................... OK
-- Copying oc binary from the OpenShift container image to VM ... OK
-- Starting OpenShift cluster ........................................
Using nsenter mounter for OpenShift volumes
Using public hostname IP 192.168.99.100 as the host IP
Using 192.168.99.100 as the server IP
Starting OpenShift using openshift/origin:v3.9.0 ...
OpenShift server started.

The server is accessible via web console at:
    https://192.168.99.100:8443

You are logged in as:
    User:     developer
    Password: <any value>

To login as administrator:
    oc login -u system:admin


Could not set oc CLI context for 'minishift' profile: Error during setting 'minishift' as active profile: The specified path to oc '' does not exist
PS C:\Users\balasman> oc
OpenShift Client

This client helps you develop, build, deploy, and run your applications on any OpenShift or Kubernetes compatible
platform. It also includes the administrative commands for managing a cluster under the 'adm' subcommand.

To create a new application, login to your server and then run new-app:

  oc login https://mycluster.mycompany.com
  oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git
  oc logs -f bc/ruby-ex

This will create an application based on the Docker image 'centos/ruby-22-centos7' that builds the source code from
GitHub. A build will start automatically, push the resulting image to the registry, and a deployment will roll that
change out in your project.

Once your application is deployed, use the status, describe, and get commands to see more about the created components: 

  oc status
  oc describe deploymentconfig ruby-ex
  oc get pods

To make this application visible outside of the cluster, use the expose command on the service we just created to create
a 'route' (which will connect your application over the HTTP port to a public domain name).

  oc expose svc/ruby-ex
  oc status

You should now see the URL the application can be reached at.

To see the full list of commands supported, run 'oc --help'.
PS C:\Users\balasman> oc login
Server [https://localhost:8443]: developer
error: dial tcp: lookup developer: getaddrinfow: This is usually a temporary error during hostname resolution and means that the local server did not receive a response from an authoritative server. - verify you have provided the correct host and port and that the server is currently running.
PS C:\Users\balasman> oc login https://localhost:8443
error: dial tcp [::1]:8443: connectex: No connection could be made because the target machine actively refused it. - verify you have provided the correct host and port and that the server is currently running.
PS C:\Users\balasman> oc login https://192.168.99.100:8443
The server uses a certificate signed by an unknown authority.
You can bypass the certificate check, but any data you send to the server could be intercepted by others.
Use insecure connections? (y/n): y

Authentication required for https://192.168.99.100:8443 (openshift)
Username: developer
Password:
Login successful.

You have one project on this server: "myproject"

Using project "myproject".
Welcome! See 'oc help' to get started.
PS C:\Users\balasman>
PS C:\Users\balasman>
PS C:\Users\balasman> minishift oc-env
$Env:PATH = "C:\Users\balasman\.minishift\cache\oc\v3.9.0\windows;$Env:PATH"
# Run this command to configure your shell:
# & minishift oc-env | Invoke-Expression
PS C:\Users\balasman> & minishift oc-env | Invoke-Expression
PS C:\Users\balasman> docker images
error during connect: Get http://%2F%2F.%2Fpipe%2Fdocker_engine/v1.38/images/json: open //./pipe/docker_engine: The system cannot find the file specified. In the default daemon configuration on Windows, the docker client must be run elevated to connect. This error may also indicate that the docker daemon is not running.
PS C:\Users\balasman> minishift docker-env
$Env:DOCKER_TLS_VERIFY = "1"
$Env:DOCKER_HOST = "tcp://192.168.99.100:2376"
$Env:DOCKER_CERT_PATH = "C:\Users\balasman\.minishift\certs"
# Run this command to configure your shell:
# & minishift docker-env | Invoke-Expression
PS C:\Users\balasman> & minishift docker-env | Invoke-Expression
PS C:\Users\balasman> docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
openshift/origin-web-console       v3.9.0              aa12a2fc57f7        7 weeks ago         495MB
openshift/origin-docker-registry   v3.9.0              8e6f7a854d66        7 weeks ago         465MB
openshift/origin-haproxy-router    v3.9.0              448cc9658480        7 weeks ago         1.28GB
openshift/origin-deployer          v3.9.0              39ee47797d2e        7 weeks ago         1.26GB
openshift/origin                   v3.9.0              4ba9c8c8f42a        7 weeks ago         1.26GB
openshift/origin-pod               v3.9.0              6e08365fbba9        7 weeks ago         223MB
PS C:\Users\balasman>
PS C:\Users\balasman>
PS C:\Users\balasman>
PS C:\Users\balasman> cd C:\mani\minishift\
PS C:\mani\minishift> dir


    Directory: C:\mani\minishift


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/15/2018   2:43 PM                db-tool
d-----        8/15/2018   2:39 PM                projects
d-----        8/15/2018   8:57 AM                s2itest
-a----        7/31/2018   5:33 PM          11374 LICENSE
-a----        8/15/2018   9:34 AM        5820976 minishift-1.22.0-windows-amd64.zip
-a----        8/15/2018  10:25 AM      349175808 minishift-centos7.iso
------        7/31/2018   5:33 PM       16433664 minishift.exe
-a----        8/15/2018   8:55 AM           7566 minishift_rhel.txt
-a----        8/15/2018   8:55 AM           7031 minishift_s2i_python.txt
-a----        8/15/2018   1:13 PM      213228544 oc.exe
-a----        7/31/2018   5:33 PM           3328 README.adoc
-a----        8/15/2018   2:34 PM         167414 s2i-python-container-master.zip
------        5/25/2018   5:59 PM        7477760 s2i.exe
-a----        8/15/2018   2:35 PM        5207866 source-to-image-v1.1.11-78a76d97-windows-amd64.zip


PS C:\mani\minishift> cd db-tool
PS C:\mani\minishift\db-tool> dir


    Directory: C:\mani\minishift\db-tool


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/15/2018   2:54 PM             42 app.py
-a----        8/15/2018   2:43 PM             23 requirements.txt

PS C:\mani\minishift\db-tool>
PS C:\mani\minishift\db-tool>
PS C:\mani\minishift\db-tool> s2i build . centos/python-27-centos7 myapp
---> Installing application source ...
---> Installing dependencies ...
You are using pip version 7.1.0, however version 18.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Collecting numpy (from -r requirements.txt (line 1))
Downloading https://files.pythonhosted.org/packages/3a/20/c81632328b1a4e1db65f45c0a1350a9c5341fd4bbb8ea66cdd98da56fe2e/numpy-1.15.0.zip (4.5MB)
Collecting pandas (from -r requirements.txt (line 2))
Downloading https://files.pythonhosted.org/packages/e9/ad/5e92ba493eff96055a23b0a1323a9a803af71ec859ae3243ced86fcbd0a4/pandas-0.23.4.tar.gz (10.5MB)
Collecting cx-Oracle (from -r requirements.txt (line 3))
Downloading https://files.pythonhosted.org/packages/0a/7a/a679d1c3e711b083ce8d40aa38e3010e0f27084ccee7ac9cd4147fa3da9a/cx_Oracle-6.4.1.tar.gz (253kB)
Collecting python-dateutil>=2.5.0 (from pandas->-r requirements.txt (line 2))
Downloading https://files.pythonhosted.org/packages/cf/f5/af2b09c957ace60dcfac112b669c45c8c97e32f94aa8b56da4c6d1682825/python_dateutil-2.7.3-py2.py3-none-any.whl (211kB)
Collecting pytz>=2011k (from pandas->-r requirements.txt (line 2))
Downloading https://files.pythonhosted.org/packages/30/4e/27c34b62430286c6d59177a0842ed90dc789ce5d1ed740887653b898779a/pytz-2018.5-py2.py3-none-any.whl (510kB)
Collecting six>=1.5 (from python-dateutil>=2.5.0->pandas->-r requirements.txt (line 2))
Downloading https://files.pythonhosted.org/packages/67/4b/141a581104b1f6397bfa78ac9d43d8ad29a7ca43ea90a2d863fe3056e86a/six-1.11.0-py2.py3-none-any.whl
Installing collected packages: numpy, six, python-dateutil, pytz, pandas, cx-Oracle
Running setup.py install for numpy
Running setup.py install for pandas
Running setup.py install for cx-Oracle
Successfully installed cx-Oracle-6.4.1 numpy-1.15.0 pandas-0.23.4 python-dateutil-2.7.3 pytz-2018.5 six-1.11.0
Build completed successfully
PS C:\mani\minishift\db-tool> docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
myapp                              latest              ae4cd3f8e1b1        55 seconds ago      778MB
centos/python-36-centos7           latest              d67307610df0        4 weeks ago         635MB
centos/python-27-centos7           latest              b8c6eff7df1e        4 weeks ago         643MB
openshift/origin-web-console       v3.9.0              aa12a2fc57f7        7 weeks ago         495MB
openshift/origin-docker-registry   v3.9.0              8e6f7a854d66        7 weeks ago         465MB
openshift/origin-haproxy-router    v3.9.0              448cc9658480        7 weeks ago         1.28GB
openshift/origin-deployer          v3.9.0              39ee47797d2e        7 weeks ago         1.26GB
openshift/origin                   v3.9.0              4ba9c8c8f42a        7 weeks ago         1.26GB
openshift/origin-pod               v3.9.0              6e08365fbba9        7 weeks ago         223MB
PS C:\mani\minishift\db-tool> docker run -e APP_FILE=app.py
"docker run" requires at least 1 argument.
See 'docker run --help'.

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Run a command in a new container
PS C:\mani\minishift\db-tool> docker run -e APP_FILE=app.py myapp
---> Running application from Python script (app.py) ...
Hello World
PS C:\mani\minishift\db-tool>


PS C:\mani\minishift\db-tool>
PS C:\mani\minishift\db-tool> s2i build . centos-rptdba-python-27 myapp
---> Installing application source ...
Build completed successfully
PS C:\mani\minishift\db-tool> docker run -e APP_FILE=app.py myapp
---> Running application from Python script (app.py) ...
Hello World