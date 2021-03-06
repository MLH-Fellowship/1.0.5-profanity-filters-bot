Profanity Filters Bot
=====================

|License| |PR| |Lang|

.. |License| image:: https://img.shields.io/github/license/MLH-Fellowship/1.0.5-profanity-filters-bot?style=flat-square   :alt: GitHub
.. |PR| image:: https://img.shields.io/github/issues-pr/MLH-Fellowship/1.0.5-profanity-filters-bot?style=flat-square   :alt: GitHub pull requests
.. |Lang| image:: https://img.shields.io/github/languages/count/MLH-Fellowship/1.0.5-profanity-filters-bot?style=flat-square   :alt: GitHub language count

- A demo can be found on `Youtube <https://www.youtube.com/watch?v=T_aDZYCJVdM>`_
- Link to devpost `here <https://devpost.com/software/profanity-filter-bot>`_
- [NSFW] Release all you can say via Swagger under  `/predict <https://profanityfilterservice.herokuapp.com/>`_
- ``biLSTM`` trained on ``iMDB`` for sentiment analysis
- ``torchtext`` was built from ``master``, which can be found `here <https://github.com/pytorch/text>`_

instructions
++++++++++++

``make help`` for further instructions

- prepare pretrained embeddings do ``make init``
- To package the model to bento do ``make build``
- to run the docker container do ``make run``
- endpoint can be accessed through ``POST`` request via ``localhost:5000``

.. code-block:: shell

	curl -X POST 0.0.0.0:5000/predict -H "accept: */*" -H "Content-Type: application/json" \
	-d "{\"text\":\"I hate you this is the worst experience I have ever seen\"}"
	# > 0.2898484170436859

building `torchtext` from source
++++++++++++++++++++++++++++++++

- do ``git clone --recurse-submodules https://github.com/MLH-Fellowship/1.0.5-DiscoBot && cd torchtext``

- ``git submodules update --init --recursive && python setup.py clean install`` to build torchtext from source (currently at *0.8.0a0+8dc2125*)

  - to prep the pretrained embedding run ``make prep``, otherwise if you want to train the model parses ``ARGS=--train``, like so:

.. code-block:: shell

    # This will train the model
    make ARGS=--train prep 
