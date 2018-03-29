# KRNNT tagger

This a definition of a docker image of the KRNNT tagger + all its dependencies. 

The source of the Docker image is available at:
https://github.com/apohllo/dockerfiles/blob/master/tagger/Dockerfile

The source code of the tagger is available at:
https://github.com/kwrobel-nlp/krnnt

The configuration of the dependencies is described at:
http://nlp.pwr.wroc.pl/redmine/projects/libpltagger/wiki/InstallOnUbuntu11

The tagger is available as a server running on port 9200, accepting POST requests.
The server responds with the input text tagged in `plain` format.

## Usage

To download the image and start the tagging server:

```
docker run -it -p 9200:9200 apohllo/krnnt:0.1 python3 /home/krnnt/krnnt/krnnt_serve.py /home/krnnt/krnnt/data
```

To tag a text using curl (with the server running):

```
curl -XPOST localhost:9200 -d "Ala ma kota."
```

You should get the following result:

```
Ala	none
	Ala	subst:sg:nom:f	disamb
ma	space
	mieć	fin:sg:ter:imperf	disamb
kota	space
	kot	subst:sg:acc:m2	disamb
.	none
	.	interp	disamb
```
