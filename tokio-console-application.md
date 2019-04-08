// Personal information redacted

# Tokio Console
Tokio provides an instrumentation API using Tokio Trace as well as a number of
instrumentation points built into Tokio itself as well as the Tokio ecosystem.
The goal of the project it to implement a library for aggregation,
metrics of said instrumentation points and a console based UI that connects
to the process, allowing users to quickly visualize, browse and debug the data.

Because processes can encode structured and typed business logic with
tokio-trace based instrumentation points, a domain specific debugger
built upon those can provide powerful,
ad hoc tooling, e.g. filtering events by connection id,
execution context etcetera.
As instrumentation points of underlying libraries are collected as well,
it is easy to observe their behaviour and interaction.
This is an eminent advantage over traditional debuggers,
where the user instead observes the implementation.

This makes it a useful tool for monitoring live services
as well as investigating issues.

While the initial implementation will be in-process, eventually it should
support connecting to gRPC endpoints for data collection and streaming.
Though, the actual implementation is not an explicit goal of this project,
as the core functionality of the console can be shown and developed independently.
This motivates the following classification,
of which 2. and 3. will be explicit goals of the proposal.

 1. A network library which connects and listens to spans and events happening
    on the server side, emitting them locally via a subscriber like interface.
    This includes a server side subscriber + the gRPC implementation.
 2. A storage layer which builds upon 1. and provides an useful interface for
    aggregation, metrics, queries, etc.
 3. The (T)UI itself, which builds upon 2. and tries to display useful information,
    makes the information browsable etc. This includes designing useful widgets,
    different views (waterfall, timeline scrubbing), filters, etc.

As the intended users are mainly developers and devops,
it will be essential to communicate with and collect feedback from the broader community.
This includes two preview releases, during which acceptance and user needs will be evaluated.
The community interaction will hopefully also motivate other contributors,
ensuring longevity of the project.

# Schedule of Deliverables
I will be able to safely commit 2 full time days as well as 4-5 hours a day
on the remaining days per week. Hence i plan with the following schedule:

CW | Description
-- | --
22 | Project Setup, CI strategy and setup (UI tests, if yes, how?)
23 | TUI Setup with waterfall style logging
24 | Storage layer: Develop infrastructure for metrics, queries/filtering
25 | **Milestone: Develop and propose initial UI component concepts**, initial implementations, gather feedback
26 | Menu concept, managing views, <br> coordinating with tui-rs on crosstem input handling support
27 | Event Interactions: Filtering, brush up initial component implementations
28 | Adapt storage layer, validation: Use real world applications with tokio console, contribute instrumentation points to (existing?) users of tokio-trace <br> **Synchronization point**: Try to move the storage layer from in process to the network library. <br> This should be transparent to users of the storage layer, making it optional.
29 | Documentation: User Guides, how do i debug applications, etc <br> **Milestone: Release and announce a first preview version**, gather feedback of the broader community
30 | Incorporate Feedback, hopefully onboard new contributors, slack time to account for delays
31 | If network library not ready/available: contribute there <br>Otherwise: binary distributions, consider custom filters, distributable with 3rd party applications for easy debugging, devops
32 | Continue work from CW 31
33 | Documentation: Library Author Guides, what information to provide users, etc. <br> **Milestone: Release and announce a second preview version**, gather feedback of the broader community

As work items may turn out more or less difficult than anticipated, the schedule will be updated as we go.

# About me

// Biographical Information, education, open source experience
