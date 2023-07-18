#  Medical Insurance Flow 

### I. Overview 
This project demonstrates a multi party Health Insurance workflow modelled using DAML  

### II. Actors
  1. Patient who needs treatment
  2. Registrar - resposible for maintaing the patient medical record
  3. Doctor
  4. Insurer proving medical insurance
  5. Bank for claim settlement

### III. Workflow
Preconditions
  Patient medical record is maintained by Registrar and owned by patient
  Patient has insurance policy with Insurer and he can share it with other parties as needed
  
  1. doctor creates the OfferAppointment contract with patient as observer     
  2. patient exercices the choice AcceptAppointment sharing his MedicalRecordId(that is kept with Registrar) and insurance provider details. Executing this choice creates the appoint with the doctor
  3. doctor provides the treatment and excercise the choice PrescribeTreatment recording treatment details, fetch health insurance policy and creates a new claim for the treatment expenses

### IV. Compiling & Testing
To compile and test, run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```
