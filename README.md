This material was prepared for the workshop held on 2022-04-07 at the Gymnasium Thun (Thun, Switzerland), and updated for the workshop held on 2022-09-02 at EPFL (Lausanne, Switzerland). 

# Regex 101

| pattern     | utilité                                                 | exemple                                                          | peut correspondre à                          | ne peut pas correspondre à                                      |
|-------------|---------------------------------------------------------|------------------------------------------------------------------|----------------------------------------------|-----------------------------------------------------------------|
| `\b`        | frontière d'un mot (début ou fin d'un mot)              | `mon\b`                                                          | `mon` dans `mon` ou `poumon`                 | `mon` dans `montagne`                                           |
| `\w`        | un caractère alphanumérique (= une lettre ou un nombre) | `\won`                                   <br/> <br/> <br/> <br/> | <br/>`Mon`, `Ton`, `son`, `mon`              | `Tonton`                                                        |
| `[abc]`     | set (un des caractère présents dans les parenthèses)    | `[mst]on`                                 <br/>                  | `mon`, `son`, `ton`                          | `non`, `bon`                                                    |
| `(abc\def)` | groupe (un des groupes de caractères séparés par `\`    | `(chans\mai)son`                                                 | `chanson`, `maison`                          |                                                                 |
| `[a]*`      | 0 ou plusieurs occurence(s)                             | `[\w]*on`                                                        | `on`, `chanson`, `poumon`, `tonton`, `bon`   |                                                                 |
| `[a]+`      | 1 ou plusieurs occurrence(s)                            | `[\w]+on`                                                        | `chanson`, `poumon`, `tonton`, `bon`         | `son`                                                           |
| `[a]?`      | 0 ou 1 occurrence                                       | `[s]?on`                                                         | `on`, `son`                                  | `ton`                                                           |
| `^`         | début d'une ligne                                       | `^Mon`                                      <br/>                | `Mon` au début de la ligne (`"Mon nom est"`) | `Mon` au milieu de la ligne (`"Le Mont Blanc est magnifique!"`) |

# Préparation
1. Ouvrez le site RegExr [https://regexr.com/](https://regexr.com/) dans votre browser.
2. Changez les paramètres de RegExr pour "JavaScript (Browser)".
3. Changez les outils pour "List".
4. Activez les "Flags" "global" and "multiline".
5. Ouvrez [scraped_wiki_neuron.md](scraped_wiki_neuron.md) et copiez-collez le contenu dans la boite de texte.

# Exercices
Essayer d'écrire les expressions qui permettront d'extraire du texte
1. Toutes les mentions exactes du mot `"neuron"`. [34 réponses]
2. Que se passe-t-il si le mot commence par une majuscule ? Parce qu'il se trouve au début de la phrase par exemple. 
   Essayez d'extraire les mentions du mot `"neuron"` ou `"Neuron"`. [35 réponses]
3. Que se passe-t-il pour la forme plurielle ? Essayez d'extraire `"neurons"`, `"Neurons"`, `"neuron"`, ou `"Neuron"`.
   [105 réponses]
4. Maintenant, essayez d'extraire tous les mots contenant `"neur"` ou `"Neur"` (comme par exemple `"interneuronal"`).
   [147 réponses]
5. Certains mot en anglais utilisent la racine `"nerv"` pour exprimer des concepts similaires (par exemple `"nervous 
   system"`). Essayer d'extraire tous les mots contenant `"neur"`, `"Neur"`, `"nerv"`, ou `"Nerv"`. [170 réponses]
6. Dans la section ["Classification"](scraped_wiki_neuron.md#Classification), nous trouvons une liste de types de 
   cellules. Ils sont tous sous la forme `"Xxxx cells"`, où `"Xxxxx"` est un adjectif commencant par une lettre 
   majuscule comme `"Basket cells"` or `"Granule cells"`. Essayez de tous les extraire. [8 réponses]
7. Dans la section ["Neurotransmitters"](scraped_wiki_neuron.md#Neurotransmitters), nous trouvons une liste
   de types de neurones. Ils sont tous sous la forme `"Xxxx neurons"`, où `"Xxxxx"` est un adjectif commencant par 
   une lettre majuscule comme `"Cholinergic neurons"` ou `"Purinergic neurons"`. Essayez de tous les extraire. [9 
   réponses]


# Solutions
<details>

<summary>Click here!</summary>
  <ol>
  <li> <code>\bneuron\b</code> </li>
  <li> <code>\b[nN]euron\b</code> </li>
  <li> <code>\b[nN]euron[s]?\b</code> </li>
  <li> <code>\b[\w]*[nN]eur[\w]*\b</code> </li>
  <li> <code>\b[\w]*[nN]e(ur|rv)[\w]*\b</code> </li>
  <li> <code>^\w+ cells\b</code> </li>
  <li> <code>^\w+ neurons\b</code> </li>
</details>
