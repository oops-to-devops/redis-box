sa-redis
=========

[![Build Status](https://travis-ci.org/softasap/sa-redis.svg?branch=master)](https://travis-ci.org/softasap/sa-redis)


Installs basic redis setup with necessary system adjustments. Optional config patch.

If you have node, installs redis commander https://github.com/joeferner/redis-commander  with option  option_install_redis_commander: true

Example of use:

<pre>

     - {
         role: "sa-redis"
       }

</pre>

Advanced:

<pre>


     - {
         role: "sa-redis",
         redis_bind_to: 0.0.0.0,
         redis_properties:
           - {regexp: "^bind *", line: "bind {{redis_bind_to}}"}
           - {regexp: "^requirepass *", line:"requirepass YOUR_SECURE_PASS"}
         option_install_redis_commander: true,
         option_install_using_chris_lea_ppa: true        
       }


</pre>


Creating the password:


$ redis-cli Run PING on redis console

127.0.0.1:6379> PING (error) NOAUTH Authentication required.

Now use AUTH and input your password.

127.0.0.1:6379> AUTH 84e5145797f2a1593a38677389c081630ce67cd3b5f272f3f750c5ae2cf50090 OK

If authentication is successful it will return OK. Now if you run PING again, it will return PONG as expected.

127.0.0.1:6379> PING PONG 127.0.0.1:6379>


Ideas for some random password:

Creating an MD5 Hash for a Redis password

echo "sa-redis" | md5sum
7ea22b9f6fb7f5ad679b59aa3aa349f0  -


Creating an SHA1 Hash for a Redis password

➜  ~  echo "sa-redis" | sha1sum
2b03a562498cffe7558f40131646bac6111d3881  -


Creating a SHA256 Hash for Redis password

➜  ~  echo "sa-redis" | sha256sum
84e5145797f2a1593a38677389c081630ce67cd3b5f272f3f750c5ae2cf50090  -
