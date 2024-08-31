# access_db_from_scr
This is a portfolio project for the Backend Engineering course where I built a database from scratch.

Here’s a detailed plan for your database schema design based on the entities you provided. This design outlines the tables, their fields, primary keys, foreign keys, and relationships between them.

### Database Schema Overview

1. **Users**
   - **id**: `INT` (PK)
   - **profile_id**: `INT` (FK to Profiles)
   - **billing_account**: `VARCHAR(255)`
   - **signup_type**: `VARCHAR(50)`
   - **signup_subdomain**: `VARCHAR(255)`
   - **profile_autofill**: `BOOLEAN`
   - **created_at**: `DATETIME`
   - **linkedin_id**: `VARCHAR(255)`
   - **agreements**: `TEXT`
   - **background_check**: `BOOLEAN`
   - **password_updated_at**: `DATETIME`
   - **last_login_at**: `DATETIME`
   - **login_attempts**: `INT`
   - **login_attempt_at**: `DATETIME`
   - **reset_password_token_hash**: `VARCHAR(255)`
   - **expert_state**: `VARCHAR(50)`
   - **compliance_completed_at**: `DATETIME`
   - **available_self_service**: `BOOLEAN`
   - **referrer**: `VARCHAR(255)` (FK to Users)
   - **sourcer**: `VARCHAR(255)`
   - **referrer_request**: `VARCHAR(255)` (FK to ExpertRequests)
   - **campaign**: `VARCHAR(255)`
   - **landing_url**: `VARCHAR(255)`
   - **deleted**: `BOOLEAN`

2. **Profiles**
   - **id**: `INT` (PK)
   - **created_by**: `VARCHAR(255)` (FK to Users)
   - **updated_by**: `VARCHAR(255)` (FK to Users)
   - **expert_request**: `VARCHAR(255)` (FK to ExpertRequests)
   - **url_endpoint**: `VARCHAR(255)`
   - **created_at**: `DATETIME`
   - **first_name**: `VARCHAR(255)`
   - **last_name**: `VARCHAR(255)`
   - **linkedin_url**: `VARCHAR(255)`
   - **linkedin_username**: `VARCHAR(255)`
   - **picture_url**: `VARCHAR(255)`
   - **picture_source_url**: `VARCHAR(255)`
   - **cover_image_url**: `VARCHAR(255)`
   - **title**: `VARCHAR(255)`
   - **summary**: `TEXT`
   - **city**: `VARCHAR(255)`
   - **country**: `VARCHAR(255)`
   - **country_iso2_code**: `VARCHAR(2)`
   - **languages**: `TEXT`
   - **keywords**: `TEXT`
   - **questions**: `TEXT`
   - **conflicted**: `BOOLEAN`
   - **skype**: `VARCHAR(255)`
   - **timezone**: `VARCHAR(255)`
   - **cv_url**: `VARCHAR(255)`
   - **cv_text_convert_attempts**: `INT`
   - **tags**: `TEXT`
   - **tier**: `INT`
   - **hourly_rate**: `DECIMAL(10,2)`
   - **hide_profile**: `BOOLEAN`
   - **available_for_long_term**: `BOOLEAN`
   - **available_pro_bono**: `BOOLEAN`
   - **available_marketplace**: `BOOLEAN`
   - **additional_information**: `TEXT`
   - **deleted**: `BOOLEAN`

3. **Conferences**
   - **id**: `INT` (PK)
   - **created_at**: `DATETIME`
   - **starts_at**: `DATETIME`
   - **finalized_at**: `DATETIME`
   - **name**: `VARCHAR(255)`
   - **state**: `VARCHAR(50)`
   - **expected_duration**: `INT`
   - **duration**: `INT`
   - **enable_recording**: `BOOLEAN`
   - **recording_url**: `VARCHAR(255)`
   - **recording_file_size**: `INT`
   - **recording_state**: `VARCHAR(50)`
   - **recording_state_updated_at**: `DATETIME`
   - **carrier**: `VARCHAR(100)`
   - **carrier_account_id**: `VARCHAR(100)`
   - **carrier_conference_id**: `VARCHAR(100)`
   - **password**: `VARCHAR(255)`
   - **country_codes**: `VARCHAR(255)`

4. **Consultations**
   - **id**: `INT` (PK)
   - **billing_account**: `VARCHAR(255)`
   - **transaction_group**: `VARCHAR(255)` (FK to TransactionGroups)
   - **requester**: `VARCHAR(255)` (FK to Users)
   - **expert**: `VARCHAR(255)` (FK to Users or Profiles)
   - **creator**: `VARCHAR(255)` (FK to Users)
   - **canceled_by**: `VARCHAR(255)` (FK to Users)
   - **transcription_order**: `VARCHAR(255)` (FK to TranscriptionOrders)
   - **request**: `VARCHAR(255)` (FK to ExpertRequests)
   - **team**: `VARCHAR(255)`
   - **transcription_id**: `VARCHAR(255)`
   - **tracking_code**: `VARCHAR(50)`
   - **created_at**: `DATETIME`
   - **starts_at**: `DATETIME`
   - **started_at**: `DATETIME`
   - **ended_at**: `DATETIME`
   - **canceled_at**: `DATETIME`
   - **proposed_times**: `DATETIME`
   - **rejected_times**: `DATETIME`
   - **expected_duration**: `INT`
   - **billing_duration**: `INT`
   - **initial_expected_duration**: `INT`
   - **credit_rate**: `DECIMAL(10,2)`
   - **credit_penalty_amount**: `DECIMAL(10,2)`
   - **credit_amount**: `DECIMAL(10,2)`
   - **bill_rate**: `DECIMAL(10,2)`
   - **expert_cost**: `DECIMAL(10,2)`
   - **incomplete_reason**: `TEXT`
   - **description**: `TEXT`
   - **summary**: `TEXT`
   - **expert_pin**: `VARCHAR(255)`
   - **requester_pin**: `VARCHAR(255)`
   - **expert_identifier**: `VARCHAR(255)`
   - **requester_identifier**: `VARCHAR(255)`
   - **reschedule_count**: `INT`
   - **cancel_reason**: `TEXT`
   - **consultation_type**: `VARCHAR(50)`
   - **disclosure**: `VARCHAR(50)`
   - **requester_event_id**: `VARCHAR(255)`
   - **expert_event_id**: `VARCHAR(255)`
   - **requester_name**: `VARCHAR(255)`
   - **expert_name**: `VARCHAR(255)`
   - **external**: `BOOLEAN`
   - **original_recording_url**: `VARCHAR(255)`
   - **recording_url**: `VARCHAR(255)`
   - **recording_duration**: `INT`
   - **recording_expert_visible**: `BOOLEAN`
   - **last_confirmation_reminder_sent_at**: `DATETIME`
   - **last_consultation_reminder_sent_at**: `DATETIME`
   - **confirmation_reminder_count**: `INT`
   - **deleted**: `BOOLEAN`
   - **receipt_sent_at**: `DATETIME`
   - **engagement_type**: `VARCHAR(50)`
   - **conference**: `VARCHAR(255)` (FK to Conferences)

5. **Expert Requests**
   - **id**: `INT` (PK)
   - **billing_account**: `VARCHAR(255)`
   - **person**: `VARCHAR(255)` (FK to Users)
   - **project**: `VARCHAR(255)` (FK to Projects)
   - **deleted**: `BOOLEAN`
   - **created_at**: `DATETIME`
   - **state**: `VARCHAR(50)`
   - **er_type**: `VARCHAR(50)`
   - **title**: `VARCHAR(255)`
   - **description**: `TEXT`
   - **focus_areas**: `TEXT`
   - **disclosure**: `VARCHAR(50)`
   - **avoid_these**: `TEXT`
   - **pursue_these**: `TEXT`
   - **slug**: `VARCHAR(255)`
   - **phone**: `VARCHAR(20)`
   - **unpaid**: `BOOLEAN`
   - **team_about**: `TEXT`
   - **instructions_research**: `TEXT`
   - **job_scope**: `TEXT`
   - **opportunity_location**: `VARCHAR(255)`
   - **tags**: `TEXT`
   - **expected_duration**: `INT`
   - **time_done_scoping_call**: `DATETIME`
   - **close_reason**: `TEXT`

6. **Expert Request Candidates**
   - **id**: `INT` (PK)
   - **request_id**: `INT` (FK to ExpertRequests)
   - **profile_id**: `INT` (FK to Profiles)
   - **email**: `VARCHAR(255)`
   - **created_at**:
