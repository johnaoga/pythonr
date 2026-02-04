Quiz 1 : Bases de Python
========================

.. raw:: html

   <div class="quiz-container" id="quiz-quiz1_python_basics">
   <form id="quiz-form-quiz1_python_basics" onsubmit="return false;">
   <div class="quiz-question" data-qid="quiz1_python_basics_0"> <p class="question-text"><strong>Q1.</strong> Combien vaudra la variable n à la fin de ce programme ?<br><br>``<code><pre><code class="language-python">n=2<br>for i in range(4,12) : <br> n=n-3<br></code>``</code></pre></p> <input type="number" step="any" name="qquiz1_python_basics_0" class="quiz-input" placeholder="Votre réponse..." /> </div>
   <div class="quiz-question" data-qid="quiz1_python_basics_1"> <p class="question-text"><strong>Q2.</strong> Quel est le résultat de <code>2 ** 3</code> en Python ?</p> <input type="number" step="any" name="qquiz1_python_basics_1" class="quiz-input" placeholder="Votre réponse..." /> </div>
   <div class="quiz-question" data-qid="quiz1_python_basics_2"> <p class="question-text"><strong>Q3.</strong> Quelle fonction permet d'afficher du texte dans la console en Python ?</p> <input type="text" name="qquiz1_python_basics_2" class="quiz-input" placeholder="Votre réponse..." /> </div>
   <div class="quiz-question" data-qid="quiz1_python_basics_3"> <p class="question-text"><strong>Q4.</strong> Quelle structure de données est <strong>mutable</strong> en Python ?</p> <div class="quiz-options"> <label class="quiz-option"> <input type="radio" name="qquiz1_python_basics_3" value="0" /> <span>tuple</span> </label> <label class="quiz-option"> <input type="radio" name="qquiz1_python_basics_3" value="1" /> <span>list</span> </label> <label class="quiz-option"> <input type="radio" name="qquiz1_python_basics_3" value="2" /> <span>string</span> </label> <label class="quiz-option"> <input type="radio" name="qquiz1_python_basics_3" value="3" /> <span>frozenset</span> </label> </div> </div>
   <div class="quiz-question" data-qid="quiz1_python_basics_4"> <p class="question-text"><strong>Q5.</strong> Quels sont les types numériques natifs en Python ?</p> <p class="question-hint"><em>(Plusieurs réponses possibles)</em></p> <div class="quiz-options"> <label class="quiz-option"> <input type="checkbox" name="qquiz1_python_basics_4" value="0" /> <span>int</span> </label> <label class="quiz-option"> <input type="checkbox" name="qquiz1_python_basics_4" value="1" /> <span>float</span> </label> <label class="quiz-option"> <input type="checkbox" name="qquiz1_python_basics_4" value="2" /> <span>str</span> </label> <label class="quiz-option"> <input type="checkbox" name="qquiz1_python_basics_4" value="3" /> <span>complex</span> </label> <label class="quiz-option"> <input type="checkbox" name="qquiz1_python_basics_4" value="4" /> <span>bool</span> </label> </div> </div>
   </form>
   <div class="quiz-actions">
   <button type="button" class="quiz-btn quiz-btn-check" onclick="checkQuiz('quiz1_python_basics')">✓ Vérifier mes réponses</button>
   <button type="button" class="quiz-btn quiz-btn-reset" onclick="resetQuiz('quiz1_python_basics')">↺ Recommencer</button>
   </div>
   <div id="result-quiz1_python_basics" class="quiz-result"></div>
   <div id="explanations-quiz1_python_basics" class="quiz-explanations"></div>
   </div>
   <script>
   if (typeof window.quizData === 'undefined') window.quizData = {};
   window.quizData['quiz1_python_basics'] = {"questions": [{"id": "quiz1_python_basics_0", "type": "number", "answer": -22.0, "tolerance": 0, "explanation": "La boucle tournera de 4 à 11 (attention pas 12). \nMais `i` n'intervient pas dans l'opération c'est juste faire `-3 * 8 = -24 + 2 = -22` (! is est le nombre de fois ou la boucle tournera, 11-4+1)"}, {"id": "quiz1_python_basics_1", "type": "number", "answer": 8.0, "tolerance": 0.0, "explanation": "L'opérateur `**` en Python représente l'exponentiation. `2 ** 3` signifie 2 puissance 3, soit 2 × 2 × 2 = 8."}, {"id": "quiz1_python_basics_2", "type": "text", "answer": "print", "case_sensitive": false, "explanation": "La fonction `print()` est utilisée pour afficher du texte ou des valeurs dans la console Python."}, {"id": "quiz1_python_basics_3", "type": "single", "answer": 1, "explanation": "Les listes (`list`) sont mutables en Python, ce qui signifie qu'on peut modifier leurs éléments après création. Les tuples, strings et frozensets sont immuables."}, {"id": "quiz1_python_basics_4", "type": "multiple", "answers": [0, 1, 3], "explanation": "Python possède trois types numériques natifs : `int` (entiers), `float` (nombres à virgule flottante) et `complex` (nombres complexes). `str` est pour les chaînes de caractères et `bool` est un sous-type de `int`."}]};
   </script>

