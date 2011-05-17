Google Reader API lib (unofficial)
==================================

This lib is a fork of [pyrfeed](http://code.google.com/p/pyrfeed/)

Docs
----

For documentation about the unofficial Google Reader API you can read [GoogleReaderAPI](http://code.google.com/p/pyrfeed/wiki/GoogleReaderAPI)

Quick Start
-----------

    from GoogleReader import  CONST
    from GoogleReader.reader import GoogleReader

    gr = GoogleReader()
    l = ('mymail@google.com', 'mypassword')
    gr.identify(*l)
    gr.login()
    
    #Example to subscribe to a new feed
    gr.add_subscription(url="https://gist.github.com/brutuscat.atom")

    #Get a feed with the Starred entries
    xmlfeed = gr.get_feed(feed=CONST.ATOM_STATE_STARRED)

    #Get a feed with unread entries of subscritions labeled "important"
    xmlfeed = gr.get_feed(feed=CONST.ATOM_PREFIXE_LABEL + "important", 
                          exclude_target=CONST.ATOM_STATE_READ) #Excludes the Read entries ;)

    #Using the JSON api to get more detailed info about items in the feed
    #:- Just add the json=True
    jsonstream = gr.get_feed(url='http://www.joelonsoftware.com/rss.xml', json=True)
    likes = jsonstream['items'][0]['likingUsers']
    
    #The same examples as before seems to be working for the json api too
    jsonstream2 = xmlfeed = gr.get_feed(feed=CONST.ATOM_PREFIXE_LABEL + "important",
                          exclude_target=CONST.ATOM_STATE_READ, json=True)
    
You can also modify and run the GoogleReader.test() method to see if everything is running smoothly.
