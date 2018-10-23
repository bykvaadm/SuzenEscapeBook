1. docker build -t gitbook ./
2. docker run -ti -v $(pwd)/book:/opt -p 80:4000 -p 8080:35729 gitbook /bin/bash -c 'cd /opt && gitbook install && gitbook serve --host 0.0.0.0'I
