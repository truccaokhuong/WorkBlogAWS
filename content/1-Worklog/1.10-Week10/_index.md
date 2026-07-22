---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 10 Objectives:

* Implement Booking module screens: Booking Page and My Bookings.
* Build booking detail view with status timeline.
* Develop cancel booking functionality with confirmation flow.
* Implement booking status state machine management.
* Integrate real-time booking updates via WebSocket.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - **Booking Page**: <br>&emsp; + Design date/time picker with available slots display <br>&emsp; + Build guest count selector and special requests input <br>&emsp; + Implement real-time availability checking to prevent double bookings <br>&emsp; + Add price summary and confirmation step before submission <br>&emsp; + Connect to POST /bookings API endpoint with form validation | 19/06/2026 | 19/06/2026 | React DatePicker, Zod Validation |
| 3 | - **My Bookings Page**: <br>&emsp; + Create booking list with status tabs: All, Pending, Confirmed, Cancelled, Completed <br>&emsp; + Implement sorting by date, status, and place name <br>&emsp; + Build booking card component with place image, date, status badge, and action buttons <br>&emsp; + Add empty state illustrations for each tab <br>&emsp; + Connect to GET /bookings?user_id=me API endpoint with pagination | 20/06/2026 | 20/06/2026 | React Query Pagination, Tailwind Tabs |
| 4 | - **Booking Detail Page**: <br>&emsp; + Design detail layout with place info, booking info, and status timeline <br>&emsp; + Build status stepper component: Pending → Confirmed → Completed (or Cancelled) <br>&emsp; + Add booking modification options based on current status <br>&emsp; + Implement QR code generation for booking confirmation <br>&emsp; + Connect to GET /bookings/:id API endpoint | 21/06/2026 | 21/06/2026 | QR Code Library, Timeline UI |
| 5 | - **Cancel Booking Flow**: <br>&emsp; + Build confirmation dialog with cancellation reason options <br>&emsp; + Implement business logic: only Pending/Confirmed bookings can be cancelled <br>&emsp; + Add refund policy display for confirmed booking cancellations <br>&emsp; + Implement optimistic UI update with rollback on failure <br>&emsp; + Connect to PATCH /bookings/:id/cancel API endpoint | 22/06/2026 | 22/06/2026 | React Modal, Optimistic Updates |
| 6 | - **Booking Status Lifecycle**: <br>&emsp; + Implement state machine: Pending → Confirmed (by business owner), Pending → Cancelled (by user), Confirmed → Completed (after booking date), Confirmed → Cancelled (by user) <br>&emsp; + Add Socket.io listener for real-time status changes <br>&emsp; + Build toast notifications for status updates <br>&emsp; + Write automated tests for all status transitions <br> - End-to-end testing of full booking flow | 23/06/2026 | 23/06/2026 | XState (state machine), Socket.io, React Hot Toast |


### Week 10 Achievements:

* ✅ **Booking Page** fully functional with date/time picker, real-time availability checking, guest selection, and multi-step booking flow.
* ✅ **My Bookings** page completed with tab-based filtering (5 status tabs), infinite scroll pagination, and responsive card layout.
* ✅ **Booking Detail** page delivering comprehensive booking information, visual status timeline stepper, and QR code for easy check-in.
* ✅ **Cancel Booking** flow implemented with reason collection, business rule validation (only Pending/Confirmed status), and optimistic UI updates.
* ✅ **Status Lifecycle State Machine** correctly handling all 4 transitions with real-time WebSocket updates and toast notifications.
* ✅ Wrote 40+ unit tests for booking logic and 15 integration tests for the full booking flow from creation to completion.
* ✅ All Booking screens deployed to staging and passing QA review with zero critical bugs.
