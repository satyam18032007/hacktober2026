# CampusLens

## Point. Understand. Fix.

**CampusLens** is a camera-first AI campus operations agent that turns a real-world campus problem into a structured, trackable maintenance report.

A student does not need to know which office to contact, how to describe the issue, or where the responsibility belongs. They can simply **show the problem to the camera**. CampusLens helps understand the visual evidence, organize the report, surface possible duplicates, and move the issue into an accountable resolution workflow.

> **See a problem. Show the agent. Change the campus.**

---

## 🔎 At a Glance

|                        | CampusLens                                                                |
| ---------------------- | ------------------------------------------------------------------------- |
| **Problem**            | Campus issues are visible, but reporting and following them is fragmented |
| **Core interaction**   | Point a camera at the problem                                             |
| **AI role**            | Understand visual evidence and structure the next actions                 |
| **Student side**       | Capture, report, and track issues                                         |
| **Admin side**         | Review, prioritize, manage, and verify issues                             |
| **Key differentiator** | End-to-end issue lifecycle, including before/after verification           |
| **Primary AI**         | Gemma 4                                                                   |
| **Prototype**          | Web-based interactive demo                                                |

---

# 🚨 The Problem

Colleges and campuses continuously deal with small physical problems:

* broken chairs, desks, doors, or equipment
* overflowing or damaged waste bins
* water leakage
* blocked ramps and accessibility obstacles
* damaged signs
* maintenance and infrastructure issues
* visibly unsafe-looking installations

The difficult part is often not **seeing** the problem.

The difficult part is getting from:

**“A student noticed something.”**

to:

**“The right person knows about it, acts on it, and the student can see what happened next.”**

Traditional reporting usually depends on manual descriptions, the student knowing the correct department, separate complaint systems, and follow-up messages.

That creates friction, duplicate complaints, poor visibility, and weak accountability.

---

# 💡 The CampusLens Idea

CampusLens treats the **camera as the interface to campus operations**.

Instead of making students translate a visual problem into a long text complaint, the system starts from the evidence itself.

### The intended flow

```text
Student sees a problem
        ↓
Captures / uploads a photo
        ↓
AI understands the visual evidence
        ↓
Issue + context are structured
        ↓
Possible duplicate is checked
        ↓
A maintenance report is created
        ↓
Building admin reviews and manages it
        ↓
Repair/update evidence is added
        ↓
Issue is reviewed for resolution
```

The objective is not to create another chatbot that only **describes** an image.

The objective is to create an agent that helps move a physical problem through a real operational workflow.

---

# 🤖 Why This Is an AI Agent, Not Just an AI Chatbot

A chatbot can answer:

> “What is wrong in this image?”

CampusLens is designed to go further:

```text
Observe
  ↓
Understand
  ↓
Decide what information is needed
  ↓
Check existing context
  ↓
Create / update an operational record
  ↓
Track the result
  ↓
Support verification
```

The agent concept is based on **model-guided actions and tools**, not only natural-language generation.

Gemma 4 supports multimodal image understanding and native function-calling capabilities, which makes it suitable for a workflow in which the model can request structured tool actions and the application executes those actions with validation.

> **Important:** the model does not directly execute arbitrary code. The application validates allowed actions and performs the actual tool execution.

---

# 📸 Student Dashboard

The student dashboard is designed around one simple goal:

### Report a campus problem with as little friction as possible.

Students can use the interface to:

* capture or upload an image
* describe or confirm the issue when needed
* view the AI-generated issue summary
* provide or review location information
* see possible duplicate reports
* submit the issue
* track its status and progress

The intended experience is:

> **See → Show → Submit → Track**

---

# 🏢 Building Admin Dashboard

The second interface is built for the people responsible for managing issues inside a building, block, or campus area.

Admins can work with reports through:

* building / area filtering
* issue review
* priority / severity information
* department or responsibility information
* status updates
* repair / resolution evidence
* issue lifecycle tracking

This creates the missing operational bridge between a student report and the people expected to act on it.

---

# 🔄 The Full Issue Lifecycle

CampusLens is designed around an explicit issue lifecycle.

### 1. Observe

A student notices a physical problem.

### 2. Capture

The student takes a photo or uploads an image.

### 3. Understand

AI analyzes the visual evidence and structures the issue.

### 4. Locate

Location can be associated using available context such as GPS, QR codes, signage, or a selected campus location.

### 5. Deduplicate

The system checks whether a similar issue may already exist.

### 6. Report

A structured maintenance record is created with the available evidence and context.

### 7. Manage

The relevant admin can review the report, update its state, and manage the resolution process.

### 8. Verify

A later “after” image can be reviewed against the original evidence to support resolution verification.

### 9. Close

The issue can move to a resolved / closed state after the required review.

---

# ⭐ What Makes the Idea Different

## 1. Camera-first, not form-first

Most issue-reporting systems begin with a form.

CampusLens begins with the physical world.

## 2. Evidence before explanation

The photograph provides the starting evidence, reducing the amount of manual description required from the student.

## 3. Agentic workflow

The AI is intended to help determine what happens next in the process, instead of only returning an answer.

## 4. Duplicate-aware reporting

The system can surface possible existing reports before creating unnecessary duplicates.

## 5. Before/after verification

The workflow does not end at “ticket created”. It can continue to “was the problem actually addressed?”

## 6. Two-sided product

The product is designed for both sides of the operation:

**Student → Report**

**Admin → Resolve**

---

# 🧠 Why Gemma 4?

Gemma 4 is a natural fit for CampusLens because the project starts from multimodal evidence rather than text alone.

Gemma 4 supports capabilities relevant to this workflow, including image understanding, OCR, visual localization, reasoning, and function calling.

Google also documents hosted Gemma access through the Gemini API and image + function-calling workflows for Gemma 4.

This aligns with the core CampusLens requirement:

> **Look at a physical problem → understand the evidence → structure the issue → trigger controlled application actions.**

Smaller Gemma variants also create a future path toward more privacy-friendly or edge-oriented deployments.

---

# 🏗️ Conceptual Architecture

```text
┌──────────────────────────────┐
│       Student Dashboard      │
│   Camera / Upload / Report   │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        Application Layer      │
│ Validation • Workflow • Auth  │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│            Gemma 4           │
│ Vision • OCR • Reasoning     │
│ Structured outputs / tools   │
└──────────────┬───────────────┘
               │
        ┌──────┼─────────┐
        │      │         │
        ▼      ▼         ▼
   Location  Duplicate  Ticket /
   Context   Check      Issue Action
        │      │         │
        └──────┼─────────┘
               ▼
┌──────────────────────────────┐
│        Issue / Data Layer     │
│ Reports • Status • Evidence   │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Building Admin Panel     │
│ Review • Assign • Update      │
│ Resolve • Verify              │
└──────────────────────────────┘
```

The architecture is intentionally modular so that the AI layer can be connected to different tools, storage systems, or institutional workflows over time.

---

# 🧪 Example Scenario

Imagine a wheelchair ramp is blocked by two bicycles.

### Student action

The student points the camera at the ramp and selects:

**“Report this.”**

### AI interpretation

A possible structured result could look like:

```json
{
  "issue_type": "accessibility_obstruction",
  "description": "The wheelchair ramp appears to be obstructed by bicycles.",
  "severity": "medium",
  "suggested_department": "Facilities",
  "recommended_action": "Remove the obstruction and keep the ramp clear"
}
```

### Operational flow

```text
Photo captured
     ↓
Issue understood
     ↓
Existing reports checked
     ↓
Report created
     ↓
Admin sees the issue
     ↓
Admin updates status
     ↓
After-repair evidence added
     ↓
Resolution reviewed
```

This is the core CampusLens story in one minute.

---

# 🔎 Duplicate Detection

A campus can receive several reports for the same physical issue.

CampusLens is designed to surface possible duplicates using the available issue information and similarity signals.

For example:

> **Possible duplicate:** A similar blocked-ramp issue may already exist in this building.

The goal is not to automatically reject reports. The goal is to give the system and the admin better context before creating another record.

---

# 📍 Location Strategy

A visual problem is useful only when the system can connect it to a place.

CampusLens can combine multiple location signals:

### GPS

Browser geolocation can provide approximate coordinates when permission is available.

### QR codes

QR codes placed around buildings can provide a deterministic building / zone identifier.

### Visible signage

Text visible in the photograph can help identify a building or area.

### Landmarks / manual selection

The interface can fall back to recognizable landmarks or a user-selected location.

Using multiple signals makes the system more practical than relying on a single source of location data.

---

# 🔐 Privacy & Safety

CampusLens is intended for real-world campus environments, so privacy and cautious AI behavior matter.

### Privacy principles

* Minimize unnecessary personal data.
* Avoid retaining data that is not needed for issue handling.
* Consider face and license-plate redaction before storage.
* Prefer on-device processing for privacy-sensitive steps when practical.
* Keep access to reports role-appropriate.

### Safety principles

The AI should treat severity and safety classifications as **advisory**.

A photograph alone should not be used to claim that an electrical, structural, fire, medical, or other professional hazard has been definitively confirmed.

For higher-risk categories, the AI should help surface evidence and route the issue while leaving final responsibility to qualified humans.

---

# 🎬 Recommended Hackathon Demo

The strongest demo is one complete end-to-end story rather than a long list of disconnected features.

### Scene

Place a blocked ramp, leaking bottle, damaged chair, or another visible campus issue in front of the camera.

### Demo

1. **Student opens CampusLens**
2. **Captures the problem**
3. **AI explains what it sees**
4. **Location / building context appears**
5. **Possible duplicates are checked**
6. **The report is created**
7. **Admin dashboard shows the new issue**
8. **Admin updates the issue status**
9. **A second “after” photo is reviewed**
10. **The issue moves toward resolution**

The message to the judge is simple:

> **One camera interaction can start a complete accountability loop.**

---

# 🌐 Live Prototype

**CampusLens Demo:**

https://campuslens.godgod12345blessing.chatgpt.site/

The prototype includes two primary views:

* **Student:** report and track campus issues
* **Building Admin:** review, filter, manage, and verify reported issues

For the demo environment, some roles, integrations, and AI behaviors are represented as prototype flows rather than a production campus deployment.

---

# 🧩 Technology Direction

The prototype is designed around a modern web application with a multimodal AI layer and an issue-management workflow.

Core technology areas include:

* **Frontend:** web-based responsive interface with camera / image upload
* **AI:** Gemma 4 multimodal understanding
* **Location:** browser geolocation, QR context, and visual signage
* **Data:** structured issue records and status history
* **Operations:** admin workflow for assignment and resolution
* **Verification:** before/after evidence review

The implementation can evolve independently in each layer without changing the core product idea.

---

# 📊 From Complaint System to Operations System

The deeper vision of CampusLens is not simply “better complaint filing”.

A campus can eventually use the accumulated issue data to understand:

* recurring problems
* high-maintenance buildings
* common issue categories
* average resolution time
* repeated problem locations
* accessibility-related issues
* maintenance workload
* preventive-maintenance opportunities

That creates a feedback loop:

```text
Physical problems
       ↓
AI-assisted reporting
       ↓
Structured issue data
       ↓
Operational decisions
       ↓
Repairs
       ↓
Resolution evidence
       ↓
Historical campus intelligence
```

The long-term opportunity is to move from **reactive complaint handling** toward **data-informed campus operations**.

---

# 🔮 Future Scope

### Phase 1 — Reporting

* camera-first capture
* AI issue understanding
* structured reports
* duplicate suggestions
* student tracking

### Phase 2 — Operations

* automatic department routing
* institutional ticket integrations
* notifications
* QR-based location infrastructure
* richer analytics

### Phase 3 — Verification

* stronger before/after comparison
* resolution confidence
* human-in-the-loop verification
* audit history

### Phase 4 — Edge / Private AI

* smaller local Gemma deployment
* offline-first workflows
* on-device redaction
* reduced dependence on cloud inference

---

# 🏆 Why CampusLens Fits a Hackathon

CampusLens brings together three layers in one visible demonstration:

### AI

Multimodal image understanding and agent-style tool use.

### Product

A simple student experience backed by an operational admin workflow.

### Real-world impact

A direct connection between AI output and physical campus maintenance.

The project is therefore easy to demonstrate visually while still having meaningful technical depth behind the interface.

---

# 📌 Current Prototype Limitations

This repository represents a hackathon prototype, not a production campus-management platform.

Some functionality may be simulated, manually assisted, or dependent on external API configuration.

In particular:

* AI analysis requires the configured AI service.
* Some classifications may be assisted by user-provided context in the prototype.
* Student and admin roles are presented as prototype views.
* Repair verification is intended as a workflow concept and may require human review.
* Continuous video understanding is deliberately not the MVP focus; image-based capture is simpler and more reliable for a hackathon demonstration.

These limitations are intentional boundaries for the prototype rather than claims of production readiness.

---

# 🧠 Design Principles

### Camera First

Start from what the student can see.

### Evidence First

Keep AI conclusions tied to available visual and contextual evidence.

### Action Over Answers

The useful output is a report, action, assignment, update, or verification step.

### Human Oversight

AI recommendations should remain reviewable, especially for safety and severity.

### Privacy by Design

Collect and retain only what the operational workflow requires.

---

# 🎤 The Pitch

> **Campus problems are everywhere, but reporting them is still mostly manual. CampusLens turns a phone camera into an AI-powered campus operations agent. Point it at a problem, and the system can understand the evidence, identify useful context, surface possible duplicates, create a structured report, and support verification after the issue is addressed.**
>
> **One photo becomes accountable action.**

---

# 👥 Project

## CampusLens

**Tagline:** Point. Understand. Fix.

A hackathon prototype exploring multimodal AI, autonomous workflows, developer tooling, privacy-aware computer vision, and practical campus operations.

---

# 📚 References

* [Google AI for Developers — Gemma 4 model card](https://ai.google.dev/gemma/docs/core/model_card_4)
* [Google AI for Developers — Run Gemma with the Gemini API](https://ai.google.dev/gemma/docs/core/gemma_on_gemini_api)
* [Google AI for Developers — Function calling with Gemma 4](https://ai.google.dev/gemma/docs/capabilities/text/function-calling-gemma4)

---

# 📜 License

Add the final project license here before production or open-source distribution.
