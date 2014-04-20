:title: I'm DIGgin it. 
:author: Paul Logston
:description: A talk on the Domain Information Groper command line utility.
:keywords: dig, command line, POSIX, unix
:css: css/presentation.css

----

I'm DIGgin it!
======================
The Domain Information Groper
-----------------------------

.. image:: media/dig.jpg
  :height: 400
  :width: 400
  :scale: 50

| SLIDES: **http://logston.github.io/dig**

Thursday, May 1st 2014

----

Using dig
=========

::

    $ dig nycpython.com

    ; <<>> DiG 9.8.1-P1 <<>> nycpython.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52392
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;nycpython.com.                 IN      A

    ;; ANSWER SECTION:
    nycpython.com.          1799    IN      A       54.204.41.210

    ;; Query time: 135 msec
    ;; SERVER: 10.0.2.3#53(10.0.2.3)
    ;; WHEN: Sat Apr 19 21:35:49 2014
    ;; MSG SIZE  rcvd: 47

----

Output SECTIONS
===============

::

    $ dig nycpython.com
    ...

::
  
      ;; QUESTION SECTION:
      ;nycpython.com.                 IN      A

::

    ;; ANSWER SECTION:
    nycpython.com.          1799    IN      A       54.204.41.210

::
  
  Authority and Additional Sections.

::

    ;; Query time: 135 msec
    ;; SERVER: 10.0.2.3#53(10.0.2.3)
    ;; WHEN: Sat Apr 19 21:35:49 2014
    ;; MSG SIZE  rcvd: 47

----

Options
=======

::

  (Specify Sections)
  +[no]stats
  +[no]answer
  +[no]...
  
  eg. $ dig nycpython.com +nostats
      ...

::

  (Specify a file with multiple FQDNs)
  -f <file>

  eg. $ dig -f names.txt
      ...

::

  (Just grab the IP)
  +short

  eg. $ dig nycpython.com +short
      54.204.41.210

----

Options
=======

::
  
  (Specify type of DNS record)
  -t MX or MX

  eg. $ dig nycpython.com -t MX
      ...

      $ dig nycpython.com MX
      ...

----

Options
=======

::

  $ dig nycpython.com +trace

  ; <<>> DiG 9.8.3-P1 <<>> nycpython.com +trace
  ;; global options: +cmd
  .                       326518  IN      NS      b.root-servers.net.
  .                       326518  IN      NS      i.root-servers.net.
  .                       326518  IN      NS      f.root-servers.net.
                          ... 
                          
  ;; Received 228 bytes from 192.168.1.1#53(192.168.1.1) in 88 ms

  com.                    172800  IN      NS      i.gtld-servers.net.
  com.                    172800  IN      NS      a.gtld-servers.net.
  com.                    172800  IN      NS      k.gtld-servers.net.
                          ...

  ;; Received 503 bytes from 192.33.4.12#53(192.33.4.12) in 27 ms
  
  nycpython.com.          172800  IN      NS      ns1.badger.com.
  nycpython.com.          172800  IN      NS      ns2.badger.com.
  ;; Received 106 bytes from 192.42.93.30#53(192.42.93.30) in 273 ms

  nycpython.com.          1800    IN      A       54.204.41.210
  nycpython.com.          3600    IN      NS      ns2.badger.com.
  nycpython.com.          3600    IN      NS      ns1.badger.com.
  ;; Received 90 bytes from 54.246.101.22#53(54.246.101.22) in 100 ms

----

Questions
=========

.. image:: media/dog_dig.jpg
  :height: 400
  :width: 400
  :scale: 50
      
My Own Quetions
---------------

    - Why are there ``;;`` in front of info for dig?

