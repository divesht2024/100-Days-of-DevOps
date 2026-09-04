The Dockerfile was supposed to:

    Use the httpd:2.4.43 base image.
    Enable SSL in Apache.
    Copy certificates (server.crt, server.key) and a custom index.html into the container.

But when I attempted a build, it failed. At first, it looked like a file path issue, but on closer inspection, I noticed the real culprit.
