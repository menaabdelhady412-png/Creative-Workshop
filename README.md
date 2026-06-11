# Creative Workshop & Studio Management System

**Course:** Database Systems  
**Project ID:** 313  
**TA:** Dina Amr  
**Program:** Special Zayed, Cairo University  

---

## Overview
This repository contains the full Phase 3 implementation of the Creative Workshop & Studio Management System. The system provides an integrated administrative solution for managing resident art studios, tracking material assets, scheduling workshops, and maintaining member metrics. It bridges a native desktop administrative panel with a synchronized database backend and a modern visual client dashboard.

---

## Core Features
* **Member Management:** Creation, updates, and tracking of studio member attributes, including unique identification, multi-channel contact logs, and explicit subscription fee processing tracking.
* **Workshop Scheduling & Registration:** Structured tracking for scheduling historical and active workshops, managing strict seat capacity allocations, and linking event registrations directly to existing accounts.
* **Operational Resource Inventory:** Real-time asset logging for high-end or standard studio tooling alongside consumption parameters for raw material stock levels.
* **Hybrid Application Interface:** Combines a performance-oriented C++ Win32 administrative management client with an automated HTML/CSS/JS dashboard generator for clear data representation.

---

## System Architecture & Constraints
The system architecture follows strict relational design constraints and enterprise structural guidelines:
* **Studio Constraint:** Workshops must map explicitly to a physical studio location. Studios can host multiple sequential workshops over time.
* **Instruction Boundary:** Every planned workshop must be assigned to exactly one resident artist who leads the training lifecycle.
* **Participation Vectors:** Provides many-to-many relationship tracking allowing a member to register for multiple workshops while tracing full class attendance sheets.
* **Resource Allocations:** Maps structural tool loans to individual members and tallies direct material unit consumption quantities back to host workshops.

---

## Technical Stack
* **Database Engine:** Microsoft SQL Server (Transact-SQL)
* **Administrative Desktop Client:** Native C++ (Win32 API) utilizing structural ODBC database handles (`odbc32.lib`, `comctl32.lib`)
* **Presentation Layer:** Vanilla HTML5, CSS3 (DM Sans/DM Mono Typography variables), and JavaScript data arrays

---

## Database Schema & Definitions
The persistence layer is mapped out across explicit structural entities:
* `MEMBER`: Tracks `MEMBERID`, `MEMBERNAME`, `MEMBEREMAIL`, `PHONE`, `SUBSCRIPTIONSTATUS`, and `SUBSCRIPTIONFEEPAID`.
* `STUDIO`: Tracks physical room properties including `STUDIOID`, `STUDIONAME`, `MAXOCCUPANCY`, and `ROOMNUMBER`.
* `RESIDENTARTIST`: Stores profile information for core instructional staff.
* `WORKSHOP`: Joins scheduling parameters including maximum attendee cutoffs with target artist and studio foreign keys.
* `TOOL` / `RAWMATERIAL`: Monitors inventory counts, qualitative states (`Excellent`, `Good`), and material volume metrics.
* `REGISTERS` / `BORROWS` / `CONSUMES`: Associative schema tables processing network transactions across actors and assets.

---

## Project Structure
```text
├── ArtStudio.sql       # Database schema creation, indexes, and constraint scripts
├── ArtsData.sql        # Standard testing dataset populate statements
├── main.cpp            # Win32 desktop application client source code
├── DBGui.html          # Dynamic responsive web visualization interface
├── ConceptualData.cdm  # Conceptual data model file (PowerDesigner)
├── PhysicalData.pdm    # Physical database layout scheme (PowerDesigner)
└── DBCover3.pdf        # Formal technical project design documentation
Compilation and Execution
1. Database Setup
Open your Microsoft SQL Server Management Studio instance.

Execute ArtStudio.sql to initialize the database structures, primary index pathways, and cascading integrity foreign constraints.

Execute ArtsData.sql to populate seed values into the working tables.

2. Desktop Client Compilation
On Windows (Visual Studio Command Prompt / MinGW Developer Environments):
Compile the native application while binding the mandatory ODBC and Windows common control library linkages:

Bash
g++ -O2 main.cpp -luser32 -lgdi32 -lcomctl32 -lodbc32 -o ArtStudioManager.exe
3. Execution
Run ArtStudioManager.exe to manage member logs, remove entries, or issue queries.

Use the "Export HTML" routine inside the interface to build updated localized web records. Open DBGui.html in any modern web browser to audit high-level analytics dashboard summaries.

Authors (Group 1 / G12)
Mena Sultan (20245068) - Lab Group: G1

Ahmed Hasanien (20246011) - Lab Group: G12

Esmail Khetam (20246019) - Lab Group: G12

Abdelrahman Zayed (20246066) - Lab Group: All (G12)

Mohamed Elnaggar (20247006) - Lab Group: G12

Sayed Ahmed (20257036) - Lab Group: All (G12)
