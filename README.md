**Introduction**

Shim is an open-source extensible API layer.  Its primary purpose is to provide REST access to resources that lack such an interface.  It can theoretically be used to access any Web or Internet service RESTfully.

This is accomplished by a Shim server which intercepts REST requests and bootstraps an ecosystem of open-source plugins to provide the resource-specific functionality needed to respond to such requests.

If a plugin exists for it, you can do REST with it.

**How it works in a nutshell.**

When a REST request is recieved at the REST service layer of a Shim server, the request is verified and passed to the bootstrap layer. The bootstrap layer tries to find a matching plugin.  If a plugin is found, it is invoked in order to satisfy the request, which is then passed onto the client.

Plugins exist as individual projects that must conform to a defined interface [link to interface].  This allows each maintainer to respond rapidly to changes in the IA of the underlying resources, giving consumers greater confidence in the availability of the resources they are interested in.

As anyone can run a shim server, there are a number of possible benefits to this architecture. For example some users may wish to have a private repository of plugins for their internal services which can only be accessed by a local Shim server.

**Project Status**

The project is currently in Phase 1: Planning, Iteration 1.  It is not yet functional.

**Structural overview**

Different areas of concern are layered in order to facilitate the growth and robustness of the Shim ecosystem, as outlined in this diagram:

[diagram 1 - model overview]

To visualise this in practice, this hypothetical chart gives an example of some (fake) use-cases:

[diagram 2 - model example]

The REQUEST -> RESPONSE process is outlined in greater detail here [request cycle diagram].  This diagram elucidates the logical flow and the data artifacts managed by the various levels of the Shim application stack.

**How to use - API Consumer**

If you wish to consume an existing Shim service, you simply issue a HTTP request as follows:

METHOD http://shim.example.com/plugin-uri/resource

If you're unsure what you can do with a particular resource, try submitting an OPTIONS request first to see what is available. (It is a requirement that ALL plugins implement OPTIONS).

**How to use - Plugin Developer**

At this stage, plugins can be written in Node.JS.  You are free to use any npm dependencies in your projects.

There are some specific requirements when structuring your plugin code.  Conforming to the shim interface specifications [link to interface specifications] is essential.

The command line tool "shim-cli" should be used during development to validate and test your code against the requirements.  The shim-cli tool can be found in the cli/bin folder of this repository.

**How to use - Server Maintainer **

The shim-server is located in the server/bin folder of this repository.  As the server is Node.JS based, you can run it from the command line as:

> node shim-server

By default, the Shim server runs on port 80.  You can adjust this by specifiying the port in the command line:

> node shim-server -p 8181

Shim server configurations are in server/etc/

**How to use - Shim developer**

You are encouraged to submit pull requests to the shim server or cli-tool.  These will be assessed by the core maintainers and merged in as they are accepted.

Your involvement serves to increase the utility and reach of Shim, and strengthens the interconnectivity of the Web and underlying Internet services.

The planned phases are:

1. Planning (current phase)
2. Initial Development (Not yet functional)
3. Alpha Development (Partial functionality - possibly bug infested)
4. Beta Development (Full functionality, bug fixing in progress)
5. Release Candidate (Full functionality, minor tweaks and bug fixes)
6. Stable Release (Maintenance development only)
7. Goto 1, for next iteration.

Each iteration will look at introducing new processes, tools and features to be assessed in the planning phase of each iteration.

**Iteration 1 development goals**

1. Define the Shim plugin interface requirements (no progress)
2. Provide basic documentation for developers and users (partial progress)
3. Implement the initial REQUEST->RESPONSE cycle workflow, as per this diagram [link to workflow], resulting in iteration 1 of shim-server (no progress)
4. Provide a basic shim-cli tool which can be used to validate and test plugins from the command line. (no progress)
5. Develop a basic plugin that can serve as a functional example for other plugin developers. (no progress)

**Support development**

As core maintainers we do not ask for donations for our work.  You can support development by spreading the word, adopting Shim in your own projects, or becoming a developer or co-maintainer.