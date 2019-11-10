# The DICT Protocol

As per [RFC 2229](https://www.ietf.org/rfc/rfc2229.txt), the Dictionary Server Protocol (DICT) is a TCP transaction based query/response protocol that allows a client to access dictionary definitions from a set of natural language dictionary databases. For more details see [dict.org](http://www.dict.org/w/). 

# How to use this image

## docker-compose

Here is an example using docker-compose.yml:

```yaml
services:
  dictd: &dict-base 
    image: amaccis/dict
  dict:
    <<: *dict-base
    entrypoint: "dict"
    depends_on:
      - dictd
```

Once the dictd container is up&running, you can use the client to perform queries:

```
docker-compose run --rm dict -h <dictd_container_ip> hacker
```
