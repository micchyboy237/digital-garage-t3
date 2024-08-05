# Subscription Management Documentation

## Table of Contents
1. [Subscription UX Process](#subscription-process)
   - 1.1 [Complete Sign-Up & User Onboarding](#complete-sign-up-user-onboarding)  
   - 1.2 [Confirm Consent](#confirm-consent)  
   - 1.3 [Choose Subscription Type](#choose-subscription-type)  
   - 1.4 [IAP Subscription Modal](#iap-subscription-modal)
   - 1.5 [Validate Receipts (for Premium Users)](#validate-receipts)
2. [Scheduled Payment Flows](#recurring-payment-flows)
   - 2.1 [Capture Payment](#capture-payment)  
   - 2.2 [Send Receipts](#send-receipts)  
3. [User Login and Subscription Monitoring](#user-login-and-subscription-monitoring)
   - 3.1 [User Login](#user-login)  
   - 3.2 [Monitor Subscriptions](#monitor-subscriptions)  
4. [Separate Flows](#separate-flows)
   - 4.1 [Renewals](#renewals)  
   - 4.2 [Reinstalls](#reinstalls)  
   - 4.3 [Recurring Monthly Payments](#recurring-monthly-payments)  
5. [Abstracted Flows by RevenueCat](#abstracted-flows-by-revenuecat)
   - 5.1 [Subscription Management](#subscription-management)  
   - 5.2 [Customer Support](#customer-support)  
   - 5.3 [Analytics and Reporting](#analytics-and-reporting)  
   - 5.4 [Cross-Platform Syncing](#cross-platform-syncing)  


## Subscription Flow

### 1. <a id="subscription-process">Subscription UX Process</a><hr>
- Subscription starts after the user completes the sign-up process and user onboarding forms. This is required before the user can go to dashboard and access the app features.

   - 1.1 <a id="complete-sign-up-user-onboarding">Complete Sign-Up & User Onboarding</a>
      - User begins the sign-up process by signing up using email and password or social media accounts.
      - Complete user onboarding forms to set up the user profile.

   - 1.2 <a id="confirm-consent">Confirm Consent</a>
      - Ensure users consent to data sharing and payment authorization during sign-up.
      - Present a clear consent form outlining the free trial terms and subsequent subscription charges.

   - 1.3 <a id="choose-subscription-type">Choose Subscription Type</a>
      - **Premium**: Full access with a 2-week (14 days) free trial.
         - All features for view, create, edit, delete.
      - **Free**: Limited access with basic features.
         - **Create**: Up to 3 vehicles.
         - **View**: All features in read-only mode. Transferred vehicle documents of any type.
         - **Edit**: 
            - Any vehicle forms if the user is the owner.
            - Enter or update vehicle forms with auto-populated fields from DVLA.
            - Manually enter forms if not existing in DVLA to create the vehicle.
         - **Vehicle Profile**:
            - **DVLA Updates**: Automatically add reminders for MOT (motExpiryDate) and Tax (taxDueDate).
            - **Manual Entry**: Users can manually enter MOT and Tax dates if not available.
         - **Automated Reminders**: Add one item in History for MOT reminder due date and one item for Tax reminder due date.
         - **Transfer Vehicle Ownership**: User can transfer vehicle ownership to another user.
         - **User Profile**: All features.

   - 1.4 <a id="iap-subscription-modal">IAP Subscription Modal</a>
      - Display a **In App Purchase** subscription modal to prompt users to subscribe to the Premium plan.
      - Modal Content: Company logo, subscription details, free trial period, and payment options.<br>(Default: **Apple Pay**).
   - 1.5 <a id="validate-receipts">Validate Receipts (for Premium Users)</a>
     - Immediately validate receipts after a user completes the Premium subscription to confirm the transaction and activate the trial.

### 2. <a id="recurring-payment-flows">Recurring Payment Flows</a><hr>
- These flows handle recurring payments and receipts for subscriptions.

   - 2.1 <a id="capture-payment">Capture Payment</a>
     - Securely capture the initial payment after the trial period ends, transitioning the user to a monthly subscription.

   - 2.2 <a id="send-receipts">Send Receipts</a>
     - Issue digital receipts for all transactions.

### 3. <a id="user-login-and-subscription-monitoring">User Login and Subscription Monitoring</a><hr>
- These flows manage user logins and monitor subscription statuses.

   - 3.1 <a id="user-login">User Login</a>
     - User logs in to access the app features.
   
   - 3.2 <a id="monitor-subscriptions">Monitor Subscriptions</a>
     - Use dashboards and analytics to track and manage subscription statuses and key performance indicators.

### 4. <a id="separate-flows">Separate Flows</a><hr>
- These flows handle edge cases and specific scenarios related to subscription management.

   - 4.1 <a id="renewals">Renewals</a>
     - Renewals occur when a user who had an expired or canceled subscription decides to renew it.
       - **Schedule Renewals**: Automate future payment schedules for Premium users.
       - **Validate Receipts**: Validate receipts during subscription renewals to ensure continuity and correct billing.

   - 4.2 <a id="reinstalls">Reinstalls</a>
     - Reinstalls involve restoring a user's subscription when they reinstall the app or switch devices.
       - **Validate Receipts**: When a user reinstalls the app or switches devices, validate receipts to restore their subscription.

### 5. <a id="abstracted-flows-by-revenuecat">Abstracted Flows by RevenueCat</a><hr>
- RevenueCat simplifies many aspects of managing in-app subscriptions through its comprehensive SDK and API. Here are some key flows abstracted by RevenueCat:

   - 5.1 <a id="subscription-management">Subscription Management</a>
     - **Purchase Handling**: Automates the purchase process, including trial periods and initial charges.
     - **Renewal Management**: Manages subscription renewals and handles billing issues.
     - **Receipt Validation**: Validates receipts to ensure the authenticity of transactions.

   - 5.2 <a id="customer-support">Customer Support</a>
     - **Subscription Transfers**: Manages the transfer of subscriptions between users and handles related events such as expiration and renewal notifications.
     - **Refund Processing**: Provides tools for handling refunds and customer support issues.

   - 5.3 <a id="analytics-and-reporting">Analytics and Reporting</a>
     - **Dashboard and Analytics**: Offers detailed insights into subscription metrics and user behavior.
     - **A/B Testing**: Supports A/B testing for paywalls and subscription offerings.

   - 5.4 <a id="cross-platform-syncing">Cross-Platform Syncing</a>
     - **Multi-Platform Support**: Ensures subscription data is consistent across iOS, Android, and web platforms.
