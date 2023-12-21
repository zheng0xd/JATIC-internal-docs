# Organization Chart

## Purpose

This is a living document to track those who are currently working on the JATIC program.

A `*` next to a name indicates that the team member is consulted or informed, but does not work on the program day-to-day.

## PM team

The PM team is the core management team for the JATIC program. 

- The CDAO Chief of T&E leads the CDAO's AI T&E policy, tools development, and execution. 
- The Chief Product Owner (CPO) leads the product owners group and coordinates program-wide strategy, plans, and epics. This is primarily at a high-level - the vast majority of epics, features, and their prioritization will be provided by the product owners of the individual products.
- The Chief Engineer facilitates program level processes and execution, drives continuous value delivery, and ensures the technical integration between products. They lead integrated efforts such as the increment demo. They manage the Software Development Plan (SDP) and provide guidance and input to the Systems Engineering team, on topics such as the SDP, DevSecOps, security, infrastructure, and product testing.
- The Scrum of Scrums Master is the scrum master for the scrum of scrums team, facilitating the prioritization and removal of impediments across teams, and continuously improving the effectiveness of the Scrum of Scrums team.
- The AI T&E Expert has a deep technical understanding of the subject matter and domain in order to advise and support the product owners and development teams. Their primary role is the application of the software developed within the program to actual DoD AI algorithms to provide feedback for the team. They will also aid in the development, integration, and deployment of the products as necessary.
- The User Engagement Coordinator helps run and coordinate engagements between the program and users or user stakeholders. Their focus is on program-level engagements, but also aids in coordination of product-level and distributed/democratized engagements.

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Jon Elliott* | @jbelliott | jonathan.b.elliott2.civ@mail.mil | CDAO | Director of Assessment & Assurance |
| David Jin | @djin | david.jin5.civ@mail.mil | CDAO | PM & Chief Product Owner |
| Ari Kapusta | @akapusta | akapusta@mitre.org | MITRE | Chief Engineer |
| Michael Ide | @michaelide | mide@mitre.org | MITRE | Scrum of Scrums Master |
| Jason Gaulin | @jason.c.gaulin.civ | jason.c.gaulin.civ@mail.mil | CDAO | AI T&E Expert |
| Susan Urban | @surban | surban@mitre.org | MITRE | User Engagement Coordinator |
| Tabitha Colter | @tcolter | tcolter@mitre.org | MITRE | Strategic Outreach & Communication Lead |
| Kevin McCleary | @kmccleary | kmccleary@mitre.org | MITRE | product owner |

## ML T&E

MIT/LL, working as the "ML T&E team", is building the JATIC toolbox, a set of common types, protocols, utilities, and tooling to support and facilitate other tools development within the AI Assurance Toolbox.

[This board](https://gitlab.jatic.net/groups/jatic/-/boards/51?label_name[]=ML%20T%26E) can be used track ongoing work by this team. The label in Gitlab associated with this team is `ML T&E`.

This product can be found internally at [`jatic/cdao/jatic-toolbox`](https://gitlab.jatic.net/jatic/cdao/jatic-toolbox).

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Michael Yee | @myee | myee@ll.mit.edu | MIT/LL | Product Owner |
| Lei Hamilton | @lei.hamilton | lei.hamilton@ll.mit.edu | MIT/LL | Deputy Product Owner| 
| Justin Goodwin | @jgoodwin | jgoodwin@ll.mit.edu | MIT/LL | | 
| Garrett Botkin | @garrett.botkin | garrett.botkin@ll.mit.edu | MIT/LL | | 
| Olivia Brown | @olivia.brown | olivia.brown@ll.mit.edu | MIT/LL | |
| Manasi Sharma | @msharma | manasi.sharma@ll.mit.edu | MIT/LL | |
| Jeffrey Arena| @jarena | jeffrey.arena@ll.mit.edu | MIT/LL | | 
| Sanjeev Mohindra | @smohindra | smohindra@ll.mit.edu | MIT/LL | |
| Vince Mancuso* | @vincent.mancuso | vincent.mancuso@ll.mit.edu | MIT/LL | LL PM |

## Systems Engineering (Systems/DevSecOps Platform/Systems Engineering)

MITRE is the lead systems integrator for the JATIC program and is working as the ["Systems team"](https://scaledagileframework.com/system-team/) from the Scaled Agile Framework, but labeled as SysEng within JATIC. This covers the Software Development Plan (SDP), DevSecOps, security, infrastructure, product testing, product integration, and onboarding. 

The issues from the SysEng team are spread throughout many repos. [This board](https://gitlab.jatic.net/groups/jatic/-/boards/51?label_name[]=SysEng) can be used to track ongoing work by this team. The label in Gitlab associated with this team is `SysEng`.

The SDP can be found internally at [`jatic/docs/sdp`](https://gitlab.jatic.net/jatic/docs/sdp). 

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Shane Ficorilli | @sficorilli | sficorilli@mitre.org | MITRE | Development team lead |
| Tony Rice | @arice | arice@mitre.org | MITRE | Development team member |
| Chris Dillon | @cdillon | cdillon@mitre.org | MITRE | Development team member |
| Craig Sims | @csims-syseng | csims@mitre.org | MITRE | Product owner |

## Kitware

The Kitware team is building XAITK Saliency, an open-source python library for visual saliency algorithm interfaces and implementations to support explainable AI. 

[This board](https://gitlab.jatic.net/groups/jatic/kitware/-/boards) can be used track ongoing work by this team. 

This product can be found internally at [`jatic/kitware/xaitk-cdao`](https://gitlab.jatic.net/jatic/kitware/xaitk-cdao) and on GitHub at [`XAITK/xaitk-saliency`](https://github.com/XAITK/xaitk-saliency/).

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Brian Hu | @brian.hu | brian.hu@kitware.com | Kitware | Principal Investigator |
| Paul Tunison | @paul.tunison | paul.tunison@kitware.com | Kitware | Scrum Master |
| Alex Lynch | @alexander.lynch | alexander.lynch@kitware.com | Kitware | | 
| Emily Veenhuis | @emily.veenhuis | emily.veenhuis@kitware.com | Kitware | |
| Barry Ravichandran | @bharadwaj.ravichandran | bharadwaj.ravichandran@kitware.com | Kitware | |
| Brandon Richardwebster | @b.richardwebster | b.richardwebster@kitware.com | Kitware | |
| Stephen Crowell | @crowelsl | stephen.crowell@kitware.com | Kitware | |
| Mary Elise Dedicke | @mdedicke  | maryelise.dedicke@kitware.com | Kitware | Technical writer/documentation expert |
| Austin Whitesell | @awhitesell | awhitesell@mitre.org | MITRE | Product Owner |

## Two Six Technologies

The Two Six team is building Armory, a testbed for running scalable evaluations of adversarial defenses. 

[This board](https://gitlab.jatic.net/jatic/twosix/armory/-/boards/34) can be used track ongoing work by this team. 

This product can be found internally at [`jatic/twosix/armory`](https://gitlab.jatic.net/jatic/twosix/armory) and on GitHub at [`twosixlabs/armory`](https://github.com/twosixlabs/armory).

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Matt Wartell | @matt.wartell | matt.wartell@twosixtech.com | TwoSix | Scrum Master |
| Christopher Woodall | @christopher.woodall | christopher.woodall@twosixtech.com | TwoSix | Software Engineer |
| Kyle Treubig | @kyle.treubig | kyle.treubig@twosixtech.com | TwoSix | Software Engineer |
| Hamza Mahmood | @hamza.mahmood | hamza.mahmood@twosixtech.com | TwoSix | Machine Learning Engineer |
| Christopher Honaker | @honaker | christopher.honaker@twosixtech.com | TwoSix | Machine Learning Engineer |
| Rohitha Bhushan | @rohithabhushan | rohithabhushan@datamachines.io | Data Machines | Data Scientist | 
| Victoria Nagy | @victorianagy | victorianagy@datamachines.io | Data Machines | Data Scientist |
| Matthew Donizetti* | | matthew.donizetti@twosixtech.com | TwoSix | Principal Investigator |
| Josh Harguess | @jharguess | jharguess@mitre.org | MITRE | Product Owner |
| Jeff Gross | @jtgross | jtgross@mitre.org | MITRE | Technical SME |

## Team MetroStar

Team MetroStar is building an AI T&E platform prototype composed almost entirely of existing open-source technologies.

[This board](https://gitlab.jatic.net/groups/jatic/team-metrostar/-/boards) can be used track ongoing work by this team.

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Joe Early | @jearlyMSS | jearly@metrostar.com | MetroStar | Scrum Master & MetroStar PM |
| Eric Kelly | @ericdatakelly | edkelly@metrostar.com | MetroStar | Pr. Data Scientist |
| Scott Blair | @sblair | sblair@metrostar.com | MetroStar | Pr. DevSecOps Engineer |
| Wilson Rodden | @wrodden | wrodden@metrostar.com | MetroStar | Sr. Data Scientist |
| Ken Foster | @kenafoster | kfoster@metrostar.com | MetroStar | Pr. Systems Engineer |
| Jesse Scearce | @jscearce | jscearce@metrostar.com | MetroStar | ML Engineer |
| Vy Truong* | @IAMVY | vtruong@metrostar.com | MetroStar | CINO |
| Dharhas Pothina | @dharhas | dharhas@quansight.com | Quansight | Quansight PM |
| Andrew James | @amjames | ajames@quansight.com | Quansight | OSS PyTorch SME |
| Kim Pevey | @kcpevey | kcpevey@quansight.com | Quansight | Full Stack Dev |
| Eskild Eriksen | @iameskild | eeriksen@quansight.com | Quansight | DevSecOps |
| Christopher Ostrouchov | @costrouc | costrouchov@quansight.com | Quansight | DevSecOps |
| Amit Kumar | @akumar | akumar@quansight.com | Quansight | DevSecOps |
| Pavithra Eswaramoorthy | @peswaramoorthy | peswaramoorthy@quansight.com | Quansight | OSS SME and Developer Advocate |
| Jen Bishop | @jbishop | jbishop@openteams.com | Quansight | Project Manager / Project coordination |
| Smera Goel | @sgoel | sgoel@quansight.com | Quansight | UI/UX Designer |
| Jonathan Velando | @jvelando | jvelando@metrostar.com | Quansight | Pr. Software Engineer / Platform and OSS Software Engineer |
| Jonathan Bouder | @jbouder | jbouder@metrostar.com | Quansight | Pr. Software Engineer / Full-Stack Developer (UI/UX) |
| Sanjeev Mohindra | @smohindra | smohindra@ll.mit.edu | MIT/LL | Product Owner |

## ARiA

[This board](https://gitlab.jatic.net/groups/jatic/aria/-/boards) can be used track ongoing work by this team.

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Jason Summers | @jason.e.summers | jason.e.summers@ariacoustics.com | ARiA | Lead Scientist |
| Scott Swan | @scott.swan | scott.swan@ariacoustics.com | ARiA | Scrum Master |
| Jonathan Botts | @bottsj | jonathan.botts@ariacoustics.com | ARiA | SME |
| Max Bright | @max.bright | max.bright@ariacoustics.com | ARiA | SME |
| Jonathan Christian | @jchristian | jonathan.christian@ariacoustics.com | ARiA | SME |
| James Gleeson | @jcgleeson1 | james.gleeson@ariacoustics.com | ARiA | Developer |
| Robert Jullens | @shaun.jullens | shaun.jullens@ariacoustics.com | ARiA | Developer |
| Ed Schwab | @eschwab | ed.schwab@ariacoustics.com | ARiA | IT |
| Andrew Weng | @aweng | andrew.weng@ariacoustics.com | ARiA | Developer |
| Justin McMillan | @jmcmillan | justin.mcmillan@ariacoustics.com | ARiA | SME |
| Jason Inman | @jinman | jason.inman@ariacoustics.com | ARiA | Developer |
| Thayer Fisher | @tfisher | thayer.fisher@ariacoustics.com | ARiA | Developer |
| Bill Peria | @bperia | bill.peria@ariacoustics.com | ARiA | Developer |
| Jason Gaulin | @jason.c.gaulin.civ | jason.c.gaulin.civ@mail.mil | CDAO | Product Owner |

## IBM

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Jae Ro | @jaero | jaero@ibm.com | IBM | Technical lead |
| Matt Tilley | @matt.tilley | matt.tilley@ibm.com | IBM |  |
| Mark Baker | @mark-baker | mark.baker@ibm.com | IBM | |
| Jackson Lee | @jackson.lee | jackson.lee@ibm.com | IBM | |
| Adam Lockwood | @lockwooda | adam@nyla.io | IBM | | 
| Pin-Yu Chen | @pinyuchen-ibm | pin-yu.chen@ibm.com | IBM | |
| Kieran Fraser | @kieranfraser | kieran.fraser@ibm.com | IBM | |
| Beat Buesser | @beat-buesser | beat.buesser@ibm.com | IBM | ART Maintainer |
| Hannah Jung* | @mhjung | mhjung@ibm.com | IBM | Project executive |
| Mark Fisk* | @fiskm | fiskm@us.ibm.com | IBM | |
| David Yu | @dyu | syu@mitre.org | MITRE | Product Owner |

## MORSE

| Name | Gitlab | Email | Org | Role |
| ---- | ------ | ----- | --- | ---- |
| Peter Wein | @pwein | pwein@morsecorp.com | MORSE | Team lead |
| Nigel Mathes | @nmathes | nmathes@morsecorp.com | MORSE |  |
| Michael Nishida | @mnishida | mnishida@morsecorp.com | MORSE |  |
| Brian Lee | @blee | blee@morsecorp.com | MORSE | |
| Andrew Briasco-Stewart | @abriasco-stewart | abriasco-stewart@morsecorp.com | MORSE |  |
| George Bikhazi | @gbikhazi | gbikhazi@morsecorp.com | MORSE |  |
| Matthew Larsen | @mlarsen | mlarsen@morsecorp.com | MORSE |  |
| Ziyang Huang | @zhuang | zhuang@morsecorp.com | MORSE |  |
| Joel Sullivan | @jsullivan | jsullivan@morsecorp.com | MORSE |  |
| Eric Nelson* | @enelsonatmorse | enelson@morsecorp.com | MORSE |  |
| Eoin Daly | @Edaly | Edaly@morsecorp.com | MORSE |  |
| Dan Gombos | @dgombos | DGombos@morsecorp.com | MORSE | |
| Sarah Lipstone | @slipstone | slipstone@morsecorp.com | MORSE | |
| Rachel Rajaseelan | @rachel.rajaseelan | rachel.m.rajaseelan.civ@mail.mil | CDAO | Product Owner |
| Andreas Elterich | @andreas.g.elterich.ctr | andreas.g.elterich.ctr@mail.mil | CDAO | Technical SME |
