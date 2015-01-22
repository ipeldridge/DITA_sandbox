DITA Sandbox
============

A place for testing DITA via the Puppet Enterprise QSG.

I'll try to keep this README updated as the experiments change. 

## Source

Contains task topics that I've ported over from the PE QSG .md files into DITA. `PE_QSG.ditamap` is the current map; it uses the conref strategy explained below.  


## Multi-topic Pages 

Most of my testing so far has been around trying to determine a best practice for getting multiple topics on a single page.

### conref 

Top-level or parent topics use conrefs within the task bodies to pull in additional tasks from the `source` directory in order to create multi-topic pages.  

### chunked 

Use the `chunk=to-content` parameter on all parent topics to create multi-topic pages. 

### Notes about Linking

For both strategies, the top-level supertask, `quick_start_supertask.dita`, is set to `collection-type=sequence` so that topic will demonstrate a clear sequence of events; because of this I've `linking=target-only` on all parent topics. This latter attribute prevents the "parent," "previous," "next" links from being applied to the parent topic. 










