# 🛠️ Medical Insurance Flow 🛠️ 

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
  
  1. doctor creates the OfferAppointment contract with the observer as patient     
  2. patient exercices  
  3. evaluator exercises ProposerAccomplishments to check proposer's past accomplishments and confirm if proposer is ready to take on a new responsibility
  4. evaluator exercises Reject with a feedback: "Aim to finish it by the end of March"
  5. proposer exercises Revise with an updated endDate (March 25, 2023)
  6. evaluator exercises Approve - a Project contract is created
  7. evaluator exercises Evaluate and decides that it's ready to be published - an Accomplishment contract is created

### III. Challenge(s)
* `controller ... can` syntax causes warning in Daml 2.0+. The code itself does not cause any issues/errors in 2.5.0 but according to the warning, the syntax will be deprecated in the future versions of Daml. More information [here](https://docs.daml.com/daml/reference/choices.html#daml-ref-controller-can-deprecation).
* The new controller syntax requires a controller to be an observer first before they can exercise a choice, otherwise it'll throw an error: "Attempt to fetch or exercise a contract not visible to the committer." For more information, check out [this post](https://discuss.daml.com/t/error-attempt-to-fetch-or-exercise-a-contract-not-visible-to-the-committer/1304/1) on the Daml Forum.
* The project was created by using `empty-skeleton` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```
and the following was added:

```
exposed-modules:
  - Main
```
For more info, check out [this post](https://discuss.daml.com/t/sandbox-options-wall-clock-time/5692/16?u=cathy_jung) on Daml Forum and [Daml Doc](https://docs.daml.com/tools/navigator/index.html?&_ga=2.48248804.337210607.1673989679-241632404.1672853064&_gac=1.17025355.1673455980.CjwKCAiA2fmdBhBpEiwA4CcHzfI2w1_D95zAr3_d6QTypOMXGTpUxtS06c55inucNwZvUZn4AebsJxoCZEgQAvD_BwE&_gl=1*elem6v*_ga*MjQxNjMyNDA0LjE2NzI4NTMwNjQ.*_ga_GVK9ZHZSMR*MTY3Mzk5NDQzOS4zMS4xLjE2NzM5OTQ3MDcuMC4wLjA.#logging-in-as-a-party).


### IV. Compiling & Testing
To compile and test, run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```
