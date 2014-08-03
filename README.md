Introduction
============

Shim is an open-source extensible API layer.  Its primary purpose is to provide REST access to resources that lack such an interface.  It can theoretically be used to access any Web or Internet service RESTfully.

tl;dr: If a Shim plugin (aka Shimmer) exists for it, you can REST it.

How Shim works
--------------

When a HTTP request is recieved at the REST layer of a Shim server, the request is verified and passed to the bootstrap layer. The bootstrap layer tries to find a matching Shimmer in the Shim plugin ecosystem.  If a Shimmer is found, it is invoked to satisfy the request.

The Shim Philosophy
-------------------

The driving principle behind Shim is to foster a large ecosystem of useful Shimmer plugins covering a wide range of services.

Ease of use is key to adoption and is a key design consideration.  Anyone should be able to write a Shimmer, and anyone should be able to run a shim server without a huge amount of configuration.

In time, the Shim bootstrap layer will support a number of transports including package managers, source control repositories, distributed filesharing protocols and more, increasing the robustness and reach of the Shimmer ecosystem.

Security is another key consideration.  As Shim acts as a proxy of sorts, support for encrypted transports is a must.  However as Shimmers 

Project Status
--------------

The project is currently in Phase 1: Planning, Iteration 1.  It is not yet functional.

How to use - API Consumer
-------------------------

If you wish to consume an existing Shim service, you simply issue a HTTP request as follows:

METHOD http://shim.example.com/plugin-uri/resource

If you're unsure what you can do with a particular resource, try submitting an OPTIONS request first to see what is available. (It is a requirement that ALL plugins implement OPTIONS).

How to use - Plugin Developer
-----------------------------

At this stage, plugins can be written in Node.JS.  You are free to use any npm dependencies in your projects.

There are some specific requirements when structuring your plugin code.  Conforming to the shim interface specifications [link to interface specifications] is essential.

The command line tool "shim-cli" should be used during development to validate and test your code against the requirements.  The shim-cli tool can be found in the cli/bin folder of this repository.

How to use - Server Maintainer
------------------------------

The shim-server is located in the server/bin folder of this repository.  As the server is Node.JS based, you can run it from the command line as:

> node shim-server

By default, the Shim server runs on port 80.  You can adjust this by specifiying the port in the command line:

> node shim-server -p 8181

Shim server configurations are in server/etc/

How to use - Shim developer
---------------------------

You are encouraged to submit pull requests to the shim server or cli-tool.  These will be assessed by the core maintainers and merged in as they are accepted.

Your involvement serves to increase the utility and reach of Shim, and strengthens the interconnectivity of the Web and underlying Internet services.

Development Phases
------------------

The planned phases are:

1. Planning (current phase)
2. Initial Development (Not yet functional)
3. Alpha Development (Partial functionality - possibly bug infested)
4. Beta Development (Full functionality, bug fixing in progress)
5. Release Candidate (Full functionality, minor tweaks and bug fixes)
6. Stable Release (Maintenance development only)
7. Goto 1, for next iteration.

Each iteration will look at introducing new processes, tools and features to be assessed in the planning phase of each iteration.

Iteration 1 development goals
-----------------------------

1. Define the Shim plugin interface requirements (partial progress)
2. Provide basic documentation for developers and users (partial progress)
3. Implement the initial REQUEST->RESPONSE cycle workflow, as per this diagram [link to workflow], resulting in iteration 1 of shim-server (no progress)
4. Provide a basic shim-cli tool which can be used to validate and test plugins from the command line. (no progress)
5. Develop a basic plugin that can serve as a functional example for other plugin developers. (no progress)

Structural overview
-------------------

Different areas of concern are layered in order to facilitate the growth and robustness of the Shim ecosystem, as outlined in this diagram:

[diagram 1 - model overview]

To visualise this in practice, this hypothetical chart gives an example of some (fake) use-cases:

[diagram 2 - model example]

The REQUEST -> RESPONSE process is outlined in greater detail here [request cycle diagram].  This diagram elucidates the logical flow and the data artifacts managed by the various levels of the Shim application stack.

Support development
-------------------

As core maintainers we do not ask for donations for our work.  You can support development by spreading the word, adopting Shim in your own projects, or becoming a developer or co-maintainer.