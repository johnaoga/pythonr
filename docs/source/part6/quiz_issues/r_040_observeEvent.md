### Quiz ID

quiz5_r_visualization

### Question Type

single (single choice)

### Question

Quelle fonction Shiny est préférée pour exécuter du code en réponse à un événement spécifique (comme un clic de bouton) ?

### Options (for single/multiple choice only)

observe()
reactive()
observeEvent()
eventReactive()

### Answer

2

### Tolerance (number type only)

_No response_

### Case Sensitive (text type only)

_No response_

### Explanation (optional)

`observeEvent(input$button, {...})` exécute le code uniquement quand le bouton est cliqué. `observe()` réagit à toute dépendance, ce qui peut être moins performant.
