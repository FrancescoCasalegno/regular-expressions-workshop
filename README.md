This material was prepared for the workshop held on 2022-04-07 at the Gymnasium Thun (Thun, Switzerland), and updated for the workshop held on 2022-09-02 at EPFL (Lausanne, Switzerland). 

# Regex 101

| pattern     | meaning                                                 | usage                                                            | matches                                      | doesn't match                                                   |
|-------------|---------------------------------------------------------|------------------------------------------------------------------|----------------------------------------------|-----------------------------------------------------------------|
| `\b`        | frontière d'un mot (début ou fin d'un mot)              | `mon\b`                                                          | `mon` dans `mon` ou `démon`                  | `mon` dans `montagne`                                           |
| `\w`        | un caractère alphanumérique (= une lettre ou un nombre) | `\won`                                   <br/> <br/> <br/> <br/> | <br/>`Mon`, `Ton`, `son`, `mon`              | `Tonton`                                                        |
| `[abc]`     | set (un des caractère présents dans les parenthèses)    | `[mst]on`                                 <br/>                  | `mon`, `son`, `ton`                          | `non`, `bon`                                                    |
| `(abc\def)` | groupe (un des groupes de caractères séparés par `\`    | `(Klav\T)ier`                                                    | `Klavier`, `Tier`                            |                                                                 |
| `[a]*`      | 0 ou plusieurs occurence(s)                             | `[\w]*on`                                                        | `on`, `chanson`, `démon`, `tonton`, `bon`    |                                                                 |
| `[a]+`      | 1 ou plusieurs occurrence(s)                            | `[\w]+on`                                                        | `chanson`, `démon`, `tonton`, `bon`          | `son`                                                           |
| `[a]?`      | 0 ou 1 occurrence                                       | `[s]?on`                                                         | `on`, `son`                                  | `ton`                                                           |
| `^`         | début d'une ligne                                       | `^Mon`                                      <br/>                | `Mon` au début de la ligne (`"Mon nom est"`) | `Mon` au milieu de la ligne (`"Le Mont Blanc est magnifique!"`) |

# Set Up
1. Open the RegExr webpage [https://regexr.com/](https://regexr.com/) in your browser.
2. Set the RegEx engine to "JavaScript (Browser)".
3. Set the Tools to "List".
4. Set the Flags to "global" and "multiline".
5. Open [scraped_wiki_neuron.md](scraped_wiki_neuron.md) and copy-paste its contents into the text box of the RegExr website. 

# Exercises
Try to write regular expressions that extract the following contents from the text.
1. Extract exact mention of the word `"neuron"`. [34 matches]
2. What about uppercase, e.g. at the beginning of a sentence? Extract mention of the word `"neuron"` or `"Neuron"`. [35 matches]
3. What about plurals?  Try to extract `"neurons"`, `"Neurons"`, `"neuron"`, or `"Neuron"`. [105 matches]
4. Now, any word containing `"neur"` or `"Neur"` inside of it (e.g. `"interneuronal"`). [147 matches]
5. Certain words use the root `"nerv"` to express similar concepts (e.g. `"nervous system"`). Extract all words containing `"neur"`, `"Neur"`, `"nerv"`, or `"Nerv"`,  inside of it. [170 matches]
6. Under the section ["Classification"](scraped_wiki_neuron.md#Classification) we find a bulleted list of neuron types. They are all in format `"Xxxx cells"`, where `"Xxxxx"` is an adjective starting with a capital letter like `"Basket cells"` or `"Granule cells"`. Try to extract all of them. [8 matches]
7. Under the section ["Neurotransmitters"](scraped_wiki_neuron.md#Neurotransmitters) we find another bulleted list of neuron types. They are all in format `"Xxxx neurons"`, where `"Xxxxx"` is an adjective starting with a capital letter like `"Cholinergic neurons"` or `"Purinergic neurons"`. Try to extract all of them. [9 matches]

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
