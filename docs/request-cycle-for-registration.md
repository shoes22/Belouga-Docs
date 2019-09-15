# Request Cycle for Registration

During the registration process, you will be making a number of requests to the Belouga API server to retrieve data, validate input,and to finally submit the registration form. These API endpoints are listed below in the order that they should be requested. Steps 1-5 should all be performed via AJAX before submit.

1. ### getCountryCodes
Request this endpoint before or during the loading of your registration form. The results from this endpoint will populate the "new-user-country" field of your registration form. If a country is not in the returned list, the user cannot register. We do not allow new country requests from external registrations.
2. ### getStatesByCountryCode
Your server should make this request when a user selects a country from the country dropdown. The results of this endpoint will populate the "State/Region" dropdown of your registration form. You must use this endpoint when retrieving State/Region names, so the IDs can map properly in our database.
3. ### getSchoolsByStateID or getDistrictsByStateID
Your server should make this request when a state/region is selected from the state/region dropdown. The results of this endpoint will populate either the "Schools" or "Districts" list dropdown of your registration form, so the registration can map to an existing school or district ID, if the school/district already exists in our database. If a new school or district is being registered that does not exist in our database, include the name of the school/district in the "new-user-school" field instead of the ID.
4. ### checkEmail
Your server should make this request immediately after the user fills out the teacher-email field. We will check whether the email is valid and unique or not.

5. ### checkUsername 
Your server should make this request immediately after the user fills out the teacher-username field. We will check whether the username is valid and unique or not.

6. ### registerTeacher
Use this endpoint to actually submit the registration form. Make sure to include the user object inside the encrypted PASETO token, not as POST data.