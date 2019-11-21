---


---

<h1 id="waterfall-development-and-its-problems">Waterfall Development and its problems</h1>
<h2 id="history-of-the-waterfall-model">History of the Waterfall model</h2>
<p>The waterfall model was first described by Winston Royce in 1970 in his article, Managing the Development of Large Software Systems. He didn’t refer to this model as the waterfall model, but he is credited with the first formal description of what we know as the waterfall model. Royce’s original article consists of the following stages :</p>
<ul>
<li>Requirement specification</li>
<li>Design</li>
<li>Contruction</li>
<li>Integration</li>
<li>Testing and debbuging</li>
<li>Installation (deployment)<strong>strong text</strong></li>
<li>Maintenance</li>
</ul>
<h2 id="how-does-waterfall-work-">How does Waterfall Work ?</h2>
<p><img src="https://www.tutorialspoint.com/sdlc/images/sdlc_waterfall_model.jpg" alt="enter image description here"></p>
<ol>
<li><strong>Requiements Analysis</strong> : All possible requirements of the system to be developed are captured in this phase and documented in a requirement specification document usualy written by buisness analyst.</li>
<li><strong>System Design</strong> : The requirement specifications from first phase are studied in this phase and the system design is prepared. This system design helps in specifying hardware and system requirements and helps in defining the overall system architecture</li>
<li><strong>Implementation</strong> : With inputs from the system design, the system is first developed in small programs called units, which are integrated in the next phase. Each unit is developed and tested for its functionality, which is referred to as Unit Testing.</li>
<li><strong>Integration and Testing</strong> : All the units developed in the implementation phase are integrated into a system after testing of each unit. Post integration the entire system is tested for any faults and failures.</li>
<li><strong>Deployment of system</strong> : Once the functional and non-functional testing is done; the product is deployed in the customer environment or released into the market.</li>
<li><strong>Maintenance</strong> : There are some issues which come up in the client environment. To fix those issues, patches are released. Also to enhance the product some better versions are released. Maintenance is done to deliver these changes in the customer environment.</li>
</ol>
<h2 id="where-is-waterfall-suitable-">Where is Waterfall suitable ?</h2>
<ul>
<li>Where requirements are well documented, clear and fixed.</li>
<li>Where product definitaion is stable.</li>
<li>When underlying technologie is well understood.</li>
<li>No ambiguous requirements</li>
<li>Where the project is short</li>
<li>Suitable resources available.</li>
</ul>
<h2 id="advantages-and-disadvantages-of-waterfall">Advantages and Disadvantages of Waterfall</h2>
<p>Advantages</p>
<ul>
<li><strong>Easier scheduling and control</strong> : As the project is splitted into differents stages.</li>
<li><strong>Departmentalization</strong> :  As the project is splitted into differents stages you can assign differents roles to different departements and give them clear delivery board.</li>
</ul>
<p>Disadvantages</p>
<ul>
<li>Does not allow for reflection or revision as the requirements are not supposed to change.</li>
<li>Once in testing stage, change is hard</li>
</ul>

<table>
<thead>
<tr>
<th>PROS</th>
<th>CONS</th>
</tr>
</thead>
<tbody>
<tr>
<td>Simple and easy to understand</td>
<td>No working software until late in the cycle</td>
</tr>
<tr>
<td>Easy to manage</td>
<td>High amounts of risk and uncertainty</td>
</tr>
<tr>
<td>Phases are completed one at a time</td>
<td>Not good for complex projects</td>
</tr>
<tr>
<td>Works well for smaller projects</td>
<td>Not good where change is expected</td>
</tr>
<tr>
<td>Clearly defined stages</td>
<td>Change is scope can end a project</td>
</tr>
<tr>
<td>Well understood milestones</td>
<td>Integration and delivery is done as a Big Bang</td>
</tr>
<tr>
<td>Process and results are well documented</td>
<td></td>
</tr>
<tr>
<td>Tasks are easy to arrange for a project manager</td>
<td></td>
</tr>
</tbody>
</table><h2 id="history-of-the-v-model">History of the V-Model</h2>
<ul>
<li>The V-Model is a modified version of the Waterfall model.</li>
<li>Designed to be non-linear.</li>
<li>Testing phase for each corresponding development stage.</li>
<li>Verification phases on one side and validation phases on the other side.<br>
<img src="https://www.wisdomjobs.com/userfiles/sdlc_v_model.jpg" alt="enter image description here"></li>
</ul>
<h1 id="what-is-agile-all-about">What is Agile all about?</h1>
<h2 id="what-is-agile">What is Agile?</h2>
<ul>
<li>Software evolves over time.</li>
<li>Adaptive planning, evolutionary development, early delivery.</li>
<li>Deliver value to the business sooner.<br>
<img src="https://www.spf-consulting.ch/file/2018/09/agile-project-management-vs-waterfall-project-management.png" alt="enter image description here"></li>
</ul>
<h2 id="the-history-of-agile.">The History of Agile.</h2>
<p>On February the 11th to the 13th, 2001 at the lodge at the Snowbird Ski Resort in the mountains of Utah, 17 people met to try and find common ground. What emerged was the Agile Software Development Manifesto. Representatives from extreme programming, Scrum, DSTM, adaptive software development, crystal, feature-driven development, pragmatic programming, and other sympathetic to the need of alternative to documentation-driven, heavyweight software development processes convened. This group named themselves The Agile Alliance.</p>
<h2 id="the-agile-manifesto-4-core-values.">The Agile Manifesto 4 Core Values.</h2>
<blockquote>
<p>We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value :</p>
</blockquote>
<ul>
<li><strong>Individuals and interactions over processes and tools.</strong><br>
Software systems are built by people, and to do this properly, they all need to work together and have good communication between all parties. It isn’t just software developers, but it includes QA, business analysts, project managers, business sponsors, and senior leadership, and anyone else involved in the project at your organization. Processes and tools are important, but they’re irrelevant if the people working on the project can’t work together effectively and communicate.</li>
<li><strong>Working software over comprehensive documentation.</strong><br>
Let’s face it, who reads a 100-page product specs. I certainly don’t. Your business users would much prefer to have small pieces of functionality delivered quickly so they can then provide feedback. These pieces of functionality may even be enough to deploy to production to gain benefit from them early. Not all documentation is bad though. When my teams work on a project, they use Visio or similar tools to produce diagrams of, and this is not an exhaustive list, deployment environments, database schemas, software layers, and news case diagrams. We normally print these out on an A3 printer and put them up on the walls so they are visible to everyone. Small, useful pieces of documentation like this are invaluable, 100-page product specs are not as 9 times out of 10 they’re invalid and out of date before you’re finished writing them. So remember, the primary goal is to develop software that gives the business benefit, not extensive documentation.</li>
<li><strong>Customer collaboration over contract negotiation.</strong><br>
All the software that you develop should be written with your customer’s involvement. To be successful at software development, you really need to work with them daily. This means inviting them to your standups, demoing to them regularly, and inviting them to any design meetings. At the end of the day, only the customer can tell you what they really want. They may not be able to give you all the technical details, but that is what your team is there for, to collaborate with them, understand their requirements, and to deliver on them</li>
<li><strong>Responding to change over following a plan.</strong><br>
Your customer or business sponsor may change their minds about what is being built. This may be because you’ve given them new ideas from the software you delivered in a previous situation. It may be because the company’s priorities have changed, or a new change has come into force. The key thing here is you should embrace it. Yes, some time might get thrown away, and some time may be left, but if you are working in short situations, then this time lost is minimized. Change is a reality of software development, a reality that your software process must reflect. There’s nothing wrong with having a project plan. In fact, I’ll be worried about any project that didn’t have one. However, a project plan must be flexible enough to be changed. There must be room to change it as your situation changes, otherwise your plan quickly becomes irrelevant.</li>
</ul>
<h2 id="the-agile-manifesto-12-principles.">The Agile Manifesto 12 Principles.</h2>
<p>On to pinning the four core values of the Agile Manifesto, we have 12 principles that should be followed. These 12 principles can be split down into three main groups: Regular delivery of software, Team communication, Excellence in design.</p>
<p><strong>This first section looks at the agile principles concerned with regular delivery of software :</strong></p>
<blockquote>
<p>Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.</p>
</blockquote>
<p>Teams work together best when they trust each other. It is common for tension to exist between the customer and the delivery team, but when the customer is satisfied by constant delivery of valuable software early rather than later, trust is built. The term valuable is important. In Scrum, for example, the customer or product owner decides what is valuable. The product backlog is prioritized and the most valuable features are delivered first.</p>
<blockquote>
<p>Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.</p>
</blockquote>
<p>It is important to deliver software frequently. Scrum and XP, for example, is built around this principle. Under Scrum and XP, features are delivered in sprints of two to four weeks with a preference towards two weeks.</p>
<blockquote>
<p>Working software is the primary measure of progress.</p>
</blockquote>
<p>With this we are saying that the software not only must valuable and delivered often, but it must be working. Scrum, for example, requires features to me, a team to find definition of done. Ideally this should mean that the feature is potentially shippable.</p>
<blockquote>
<p>Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.</p>
</blockquote>
<p>As teams build trust and deliver software over and over, a constant pace that is sustainable without over taxing anyone will emerge. This allows the team to work forever, or until enough value has been added to the product. An important aspect of this is regular releases of the product. If the team can deliver a shippable product each quarter, for example, it makes conversations with the customer much easier.</p>
<p><strong>This second section looks at the agile principles concerned with the team communication :</strong></p>
<blockquote>
<p>Business people and developers must work together daily throughout the project.</p>
</blockquote>
<p>The whole team needs to be readily available to each other. Scrum, for example, uses the daily standup meeting as a critical communication mechanism. Here, the team reports what was accomplished since the last meeting, what will be accomplished by the next meeting, and if there are any impediments to completing this feature in the sprint. This meeting exposes issues early so they can be addressed before they become critical.</p>
<blockquote>
<p>The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.</p>
</blockquote>
<p>This principle was offered before geographically separate teams were common. Today, with offshore teams and teams that are divided across the country and the globe, regular face-to-face communication is not often possible. Online meetings and instant messaging tools are available that improve communication when teams are separated. Meetings that include the whole team may be planned so that face-to-face communication is possible. This does add cost to the project because portions of the team need to travel to a central location for the meeting. This approach is helpful for important meetings like sprints and release planning. When offshore resources are used, portions of the offshore team may be rotated to your internal team for a period of time. This allows team members to interact personally and get to know each other. It allows the offshore team to return home with firsthand experience that helps the remote team gain valuable insight. This is often a win-win situation because offshore team members look forward to an experience with the main project team. When possible, try to separate out teams so the individual teams are collocated. For example, it is better to have one whole team in the UK and another team in India than it is to have teams split. This allows the individual teams to benefit from face-to-face communication. Separated teams do pose a challenge and a cost, but on large projects, the incremental cost addition is often worth the experience.</p>
<blockquote>
<p>The best architectures, requirements, and designs emerge from self-organizing teams.</p>
</blockquote>
<p>The team knows the best way to get something done, they are the experts; however, this does not mean that the right outcome will always happen on its own. Each individual is at a different place in his or her own personal growth and career. The term servant leader has emerged in the agile community and replaces a typical command of control project manager. A servant leader observes how the members of the team operate and interact with each other. He or she asks the probing questions and acts as a flashlight, shining a light on areas that individual team members may not notice. It is important for the servant leader to treat everyone with respect and dignity, even when tensions are high. Conflict amongst team members is normal, and actually a good thing. A servant leader understands this and embraces a healthy debate. Self-organizing teams do not happen automatically, they emerge under the proper guidance and the advice of a servant leader.</p>
<blockquote>
<p>Build projects around motivated individuals. Give them the environment and the support they need, and trust them to get the job done.</p>
</blockquote>
<p>This is an extension of self-organizing teams. There are some important words in this principle. No one would ever admit to not being motivated. Servant leader pays attention to the aspirations and goals of the team members, and aligns these goals with the project needs wherever possible. People perform best when they are doing something they are passionate about. A good agile leader also shelters the team from outside distractions. In Scrum, for example, a team commits to completing a set of features. Anything that distracts from this is a risk. By being there for the team, the servant leader provides them with an environment and support needed for success. Trust is not automatic, but it is built over time, and it is easy to lose. Team members must trust each other and be comfortable with conflict.</p>
<blockquote>
<p>At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behaviors accordingly.</p>
</blockquote>
<p>Scrum uses the retrospective for this process. Teams often needs help for these activities to be effective. People may be challenged when it comes to engaging in true self-reflection. This is all part of the agile journey, and each of the agile principles are interrelated. The retrospective is the perfect place for the team to reflect and improve. It is up to the Scrum Master to elicit self-reflection. Once we have identified areas for improvement, we need to really improve. If teams spend time reflecting and do not improve, they see the retrospection as a waste of time. It is, again, up to the Scrum Master to tactfully remind the team about the areas of improvement they agreed upon. Some teams hang the points they agreed to up on the wall where the standup meetings take place.</p>
<p><strong>This third section looks at the agile principles is all about excellence in design :</strong></p>
<blockquote>
<p>Continuous attention to technical excellence and good design enhances agility.</p>
</blockquote>
<p>We need to pay close attention to the technical excellence and design as our products evolve. There is a balance between building the right thing and building the thing right. We must also be wary of delivering fragile systems. If we make a few changes and our application falls apart, like a house of cards, we’re not in a good place. Extreme programming, and to some degree Scrum, recommends test-driven development and automated builds as a way of avoiding fragile solutions. When we have a set of proper automated unit tests, that were included in some sort of automated build, we see problems every time the build runs. The higher our code coverage is and the closer we get to continuous integration, the better our solutions will be. It’s all about balance. Over time, our solution will accumulate technical debt. As we weigh the tradeoffs between building it right and building the right thing, this is bound to happen. It is best to include a few technical debt features along with features that add value in sprints, so each sprint is delivering business value.</p>
<blockquote>
<p>Simplicity, the art of maximizing the amount of work not done, is essential.</p>
</blockquote>
<p>Agile is all about doing the right amount of something at any given time, and no more. We should often use a story small enough to get the job done, and no more. She should build what we know we need now. We should not build some huge framework we think we may need some day. It is critical to have a complete and thorough understanding of the software frameworks we use.</p>
<blockquote>
<p>Welcome changing requirements, even late in development. Agile processes harness change for the customer’s competitive advantage.</p>
</blockquote>
<p>This principle will scare teams who are used to waterfall projects. At first glance it seems crazy to welcome change late in the development process. Late in development means late in the release of the complete product. Scrum, for example, delivers features in short sprints. Because we are delivering features in short cycles, change is part of the whole process. In Scrum, the change is directed by the product owner. It is up to the product owner to understand what the competitive advantage is for each feature in the backlog.</p>
<h2 id="agile-methodology-overview.">Agile Methodology Overview.</h2>
<p>In this section, we’ll take a look at some of the Agile methodologies that are in use today. Which are :</p>
<ul>
<li>
<p><strong>Scrum :</strong><br>
Scrum, is a lightweight management framework with broad appeal for managing iterative and incremental projects of all types. Ken Schwaber, Mike Beedle, Jeff Sutherland, and others contributed significantly to the evolution of Scrum over the last decade and a half. Over the last few years in particular, Scrum has garnered increasing popularity in the software community due to its simplicity, proven success, and improved productivity, and its ability to act as a wrapper for various engineering practices promoted by other agile methodologies.</p>
</li>
<li>
<p><strong>Extrem programming (XP) :</strong><br>
Extreme programming was originally devised by Kent Beck and has emerged as one of the more popular and controversial agile methods. XP is a disciplined approach to delivering high-quality software quickly and continuously. It promotes high customer involvement, rapid feedback loops, continuous testing, continuous planning, and close teamwork to deliver working software at very frequent intervals, typically every one to three weeks. The original XP recipe is based on four simple values, simplicity, communication, feedback, and courage. And there’s also 12 supporting practices. These are :</p>
<ol>
<li>The planning game.</li>
<li>Small releases.</li>
<li>Customer acceptance tests.</li>
<li>Simple design.</li>
<li>Pair programming.</li>
<li>Test-driven development.</li>
<li>Refactoring.</li>
<li>Continuous integration.</li>
<li>Collective code ownership.</li>
<li>Coding standards.</li>
<li>Metaphors.</li>
<li>Sustainable pace.</li>
</ol>
</li>
<li>
<p><strong>The crystal methodology :</strong><br>
The crystal methodology is one of the most lightweight adaptable approaches to software development. Crystal is actually comprised of a family of methodologies, like crystal clear, crystal yellow, and crystal orange. These unique characteristics are driven by several factors, such as team size, system criticality, and project priorities. This crystal family addresses the realization that each project may require a slightly tailored set of policies, practices, and processes in order to meet the project’s unique characteristics</p>
</li>
<li>
<p><strong>Dynamic systems development method, or DSDM :</strong><br>
DSDM dates back to 1994 and grew out of the need to provide an industry project delivery framework for what is referred to as rapid application development, or RAD for short. While RAD was extremely popular in the early 1990s, the RAD approach to software delivery evolved in a fairly unstructured manner. As a result, the DSDM consortium was created and convened in 1994 with the goal of devising and promoting a common industry framework for rapid software delivery. Since 1994, the DSDM methodology has evolved to mature to provide a comprehensive foundation for planning, managing, executing, and scaling agile and iterative software development projects. DSDM is based on nine key principles that primarily revolve around :</p>
<ol>
<li>Active user involvement is imperative.</li>
<li>DSDM teams must be empowered to make decisions.</li>
<li>The focus is on frequent delivery of products.</li>
<li>Fitness for business purpose is the essential criterion for acceptance of deliverables.</li>
<li>Iterative and incremental development is necessary to converge on an accurate business solution.</li>
<li>All changes during development are reversible.</li>
<li>Requirements are baselined at a high level.</li>
<li>Testing is integrated throughout the life cycle.</li>
<li>A collaborative and cooperative approach between all stakeholders is essential.</li>
</ol>
<p>DSDM specifically calls out fitness for business purpose as the primary criteria for delivering and acceptance of the system, focusing on the useful 80% of the system that can be deployed in 20% of the time.</p>
</li>
<li>
<p><strong>Feature-driven design, or FDD :</strong><br>
Feature-driven design was originally developed by Jeff De Luca. The first incarnations of FDD occurred as a result of collaborations between De Luca and a thought leader, Peter Coad. FDD is a model driven, short iteration process. It begins with establishing an overall model shape. Then it continues with a series of two week design by feature, build by feature iterations. The features are small and useful in the eyes of the client. FDD designs the rest of the development process around feature deliveries, and they follow eight practice. Domain object modeling, developing by feature, components and class ownership, feature teams, inspections, configuration management, regular builds, visibility of progress, and results.</p>
</li>
<li>
<p><strong>Lean software development :</strong><br>
Lean software development is an iterative methodology, originally developed by Mary and Tom Poppendieck. Lean software development owes much of its principles and practices to the lean enterprise movement and the practices of companies like Toyota. Lean software development focuses the team on delivering value to the customer and on the efficiency of the value stream and the mechanisms that deliver that value. The main principles of lean include eliminating waste, amplifying learning, deciding as late as possible, delivering as fast as possible, empowering the team, building integrity, and seeing the whole. Lean eliminates waste by selecting only the truly valuable features for a system, prioritizing and delivering them in small batches. It emphasizes the speed and efficiency of development workflow and relies on rapid and reliable feedback between programmers and customers.</p>
</li>
<li>
<p><strong>Kanban :</strong><br>
Kanban is applied to software development, is a pool-based planning and execution method. Rather than planning work items upfront and pushing them into the work queue for the other team, the team signals when they are ready for more work and pools it into their queue. Kanban historically uses cards to signal the need for an item. For software developments teams, these cards are kept on a kanban board, which is organized into columns and rows. The columns represent the different states of a work item, from initial planning through customer acceptance. The specific column the team uses should meet the needs of the team and be tailored to their context. The rows on the kanban board represent work items. Work items are sometimes grouped within areas such as feature sets and category types. Kanban focuses on maximizing the throughput of the team. One of the ways this achieves its goal is through the application of work-in-process-limits, or WIP limits, and each of the states have a work item. Under a kanban or lean approach, queues or entries of work in a any state are seen as waste. The work-in-process limits enable a team to focus on the optimal flow of work items through the system, minimizing any associated waste. Kanban allows teams to achieve process optimizations while respecting and maintaining in a sustainable pace. Next, we’ll take a look at some of the different roles in an agile team.</p>
</li>
</ul>
<h2 id="roles-within-an-agile-team.">Roles Within an Agile Team.</h2>
<h2 id="summary">Summary</h2>

