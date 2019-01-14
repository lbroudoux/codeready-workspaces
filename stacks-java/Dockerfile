FROM registry.access.redhat.com/codeready-workspaces-beta/stacks-java:1.0.0.Beta1
ADD ca.crt /etc/pki/ca-trust/source/anchors/ca.crt
RUN sudo update-ca-trust
USER root
RUN echo yes | keytool -keystore /etc/pki/java/cacerts -importcert \
               -alias HOSTDOMAIN -file /etc/pki/ca-trust/source/anchors/ca.crt \
               -storepass changeit
RUN curl -LO https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
         tar xvf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz
RUN mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/oc /usr/local/bin/oc && \
         chmod +x /usr/local/bin/oc
