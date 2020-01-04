Data: wherever we are defining or using props
- If it's passed in from a parent via props, it probably isn't state.
- If it does NOT change over time, it probably isn't state.
- If it can be computed based on other state or props in your component, it probably isn't state. 

TimersDashboard
- passing to ToggleableTimerForm
  - isOpen boolean: STATE

EditableTimerList
- timer properties: STATE
  - runningSince: this is also state?
  - editFormOpen boolean

EditableTimer
  - editFormOpen boolean: STATE
  - timer properties: not state, because passed in

Timer
- passed in from parent, NOT STATE 
  - elapsed
  - title
  - project

TimerForm
- special case because forms are special state managers
  - title
  - project


# Stateful data outside of TimerForm (forms are special cases)
- list of timers and properties of each timer: owned by timersdashboard
- whether or not the edit form of each timer is open (timer otherwise): owned by editabletimer
- whether or not the create form is open (button otherwise): owned by timerform
