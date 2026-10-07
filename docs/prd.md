2# CourtView Product Requirements Document

Basketball Community, Clubs, and Video Analysis Service

Version 0.1  |  October 6, 2026  |  For Review

## 1 Product Overview

CourtView is an app that analyzes users’ basketball training and game videos to help them assess their shooting, dribbling, and rebounding skills and apply the findings to their training. Motion Analysis evaluates form and execution quality, while Game Analysis presents metrics that reflect performance and impact in actual games.

This PRD is a proposal for review that brings together community, Net, basketball court, NBA information, and account features with analysis experiences across three skill areas. The product owner will determine which BKDUNK features to incorporate into CourtView and how the two names relate. The workflow connecting video collection to analysis results is proposed as an operational requirement and must be finalized, together with the analysis system’s supported capabilities, before development begins.

## 2 Goals and Target Users

The primary users are basketball players who want to review their training and game performance. The presentation identifies adults who enjoy basketball as the target audience. Club members and organizers are also included; an analytics dashboard for coaches is subject to separate review.

The product aims to help users understand recent changes in their training performance, interpret game metrics clearly, and identify actionable improvements for their next training session. Scores should be accompanied by an explanation of their basis and any data limitations.

## 3 Requirement Status and Source Materials

| Category | Meaning |
| --- | --- |
| Source-supported | Directly supported by the HWPX descriptions or PNG screens. |
| Proposed | Additional requirements needed for implementation and usability; approval required. |
| Decision required | Items for which the original materials provide no standard, or for which screens and descriptions must be interpreted together. |

Source materials: the 41-slide BKDUNK Design presentation (.pptx), Component Features and Detailed Descriptions (.hwpx), and six PNG mockups showing Motion Analysis and Game Analysis for shooting, dribbling, and rebounding. The value 87 shown in the screens is a placeholder and must not be used as an actual score, target, or accuracy figure.

## 4 Product Scope and User Flow

### Core Scope Supported by the Source Materials

Users can switch between Motion Analysis and Game Analysis for each of the three skill areas. Motion Analysis displays the three to five most recent analysis results in a chart, together with feedback. The source describes shooting analysis that evaluates training videos using factors such as similarity to reference form and arm angles. Game Analysis provides game metrics based on footage of games in which the user participated.

### Skill Categories and Analysis Scope

| Skill Area | Skills Described in the HWPX | Product Scope Status |
| --- | --- | --- |
| Shooting | Layup, jump shot, three-point shot, hook shot, fadeaway | Skill categories are source-supported. Automatic recognition of each shot type requires a decision. |
| Dribbling | Basic dribble, crossover, behind-the-back dribble, spin move, hesitation | Assessment criteria and scoring formulas for each type require decisions. |
| Rebounding | Offensive and defensive rebounds, tipping, boxing out | Design skill categories separately from aggregated game metrics. |

### Proposed User Flow

Add a training or game video → Select an analysis type → Confirm the player to analyze → Request analysis → Check processing status → View results → Switch between shooting, dribbling, and rebounding and between analysis modes → Review metrics and feedback

The video submission method, player identification method, and supported video requirements are not yet defined. If an existing system provides analysis results, prioritize the results screens and integration with that system.

### Proposed Priorities

P0: all three skill areas and both analysis modes; recent-results charts and feedback; nine game metrics; empty and error states; metric definitions; and the data integration contract. P0 is the proposed initial release scope and will be finalized after analysis feasibility has been validated.

These P0 priorities apply within the analysis module. For the overall service, account, community, and Net features should be considered the shared foundation. The release order for basketball courts, NBA information, and video analysis will depend on external integrations and analysis readiness. Full analysis history, sharing and export, and a coach dashboard are proposed extensions. Payment and court booking are not included in the implementation scope solely on the basis of the mockups.

## 5 Motion Analysis Requirements

| ID | Requirement and Acceptance Criteria | Status |
| --- | --- | --- |
| MA01 | Display Motion Analysis results by skill area. Switching areas must show only the data and feedback for the selected area. | Source-supported / Acceptance criteria proposed |
| MA02 | Chart the three to five most recent completed analyses. A default of five is proposed; show the analysis date and chronological order. | Source-supported / Result-count policy proposed |
| MA03 | Provide an overall score and feedback. Shooting assessment includes factors such as reference-form match percentage and arm angles. | Source-supported |
| MA04 | The analysis owner must define assessment items, weights, and reference movements for dribbling and rebounding. Do not reuse the shooting criteria unchanged. | Decision required |
| MA05 | When only one or two results exist, display those results without drawing trend conclusions. When none exist, show a message stating that there is no analysis history. | Proposed |
| MA06 | Provide chart axes, units, dates, and values. The score and feedback for a selected record must refer to the same analysis result. | Proposed |

### Scoring and Feedback Policy

The overall score range, reference-form standard, form-match calculation, and the timing and units of joint-angle measurements require decisions. Example values from Game Analysis screens must not be repurposed as a motion scoring system. When the scoring formula version changes, indicate whether results remain comparable across versions.

The proposed feedback structure covers the observed movement, areas for improvement, and actions to try in the next training session. If an item cannot be assessed because of occlusion or poor video quality, mark it as unable to analyze instead of generating an arbitrary score.

### Interpreting the Original Screens

The Motion Analysis PNGs contain orange and gray bars without axes, legends, values, or labels. Use the recent-results chart described in the HWPX as the functional reference, but confirm with design whether the bars represent scores, progress, or feedback. Do not assume they are loading indicators.

## 6 Game Analysis Metric Requirements

Each skill area has three circular metric indicators. The metric names below come from the screens; formulas and display policies are proposals or open decisions that must be agreed before implementation.

| Skill Area | Metric | Formula or Open Decision |
| --- | --- | --- |
| Shooting | Field Goal Percentage | Proposed: field goals made ÷ field goals attempted × 100. Include two- and three-point shots; exclude free throws. |
| Shooting | Three-Point Percentage | Proposed: three-point shots made ÷ three-point shots attempted × 100. |
| Shooting | Free Throw Percentage | Proposed: free throws made ÷ free throws attempted × 100. |
| Dribbling | Turnover Rate | Decision required: determine whether this covers all turnovers or only turnovers while dribbling, and whether the denominator is possessions or plays. |
| Dribbling | Drive Success Rate | Proposed: successful drives ÷ attempted drives × 100. Define the event that counts as success and when a drive ends. |
| Dribbling | Assist Rate | Decision required: define the denominator for assist contribution, whether playing time is accounted for, and the criteria for crediting an assist. |
| Rebounding | Offensive Rebound Rate | Decision required: determine whether this is the player’s share of team rebounds or the share of available opportunities secured, and how on-court intervals apply. |
| Rebounding | Defensive Rebound Rate | Decision required: define which rebound opportunities enter the denominator and the scope of team and opponent statistics used. |
| Rebounding | Total Rebound Rate | Decision required: confirm whether offensive and defensive opportunities within the same scope are combined. Do not take a simple average of the two rates. |

### Proposed Display and Acceptance Policies

Display percentage metrics with the % symbol and, where possible, include counts for successes and attempts or rebounds secured and opportunities. Apply a consistent number of decimal places across all metrics. When the denominator is zero, display “Cannot calculate” rather than 0%, and distinguish this state from a calculated result of 0%.

The circular indicator must fill in proportion to the actual value. Treat the value 87 and the fill levels in the source materials as mockup content only. Because a lower turnover rate may be preferable, the interface must not present every metric as a green performance indicator that implies higher is better.

Show the selected game and aggregation period with the results. Use the same game, player, and aggregation scope consistently. Treat references to comprehensive game statistics as a future direction. The proposed initial scope is limited to the nine metrics above.

## 7 Screen and Data Requirements

### Screen Layout and Interaction

Place the skill name and the Motion Analysis / Game Analysis switch at the top, with the selected mode’s results below. Retain the mockups’ visual direction: a black background, orange accents, rounded containers, and circular indicators. A vertical arrangement of metrics is proposed for mobile screens.

The Motion Analysis button is filled in the PNGs for both modes, making the selected state ambiguous. Update the active tab to match the displayed content and distinguish it through text and accessibility state as well as color. Expose each metric’s name, value, unit, and status to screen readers.

### Proposed Analysis States

| State | What the User Sees |
| --- | --- |
| Queued or Processing | Show the current processing stage. Do not display placeholder scores before results are ready. |
| Completed | Show results linked to the video or game, the analysis timestamp, metrics, and feedback. |
| Partially Completed | Show only the items that can be calculated, and explain which items are missing and why. |
| Failed | Show a failure message and a retry option. Do not arbitrarily delete previously valid results. |
| No History | Show an empty-state message and, where supported, an entry point for adding a video. |

### Proposed Minimum Data Contract

Analysis results require a result ID, user and player identifiers, video and game identifiers, analysis type, skill area, analysis timestamp, status, and formula version. Motion Analysis must provide an overall score, detailed assessments, and feedback. Game Analysis must provide the metric code, value, unit, numerator, denominator, and aggregation scope. Report failures and missing data with distinct statuses and reasons.

### Proposed Quality and Operational Requirements

Restrict access so that authorized users can view only their own videos and results. The service operator must define video retention and deletion policies and how to handle other people appearing in game footage. File formats, size limits, recording conditions, and processing-time targets will be set after the analysis system has been validated.

Validate analysis accuracy against ground-truth data for each metric. Define supported recording conditions and failure conditions first. Do not promise accuracy or processing-time figures without actual validation.

## 8 Acceptance Testing and Open Decisions

### Proposed Release Acceptance Scenarios

| ID | Pass Criteria |
| --- | --- |
| QA01 | Across all six screens (shooting, dribbling, and rebounding × Motion Analysis and Game Analysis), the title, selected tab, and results agree. |
| QA02 | For 0, 1, 2, 3, 5, and 6 recent records, show the appropriate empty state or up to the five latest results in accordance with policy. |
| QA03 | For four made shots out of ten attempts, display 40% and a matching circular fill. A zero denominator displays “Cannot calculate.” |
| QA04 | Switching games, players, or skill areas does not mix in previous results. Feedback matches the selected record. |
| QA05 | Placeholder values never appear as actual results during processing, partial completion, failure, or retry. |
| QA06 | Unable to analyze, a score of 0, 0%, and no history are distinct states. Key values remain visible without clipping on small screens and when zoomed in. |

### Decisions Required Before Development

Product: confirm the default entry mode, default number of recent results, whether results are shown per game or aggregated over a period, initial release scope, and target users.

Analysis: confirm the supported assessments for all three skills, player identification method, scoring criteria and weights, denominators and event definitions for each game metric, recording conditions, and accuracy validation criteria.

Design: confirm the meaning and axes of the motion chart, active-tab treatment, value, unit, and color policies for circular indicators, mobile layout, and exception states.

Engineering and operations: confirm video input methods, analysis APIs and state transitions, retention and deletion policies, permissions, processing times, and incident response criteria. Specific owners and schedules will be agreed separately.

### Proposed Product Success Metrics

Measure analysis completion rate as the share of valid analysis requests that are completed, and results view rate as the share of completed results viewed by users. Measure repeat usage as the share of users who request another analysis within a defined period after their first analysis. Set measurement windows and targets after initial operational data is available.

### Requirements Traceability

HWPX descriptions of recent results, charts, and feedback → MA02 and MA03. HWPX description of training-video assessment → MA03 and MA04. Three Game Analysis PNGs → nine game metrics. Three Motion Analysis PNGs → shared mode switching and motion-chart design decisions. The final Game Analysis description in the original text is incomplete and must not be used to establish the scope of additional metrics.

## 9 Overall Service Structure and User Accounts

### Service Structure and Branding Decisions

The presentation’s main menus are Net, NBA, Posts, and Basketball Courts. The proposed structure adds an Analysis entry point and provides access to My Nets and analysis history from My Page. The presentation shows an orange-and-white desktop website, while the analysis PNGs show cards on a black background. The overall design system and in-app navigation therefore require a unified design.

The external community screens and logos on slides 3–7 are references only. Do not automatically convert those services’ features into CourtView requirements. The description on slide 11 about retaining the shared screen structure is reflected as a requirement to preserve the header and navigation when content changes; it does not establish a specific technology or performance improvement.

| ID | Source-Supported Feature | Proposed Acceptance Criteria and Open Decisions |
| --- | --- | --- |
| AC01 | Email/password sign-in and account recovery<br>Slides 21–22 | Return to the requested screen after successful sign-in. Provide failure messages and define the account recovery method. |
| AC02 | Agreement to terms during sign-up<br>Slide 23 | Distinguish required and optional consent. Further define sign-up fields and verification steps. |
| AC03 | Profile editing and password changes<br>Slide 38 | Allow changes only by the account owner. Handle session expiration and authentication failures. |
| AC04 | My posts, comments, and liked posts<br>Slide 38 | Show only the user’s actual activity and provide empty-list messages. |
| AC05 | Terms of Service and Privacy Policy<br>Slides 13–15 | Provide menu access and display the latest approved documents. Do not treat policy text in the mockups as finalized operational policy. |

### Proposed Permission Model

Guests can browse public posts, Nets, game information, and basketball courts. Members can create posts and comments, like posts, access My Nets, and view their own analysis results. Net organizers can use only the management functions for which they are authorized. Service administrators are proposed to have permission to handle reports and manage content. Net visibility rules and membership approval methods require decisions.

### Primary User Flows

Community: search posts → View the list → Open a post → Sign in → Comment or like. Nets: browse by region and skill level → Select a Net → Complete the joining process → Access My Nets. Detailed membership application and approval screens require additional design. Basketball courts: allow location access or select a region → View the map and list → View a court.

## 10 Community and Net Features

| ID | Source-Supported Requirement | Proposed Acceptance Criteria and Open Policies |
| --- | --- | --- |
| CM01 | Search across all content, posts, and Nets; filter posts by category<br>Slides 17, 29–30 | Apply search terms and categories to the list, and distinguish no results from loading. |
| CM02 | Post lists, post details, comments, likes, and post creation and editing<br>Slides 29–34 | Verify posting permissions and required title and body fields; allow authors to edit their own posts. Policies for deletion, reporting, and attachment limits are still needed. |
| CM03 | Image attachments and popular posts<br>Slides 17, 34 | Explain supported formats and size limits. Define the measurement period and criteria for popular posts. |
| NT01 | Region and skill-level filters; popular and new Nets<br>Slides 18, 26 | Results must match combined filters. Criteria for popular and new Nets require decisions. |
| NT02 | My Nets list and organizer activity count<br>Slide 39 | Show name, introduction, region, schedule, member count, join date, skill level, and a direct link. |
| NT03 | Net creation flow<br>Slides 40–41 | Basic information → Activity information → Detailed settings → Complete. Fields for later steps require additional design. |
| NT04 | Net rankings and game schedules<br>Slides 17, 19 | Distinguish rankings by activity score from rankings by member count. Define the scoring formula, schedule-creation permissions, and links to detail views. |

### Net Creation Inputs

The mockup marks the Net name and short introduction as required, with limits of 20 and 50 characters respectively. Provide category, cover image, and profile image inputs. The recommended cover image size shown is 1200 × 400 px. Character-counting rules, duplicate-name policy, file limits, draft saving, and handling of users leaving the flow before completion require further decisions.

### Future Matchmaking Scope

Slide 8 describes the difficulty of finding pickup games and guest-player opportunities and identifies arranging games between Nets as a future feature. This document retains that future scope. Do not commit to automated matchmaking or booking before defining policies for recruitment, applications, acceptance, cancellation, no-shows, notifications, and scheduling conflicts.

## 11 Basketball Courts NBA Information and Integrated Acceptance Testing

| ID | Source-Supported Feature | Proposed Acceptance Criteria and Integration Requirements |
| --- | --- | --- |
| CT01 | Find nearby basketball courts using my location<br>Slides 35–36 | Provide a map and a list of nearby courts. A selection must refer to the same location in both views. |
| CT02 | Court name, address, rating, and indoor indicator<br>Slide 36 | Hide unavailable fields or label them as unavailable. Identify the source of ratings. |
| NB01 | NBA game schedules with upcoming and recent game tabs<br>Slides 20, 27–28 | Show dates, teams, and times. Define the time zone, refresh interval, and external provider. |
| NB02 | NBA Eastern and Western Conference standings<br>Slides 17, 37 | Show rank, team, wins, and losses for a consistent season. Notify users when updates fail. |

### Failure States and Operational Data

If location permission is denied, the proposed fallback is to let users explore by searching for a region or moving the map. If map or game-data requests fail, provide a retry option and show the last update time. Confirm the map provider and the scope, cost, and terms of use for venue information and NBA data before development begins. All team rankings, dates, member counts, and scores shown in the screens are sample data.

Proposed additional data models cover members, Nets, memberships and roles, posts, comments, likes, game schedules, and basketball courts. Store the reference period for activity aggregates and rankings. Consider sharing analysis results within a Net or post only after defining separate consent requirements and visibility settings.

### Proposed Integrated Acceptance Criteria

QA07: When guests attempt to create content, redirect them to sign-in and return them to their original task after signing in. QA08: Prevent users from editing other users’ posts, changing their accounts, or viewing their analysis results. QA09: Preserve search and filter criteria when searching, filtering, or changing pages, and display an empty state when there are no results.

QA10: Validate Net name and introduction lengths and required fields, and prevent duplicate creation requests. QA11: Provide usable fallback states when location permission is denied or map or NBA data requests fail. QA12: Ensure navigation and core features are connected consistently across web and app screens.

### Release Decisions and Success Metrics

The proposed sequence is: approve branding and platform scope → Approve core screens and operational policies → Validate analysis, map, and NBA integrations → Develop features and complete integrated acceptance testing → Conduct a limited release. Estimate timelines and costs after reviewing these dependencies and the scope of any outsourcing agreements.

Proposed metrics are sign-up completion and post/comment participation rates for the community, browse-to-join conversion for Nets, and search success rate for basketball courts. The product owner will finalize event definitions, aggregation periods, and targets for these metrics alongside the analysis metrics.
