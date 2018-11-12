---
title: Expressions régulières (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: dafbe7c7ba10db2b0f34fdc6065c1475d63be284
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443461"
---
# <a name="regular-expressions-c"></a>Expressions régulières (C++)

La bibliothèque C++ standard prend en charge plusieurs grammaires d’expressions régulières. Cette rubrique aborde les variations de grammaire disponibles lors de l’utilisation d’expressions régulières.

## <a name="regexgrammar"></a> Grammaire des expressions régulières

La grammaire d’expression régulière à utiliser est spécifiée à l’aide d’un par le `std::regex_constants::syntax_option_type` valeurs d’énumération. Ces grammaires d’expressions régulières sont définies dans std::regex_constants :

- `ECMAScript`: Il s’agit le plus proche de la grammaire utilisée par JavaScript et les langages .NET.
- `basic`: Les expressions régulières base POSIX ou un BRE.
- `extended`: La POSIX étendue des expressions régulières ou ERE.
- `awk`: Il s’agit de `extended`, mais il a d’autres séquences d’échappement pour les caractères non imprimables.
- `grep`: Il s’agit de `basic`, mais il permet également saut de ligne ('\n') caractères séparateur d’alternatives.
- `egrep`: Il s’agit de `extended`, mais il permet également des caractères de saut de ligne séparer les alternatives.

Par défaut, si aucune syntaxe n’est spécifié, `ECMAScript` est supposé. Grammaire qu’une seule peut être spécifiée.

En plus de la grammaire, plusieurs indicateurs peuvent être appliqués :
- `icase`: Ignorer la casse lors de la correspondance.
- `nosubs`: Ignorer les correspondances marquées (autrement dit, des expressions entre parenthèses) ; aucune substitution n’est stockées.
- `optimize`: Assurez-vous de correspondance plus rapidement, aux dépens du moment de la construction.
- `collate`: Utilisez des séquences de classement de respectant les paramètres régionaux (par exemple, les plages de la forme « [a-z] »).

Zéro ou plusieurs indicateurs peuvent être combinées avec la syntaxe pour spécifier le comportement de moteur d’expression régulière. Si seuls sont spécifiés, `ECMAScript` est considéré comme étant la grammaire.

### <a name="element"></a>Élément

Un élément peut être ce qui suit :

- *Caractère ordinaire* qui correspond au même caractère dans la séquence cible.

- *Caractère générique* "." qui correspond à n’importe quel caractère dans la séquence cible, à l’exception d’un saut de ligne.

- *Expression entre crochets* au format "[`expr`]", qui correspond à un caractère ou à un élément de classement dans la séquence cible qui se trouve également dans le jeu défini par l’expression `expr`, ou au format "[^`expr`]", qui correspond à un caractère ou à un élément de classement dans la séquence cible qui ne se trouve pas dans le jeu défini par l’expression `expr`.

   L'expression `expr` peut contenir n'importe quelle combinaison des éléments suivants :

   - Un caractère individuel. Ajoute ce caractère au jeu défini par `expr`.

   - Une *plage de caractères* au format "`ch1`-`ch2`". Ajoute des caractères qui sont représentés par des valeurs dans la plage fermée [`ch1`, `ch2`] au jeu défini par `expr`.

   - Une *classe de caractères* au format "[:`name`:]". Ajoute les caractères de la classe nommée au jeu défini par `expr`.

   - Une *classe d’équivalence* au format "[=`elt`=]". Ajoute les éléments de classement qui sont équivalents à `elt` au jeu défini par `expr`.

   - Un *symbole de classement* au format "[.`elt`.]". Ajoute l'élément de classement `elt` au jeu défini par `expr`.

- Une *ancre*. L'ancre '^' correspond au début de la séquence cible ; l'ancre '$' correspond à la fin de la séquence cible.

Un *groupe de capture* au format "( *sous-expression* )", ou "\\( *sous-expression* \\)" dans `basic` et `grep`, qui correspond à la séquence de caractères dans la séquence cible correspondant au modèle situé entre les délimiteurs.

- Un *échappement d’identité* au format "\\`k`", qui correspond au caractère `k` dans la séquence cible.

Exemples :

- "a" correspond à la séquence cible "a", mais pas aux séquences cibles "B", "b" ou "c".

- "." correspond à toutes les séquences cibles "a", "B", "b" et "c".

- "[b-z]" correspond aux séquences cibles "b" et "c", mais pas aux séquences cibles "a" ou "B".

- "[:lower:]" correspond aux séquences cibles "a", "b" et "c", mais pas à la séquence cible "B".

- "(a)" correspond à la séquence cible "a" et associe le groupe de capture 1 à la sous-séquence "a", mais il ne correspond pas aux séquences cibles "B", "b" ou "c".

Dans `ECMAScript`, `basic` et `grep`, un élément peut également être une *référence arrière* au format "\\`dd`", où `dd` représente une valeur décimale N qui correspond à une séquence de caractères dans la séquence cible qui est identique à la séquence de caractères correspondant au Nième *groupe de capture*. Par exemple, "(a)\1" correspond à la séquence cible "aa", car le premier (et unique) groupe de capture correspond à la séquence initiale "a", et \1 correspond à la séquence finale "a".

Dans `ECMAScript`, un élément peut également être ce qui suit :

- Un *groupe de non capture* sous la forme « ( ? : *sous-expression* ) ». Correspond à la séquence de caractères de la séquence cible qui correspond au modèle situé entre les délimiteurs.

- Un *échappement de format de fichier* limité au format "\f", "\n", "\r", "\t" ou "\v". Ces derniers correspondent, respectivement, à un saut de page, un saut de ligne, un retour chariot, une tabulation horizontale et une tabulation verticale, dans la séquence cible.

- Une *assertion positive* au format "(= *sous-expression* )". Correspond à la séquence de caractères de la séquence cible qui correspond au modèle situé entre les délimiteurs, mais qui ne modifie pas la position correspondante dans la séquence cible.

- Une *assertion négative* au format "(! *sous-expression* )". Correspond à n’importe quelle séquence de caractères de la séquence cible qui ne correspond pas au modèle situé entre les délimiteurs, et ne modifie pas la position correspondante dans la séquence cible.

- Une *séquence d’échappement hexadécimale* au format "\x`hh`". Correspond à un caractère de la séquence cible qui est représenté par les deux chiffres hexadécimaux `hh`.

- Une *séquence d’échappement Unicode* au format "\u`hhhh`". Correspond à un caractère de la séquence cible qui est représenté par les quatre chiffres hexadécimaux `hhhh`.

- Une *séquence Contrôle Échap* au format "\c`k`". Correspond au caractère de contrôle nommé par le caractère `k`.

- Une *assertion de limite de mot* au format "\b". Correspond à la position actuelle dans la séquence cible qui est située immédiatement après une *limite de mot*.

- Une *assertion négative de limite de mot* au format "\B". Correspond à la position actuelle dans la séquence cible qui n’est pas située immédiatement après une *limite de mot*.

- Un *caractère d’échappement dsw* au format "\d", "\D", "\s", "\S", "\w", "\W". Fournit un nom court pour une classe de caractères.

Exemples :

- "(?:a)" correspond à la séquence cible "a", mais "(?:a)\1" n'est pas valide, car il n'existe aucun groupe de capture 1.

- "(=a)a" correspond à la séquence cible "a". L'assertion positive correspond à la séquence initiale "a" dans la séquence cible, et le dernier "a" de l'expression régulière correspond à la séquence initiale "a" de la séquence cible.

- "(!a)a" ne correspond pas à la séquence cible "a".

- "a\b." correspond à la séquence cible "a~", mais pas à la séquence cible "ab".

- "a\B." correspond à la séquence cible "ab", mais pas à la séquence cible "a~".

Dans `awk`, un élément peut également être ce qui suit :

- Un *échappement de format de fichier* au format "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" ou "\v". Ces derniers correspondent, respectivement, à une barre oblique inverse, une alerte, un retour arrière, un saut de page, un saut de ligne, un retour chariot, une tabulation horizontale et une tabulation verticale, dans la séquence cible.

- Une *séquence d’échappement octale* au format "\\`ooo`". Correspond à un caractère de la séquence cible qui est représenté par la valeur `ooo` d'un, deux ou trois chiffres octaux.

### <a name="repetition"></a>Répétition

Tous les éléments autres qu’une *assertion positive*, une *assertion négative* ou une *ancre* peuvent être suivis par un nombre de répétitions. Le type le plus général de nombre de répétitions apparaît au format "{`min`,`max`}", ou "\\{`min`,`max`\\}" dans `basic` et `grep`. Un élément qui est suivi par ce format de nombre de répétitions correspond au moins à `min` occurrences successives, et au maximum à `max` occurrences successives d'une séquence qui correspond à l'élément. Par exemple, « un{2,3}» correspond à la séquence cible « aa » et la séquence cible « aaa », mais pas la séquence cible « a » ou la séquence cible « aaaa ».

Un nombre de répétitions peut également prendre l'une des formes suivantes :

- "{`min`}", ou "\\{`min`\\}" dans `basic` et `grep`. Équivalent à "{`min`,`min`}".

- "{`min`,}", ou "\\{`min`,\\}" dans `basic` et `grep`. Équivalent à "{`min`, unbounded}".

- "\*". Équivalent à "{0,unbounded}".

Exemples :

- « un{2}» correspond à la séquence cible « aa », mais pas à la séquence cible « a » ou la séquence cible « aaa ».

- « un{2,}» correspond à la séquence cible « aa », la séquence cible « aaa » et ainsi de suite, mais ne correspond pas à la séquence cible « a ».

- « un\*» correspond à la séquence cible « », « a », la séquence cible « aa » de la séquence cible et ainsi de suite.

Pour toutes les grammaires, sauf `basic` et `grep`, un nombre de répétitions peut également prendre l'une des formes suivantes :

- "?". Équivalent à «{0,1}».

- "+". Équivalent à "{1,unbounded}".

Exemples :

- « a » ? correspond à la séquence cible « » et la séquence cible « a », mais pas à la séquence cible « aa ».

- "a+" correspond aux séquences cibles "a", "aa", et ainsi de suite, mais pas à la séquence cible "".

Dans `ECMAScript`, toutes les formes de nombres de répétitions peuvent être suivies par le caractère ' ?', qui désigne une *répétition non gourmande*.

### <a name="concatenation"></a>Concaténation

Les éléments d’expression régulière, avec ou sans *nombre de répétitions*, peuvent être concaténés pour former de plus longues expressions régulières. L'expression résultante correspond à une séquence cible qui est une concaténation des séquences auxquelles correspondent les éléments. Par exemple, « un{2,3}b » correspond à la séquence cible « aab » et la séquence cible « aaab », mais ne correspond pas à la séquence cible « ab » ou la séquence cible "et « aaaab ».

### <a name="alternation"></a>Alternative

Dans toutes les grammaires d’expressions régulières, à l’exception de `basic` et `grep`, une expression régulière concaténée peut être suivie par le caractère "&#124;" et par une autre expression régulière concaténée. Le nombre d'expressions régulières concaténées pouvant être combinées de cette manière est illimité. L'expression résultante correspond à n'importe quelle séquence cible qui correspond à une ou plusieurs expressions régulières concaténées.

Si plusieurs expressions régulières concaténées correspondent à la séquence cible, `ECMAScript` choisit la première des expressions régulières concaténées qui correspond à la séquence (*première correspondance*). Les autres grammaires d’expressions régulières choisissent celle qui correspond à la *correspondance la plus longue*. Par exemple, "ab&#124;cd" correspond à la séquence cible "ab" et à la séquence cible "cd", mais ne correspond pas aux séquences cibles "abd" et "acd".

Dans `grep` et `egrep`, un caractère de saut de ligne ('\n') peut être utilisé comme séparateur d'alternatives.

### <a name="subexpression"></a>Sous-expression

Dans `basic` et `grep`, une sous-expression est une concaténation. Dans les autres grammaires d'expressions régulières, une sous-expression est une alternative.

## <a name="grammarsummary"></a> Résumé des grammaires

Le tableau suivant résume les fonctionnalités disponibles dans les différentes grammaires d’expressions régulières :

|Élément|de base|étendues|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternative utilisant '&#124;'||+|+||+|+|
|alternative utilisant '\n'||||+|+||
|ancre|+|+|+|+|+|+|
|référence arrière|+||+|+|||
|expression entre crochets|+|+|+|+|+|+|
|groupe de capture utilisant "()"||+|+||+|+|
|groupe de capture utilisant "\\(\\)"|+|||+|||
|séquence Contrôle Échap|||+||||
|caractère d'échappement dsw|||+||||
|échappement de format de fichier|||+|||+|
|séquence d'échappement hexadécimale|||+||||
|échappement d'identité|+|+|+|+|+|+|
|assertion négative|||+||||
|assertion négative de limite de mot|||+||||
|groupe de non capture|||+||||
|répétition non gourmande|||+||||
|séquence d'échappement octale||||||+|
|caractère ordinaire|+|+|+|+|+|+|
|assertion positive|||+||||
|répétition utilisant "{}»||+|+||+|+|
|répétition utilisant "\\{\\}"|+|||+|||
|répétition utilisant '\*'|+|+|+|+|+|+|
|répétition utilisant '?' et '+'||+|+||+|+|
|séquence d'échappement Unicode|||+||||
|caractère générique|+|+|+|+|+|+|
|assertion de limite de mot|||+||||

## <a name="semanticdetails"></a> Détails sémantiques

### <a name="anchor"></a>Ancre

Une ancre correspond à une position dans la chaîne cible, et non à un caractère. Un '^' correspond au début de la chaîne cible, et un '$' correspond à la fin de la chaîne cible.

### <a name="back-reference"></a>Référence arrière

Une référence arrière est une barre oblique inverse suivie par une valeur décimale N. Elle correspond au contenu du Nième *groupe de capture*. La valeur N ne doit pas dépasser le nombre de groupes de capture qui précèdent la référence arrière. Dans `basic` et `grep`, la valeur N est déterminée par le chiffre décimal qui suit la barre oblique inverse. Dans `ECMAScript`, la valeur N est déterminée par le nombre total de chiffres décimaux qui suivent immédiatement la barre oblique inverse. Par conséquent, dans `basic` et `grep`, la valeur N n'est jamais supérieure à 9, même si l'expression régulière contient plus de neuf groupes de capture. Dans `ECMAScript`, la valeur N est illimitée.

Exemples :

- "((a+)(b+))(c+)\3" correspond à la séquence cible "aabbbcbbb". La référence arrière "\3" correspond au texte du troisième groupe de capture, "(b+)". Elle ne correspond pas à la séquence cible "aabbbcbb".

- "(a)\2" n'est pas valide.

- "(b(((((((((a))))))))))\10" possède plusieurs significations dans `basic` et `ECMAScript`. Dans `basic`, la référence arrière est "\1". La référence arrière correspond au contenu du premier groupe de capture (autrement dit, celui qui commence par "(b", qui se termine par le ")" final, et qui précède la référence arrière). Le '0' final correspond au caractère ordinaire '0'. Dans `ECMAScript`, la référence arrière est "\10". Elle correspond au dixième groupe de capture, c'est-à-dire, le plus profond.

### <a name="bracket-expression"></a>Expression entre crochets

Une expression entre crochets définit un jeu de caractères et des *éléments de classement*. Lorsque l'expression entre crochets commence par le caractère '^', la correspondance aboutit si aucun élément du jeu ne correspond au caractère actuel de la séquence cible. Sinon, la correspondance aboutit si l'un des éléments du jeu correspond au caractère actuel de la séquence cible.

Le jeu de caractères peut être défini en spécifiant une combinaison de *caractères individuels*, de *plages de caractères*, de *classes de caractères*, de *classes d’équivalence* et de *symboles de classement*.

### <a name="capture-group"></a>Groupe de capture

Un groupe de capture marque son contenu en tant qu'unité dans la grammaire d'expressions régulières, et étiquette le texte cible qui correspond à son contenu. Le nom associé à chaque groupe de capture est un nombre, qui est déterminé par le nombre de parenthèses ouvrantes qui marquent les groupes de capture jusqu'à la parenthèse ouvrante (incluse) qui marque le groupe de capture actuel. Dans cette implémentation, le nombre maximal de groupes de capture est 31.

Exemples :

- "ab+" correspond à la séquence cible "abb", mais pas à la séquence cible "abab".

- "(ab)+" ne correspond pas à la séquence cible "abb", mais correspond à la séquence cible "abab".

- "((a+)(b+))(c+)" correspond à la séquence cible "aabbbc" et associe le groupe de capture 1 à la sous-séquence "aabbb", le groupe de capture 2 à la sous-séquence "aa", le groupe de capture 3 à "bbb", et le groupe de capture 4 à la sous-séquence "c".

### <a name="character-class"></a>Classe de caractères

Dans une expression entre crochets, une classe de caractères ajoute tous les caractères de la classe nommée au jeu de caractères défini par l'expression entre crochets. Pour créer une classe de caractères, utilisez "[:", suivi du nom de la classe, suivi de ":]". En interne, les noms des classes de caractères sont identifiés par l'appel à `id = traits.lookup_classname`. Un caractère `ch` appartient à une telle classe si `traits.isctype(ch, id)` retourne true. Le modèle `regex_traits` par défaut prend en charge les noms de classes répertoriés dans le tableau suivant.

|Nom de la classe|Description|
|----------------|-----------------|
|"alnum"|minuscules, majuscules et chiffres|
|"alpha"|minuscules et majuscules|
|"blank"|espace ou tabulation|
|"cntrl"|caractères d’*échappement de format de fichier*|
|"digit"|chiffres|
|"graph"|minuscules, majuscules, chiffres et ponctuation|
|"lower"|minuscules|
|"print"|minuscules, majuscules, chiffres, ponctuation et espaces|
|"punct"|ponctuation|
|"space"|space|
|"upper|majuscules|
|"xdigit"|chiffres, 'a', 'b', 'c', 'd', 'e', 'f', 'A', 'B', 'C', 'D', 'E', 'F'|
|"d"|identique à "digit"|
|"s"|identique à "space"|
|"w"|identique à "alnum"|

### <a name="character-range"></a>Plage de caractères

Dans une expression entre crochets, une plage de caractères ajoute tous les caractères de la plage au jeu de caractères défini par l'expression entre crochets. Pour créer une plage de caractères, placez le caractère '-' entre le premier et le dernier caractère de la plage. Cela ajoute au jeu tous les caractères ayant une valeur numérique supérieure ou égale à la valeur numérique du premier caractère, et inférieure ou égale à la valeur numérique du dernier caractère. Notez que ce jeu de caractères ajoutés dépend de la représentation de caractères spécifique à la plateforme. Si le caractère '-' apparaît au début ou à la fin d'une expression entre crochets, ou en tant que premier ou dernier caractère d'une plage de caractères, il se représente lui-même.

Exemples :

- "[0-7]" représente le jeu de caractères { '0', '1', '2', '3', '4', '5', '6', '7' }. Il correspond aux séquences cibles "0", "1", etc., mais pas à "a".

- Sur les systèmes qui utilisent l'encodage de caractères ASCII, "[h-k]" représente le jeu de caractères { 'h', 'i', 'j', 'k' }. Il correspond aux séquences cibles "h", "i", etc, mais pas à "\x8A" ou "0".

- Sur les systèmes qui utilisent l'encodage de caractères EBCDIC, "[h-k]" représente le jeu de caractères { 'h', 'i', '\x8A', '\x8B', '\x8C', '\x8D', '\x8E', '\x8F', '\x90', 'j', 'k' } ('h' est encodé comme 0x88 et 'k' est encodé comme 0x92). Il correspond aux séquences cibles "h", "i", "\x8A", etc, mais pas à "0".

- "[-0-24]" représente le jeu de caractères { '-', '0', '1', '2', '4' }.

- "[0-2-]" représente le jeu de caractères { '0', '1', '2', '-' }.

- Sur les systèmes qui utilisent l'encodage de caractères ASCII, "[+--]" représente le jeu de caractères { '+', ',', '-' }.

Toutefois, lorsque des plages respectant les paramètres régionaux sont utilisées, les caractères d'une plage sont déterminés par les règles de classement des paramètres régionaux. Les caractères qui sont classés après le premier caractère de la définition de la plage et avant le dernier caractère de la définition de la plage se trouvent dans le jeu. Les deux caractères de fin sont également dans le jeu.

### <a name="collating-element"></a>Élément de classement

Un élément de classement est une séquence de plusieurs caractères qui est traitée comme un caractère unique.

### <a name="collating-symbol"></a>Symbole de classement

Un symbole de classement d’une expression entre crochets ajoute un *élément de classement* au jeu défini par l’expression entre crochets. Pour créer un symbole de classement, utilisez "[." suivi par l’élément de classement et par ".]".

### <a name="control-escape-sequence"></a>Séquence Contrôle Échap

Une séquence Contrôle Échap est une barre oblique inverse suivie de la lettre 'c', suivie d'une lettre de 'a' à 'z' ou de 'A' à 'Z'. Correspond au caractère de contrôle ASCII nommé par la lettre. Par exemple, "\ci" correspond à la séquence cible "\x09", car \<ctrl-i> a la valeur 0x09.

### <a name="dsw-character-escape"></a>Caractère d'échappement dsw

Un caractère d'échappement dsw est un nom court donné à une plage de caractères, comme indiqué dans le tableau suivant.

|Séquence d'échappement|Classe nommée équivalente|Classe nommée par défaut|
|---------------------|----------------------------|-------------------------|
|"\d"|"[[:d:]]"|"[[:digit:]]"|
|"\D"|"[^[:d:]]"|"[^[:digit:]]"|
|"\s"|"[[:s:]]"|"[[:space:]]"|
|"\S"|"[^[:s:]]"|"[^[:space:]]"|
|"\w"|"[[:w:]]"|« [a-zA-Z0-9_] »\*|
|"\W"|"[^[:w:]]"|« [^ a-zA-Z0-9_] »\*|

\*Jeu de caractères ASCII

### <a name="equivalence-class"></a>Classe d'équivalence

Dans une expression entre crochets, une classe d’équivalence ajoute au jeu défini par l’expression entre crochets, tous les caractères et *éléments de classement* équivalents à l’élément de classement dans la définition de classe d’équivalence. Pour créer une classe d'équivalence, utilisez "[=" suivi d'un élément de classement, suivi de "=]". En interne, les deux éléments de classement `elt1` et `elt2` sont équivalents si `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Échappement de format de fichier

Un échappement de format de fichier comprend les séquences d’échappement de caractère habituelles du langage C : "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" et "\v". Celles-ci ont leur signification habituelle, c’est-à-dire, respectivement, barre oblique inverse, alerte, retour arrière, saut de page, saut de ligne, retour chariot, tabulation horizontale et tabulation verticale. Dans `ECMAScript`, "\a" et "\b" ne sont pas autorisés. "\\\\" est autorisé, mais il s’agit d’un échappement d’identité, et non d’un échappement de format de fichier.

### <a name="hexadecimal-escape-sequence"></a>Séquence d'échappement hexadécimale

Une séquence d'échappement hexadécimale est une barre oblique inverse suivie de la lettre 'x', suivie de deux chiffres hexadécimaux (0-9a-fA-F). Elle correspond à un caractère dans la séquence cible dont la valeur est spécifiée par les deux chiffres. Par exemple, "\x41" correspond à la séquence cible "A" lorsque l'encodage de caractères ASCII est utilisé.

### <a name="identity-escape"></a>Échappement d'identité

Un échappement d'identité est une barre oblique inverse suivie d'un caractère unique. Elle correspond à ce caractère. Il est requis lorsque le caractère a une signification particulière ; si vous utilisez l'échappement d'identité, la signification particulière sera supprimée. Exemple :

- « un\*» correspond à la séquence cible « aaa », mais ne correspond pas à la séquence cible « un\*».

- « un\\\*» ne correspond pas à la séquence cible « aaa », mais correspond à la séquence cible « un\*».

Le jeu de caractères autorisés dans un échappement d'identité dépend de la grammaire d'expression régulière, comme indiqué dans le tableau suivant.

|Grammaire|Caractères autorisés d'échappement d'identité|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` plus { '"', '/' }|
|`ECMAScript`|Tous les caractères à l'exception de ceux pouvant faire partie d'un identificateur. En règle générale, cela inclut des lettres, chiffres, '$', '\_' et les séquences d’échappement unicode. Pour plus d'informations, consultez la spécification du langage ECMAScript.|

### <a name="individual-character"></a>Caractère individuel

Dans une expression entre crochets, un caractère individuel ajoute ce caractère au jeu de caractères défini par l'expression entre crochets. Un '^' se représente lui-même à toute position d'une expression entre crochets, hormis au début.

Exemples :

- "[abc]" correspond aux séquences cibles "a", "b" et "c", mais pas à la séquence "d".

- "[^abc]" correspond à la séquence cible "d", mais pas aux séquences cibles "a", "b" ou "c".

- "[a^bc]" correspond aux séquences cibles "a", "b", "c" et "^", mais pas à la séquence cible "d".

Dans toutes les grammaires d'expressions régulières, à l'exception de `ECMAScript`, si a ']' est le premier caractère qui suit le '[' ouvrant, ou le premier caractère qui suit le '^' initial, il se représente lui-même.

Exemples :

- "[]a" n'est pas valide, car il n'y aucun ']' qui termine l'expression entre crochets.

- "[]abc]" correspond aux séquences cibles "a", "b", "c" et "]", mais pas à la séquence cible "d".

- "[^]abc]" correspond à la séquence cible "d", mais pas aux séquences cibles "a", "b", "c" ou "]".

Dans `ECMAScript`, utilisez '\\]' pour représenter le caractère ']' dans une expression entre crochets.

Exemples :

- "[]a" correspond à la séquence cible "a", car l'expression entre crochets est vide.

- "[\\]abc]" correspond aux séquences cibles "a", "b", "c" et "]", mais pas à la séquence cible "d".

### <a name="negative-assert"></a>Assertion négative

Une assertion négative peut représenter n'importe quel élément, à l'exception de son contenu. Elle ne consomme pas les caractères situés dans la séquence cible. Par exemple, "(!aa) (un\*) » correspond à la séquence cible « a » et associe le groupe 1 capture à la sous-séquence « a ». Elle ne correspond pas à la séquence cible "aa" ni à la séquence cible "aaa".

### <a name="negative-word-boundary-assert"></a>Assertion négative de limite de mot

Une assertion négative de limite de mot aboutit si la position actuelle dans la chaîne cible n’est pas située immédiatement après une *limite de mot*.

### <a name="non-capture-group"></a>Groupe de non capture

Un groupe de non capture marque son contenu comme une unité dans la grammaire d'expressions régulières, mais n'étiquette pas le texte cible. Par exemple, « (a)(?:b)\*(c) » correspond au texte cible « abbc » et associe le groupe de capture 1 à la sous-séquence « un « et groupe de capture 2 à la sous-séquence « c ».

### <a name="non-greedy-repetition"></a>Répétition non gourmande

Une répétition non gourmande consomme la sous-séquence la plus courte de la séquence cible qui correspond au modèle. Une répétition gourmande consomme la sous-séquence la plus longue. Par exemple, "(a+) (un\*b) » correspond à la séquence cible « aaab ». Lorsqu'une répétition non gourmande est utilisée, elle associe le groupe de capture 1 à la sous-séquence "a" au début de la séquence cible, et le groupe de capture 2 à la sous-séquence "aab" à la fin de la séquence cible. Lorsqu'une répétition gourmande est utilisée, elle associe le groupe de capture 1 à la sous-séquence "aaa", et le groupe de capture 2 à la sous-séquence "b".

### <a name="octal-escape-sequence"></a>Séquence d'échappement octale

Une séquence d'échappement octale est une barre oblique inverse suivie de un, deux ou trois chiffres octaux (0-7). Elle correspond à un caractère dans la séquence cible dont la valeur est spécifiée par ces chiffres. Si tous les chiffres ont la valeur '0', la séquence n'est pas valide. Par exemple, "\101" correspond à la séquence cible "A" lorsque l'encodage de caractères ASCII est utilisé.

### <a name="ordinary-character"></a>Caractère ordinaire

Un caractère ordinaire est un caractère valide qui n'a pas de signification spéciale dans la grammaire actuelle.

Dans `ECMAScript`, les caractères suivants ont une signification particulière :

- ^  $  \  .  \*  +  ?  (  )  \[  ]  {  }&#124;

Dans `basic` et `grep`, les caractères suivants ont une signification particulière :

- .   \[   \

Dans `basic` et `grep`, les caractères suivants ont une signification particulière lorsqu'ils sont utilisés dans un contexte spécifique :

- '\*' a une signification spéciale dans tous les cas sauf quand il est le premier caractère dans une expression régulière ou le premier caractère qui suit un premier ' ^' dans une expression régulière, ou lorsqu’il est le premier caractère d’une capture de groupe ou le premier caractère suit un premier ' ^' dans un groupe de capture.

- '^' possède une signification particulière lorsqu'il s'agit du premier caractère d'une expression régulière.

- '$' possède une signification particulière lorsqu'il s'agit du dernier caractère d'une expression régulière.

Dans `extended`, `egrep` et `awk`, les caractères suivants ont une signification particulière :

- .   \[   \   (   \*   +   ?   {   &#124;

Dans `extended`, `egrep` et `awk`, les caractères suivants ont une signification particulière lorsqu'ils sont utilisés dans un contexte spécifique.

- ')' possède une signification particulière lorsqu'il correspond à un '(' qui le précède.

- '^' possède une signification particulière lorsqu'il s'agit du premier caractère d'une expression régulière.

- '$' possède une signification particulière lorsqu'il s'agit du dernier caractère d'une expression régulière.

Un caractère ordinaire correspond au même caractère situé dans la séquence cible. Par défaut, cela signifie que la correspondance aboutit si les deux caractères sont représentés par la même valeur. Dans une correspondance respectant la casse, les deux caractères `ch0` et `ch1` correspondent si `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. Dans une correspondance respectant les paramètres régionaux, les deux caractères `ch0` et `ch1` correspondent si `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Assertion positive

Une assertion positive correspond à son contenu, mais ne consomme pas les caractères de la séquence cible.

Exemples :

- "(=aa) (un\*) » correspond à la séquence cible « aaaa » et associe le groupe de capture 1 à la sous-séquence « aaaa ».

- « (aa) (un\*) » correspond à la séquence cible « aaaa » et associe le groupe de capture 1 à la sous-séquence « aa » au début de la cible séquence et capture le groupe 2 à la sous-séquence « aa » à la fin de la séquence cible.

- "(=aa)(a)&#124;(a)" correspond à la séquence cible "a" et associe le groupe de capture 1 à une séquence vide (car l’assertion positive a échoué), et le groupe de capture 2 à la sous-séquence "a". Elle correspond également à la séquence cible "aa" et associe le groupe de capture 1 à la sous-séquence "aa", et le groupe de capture 2 à une séquence vide.

### <a name="unicode-escape-sequence"></a>Séquence d'échappement Unicode

Une séquence d'échappement Unicode est une barre oblique inverse suivie de la lettre 'u', suivie de quatre chiffres hexadécimaux (0-9a-fA-F). Elle correspond à un caractère dans la séquence cible dont la valeur est spécifiée par les quatre chiffres. Par exemple, "\u0041" correspond à la séquence cible "A" lorsque l'encodage de caractères ASCII est utilisé.

### <a name="wildcard-character"></a>Caractère générique

Un caractère générique correspond à n'importe quel caractère de l'expression cible, à l'exception du saut de ligne.

### <a name="word-boundary"></a>Limite de mot

Une limite de mot apparaît dans les situations suivantes :

- Le caractère actuel se situe au début de la séquence cible, et fait partie des caractères alphabétiques `A-Za-z0-9_.`

- Le caractère actuel se situe après la fin de la séquence cible, et le dernier caractère de la séquence cible est l'un des caractères alphabétiques.

- Le caractère actuel est l'un des caractères alphabétiques, contrairement au caractère précédent.

- Le caractère actuel n'est pas l'un des caractères alphabétiques, contrairement au caractère précédent.

### <a name="word-boundary-assert"></a>Assertion de limite de mot

Une assertion de limite de mot aboutit si la position actuelle dans la chaîne cible est située immédiatement après une *limite de mot*.

## <a name="matchingandsearching"></a> Correspondance et recherche

Pour qu'une expression régulière corresponde à une séquence cible, l'expression régulière dans son intégralité doit correspondre à la séquence cible dans son intégralité. Par exemple, l'expression régulière "bcd" correspond à la séquence cible "bcd", mais ne correspond pas aux séquences cibles "abcd" ou "bcde".

Pour qu'une recherche d'expression régulière aboutisse, la séquence cible doit contenir une sous-séquence qui corresponde à l'expression régulière. En général, la recherche trouve la sous-séquence correspondante située la plus à gauche.

Exemples :

- Une recherche de l'expression régulière "bcd" dans la séquence cible "bcd" aboutit et correspond à la séquence complète. La même recherche dans la séquence cible "abcd" aboutit également et correspond aux trois derniers caractères. La même recherche dans la séquence cible "bcde" aboutit également et correspond aux trois premiers caractères.

- Une recherche de l'expression régulière "bcd" dans la séquence cible "bcdbcd" réussit et correspond aux trois premiers caractères.

Lorsque plusieurs sous-séquences correspondantes se trouvent au même emplacement de la séquence cible, il existe deux moyens de choisir le modèle correspondant. La *première correspondance* choisit la sous-séquence qui a été trouvée en premier parmi les correspondances avec l’expression régulière. La *correspondance la plus longue* choisit la sous-séquence la plus longue parmi les correspondances trouvées à cet emplacement. En présence de plusieurs sous-séquences possédant toutes la longueur maximale, la correspondance la plus longue choisit celle qui a été rencontrée en premier. Par exemple, si la première correspondance est utilisée, une recherche de l’expression régulière "b&#124;bc" dans la séquence cible "abcd" correspond à la sous-séquence "b", car le terme de gauche de l’alternative correspond à cette sous-séquence. Par conséquent, la première correspondance n’essaie pas le terme de droite de l’alternative. Lorsque la plus longue correspondance est utilisée, la même recherche correspond à "bc", car "bc" est plus long que "b".

Une correspondance partielle aboutit si la correspondance atteint la fin de la séquence cible sans échouer, même si elle n'a pas atteint la fin de l'expression régulière. Par conséquent, après la réussite d'une correspondance partielle, l'ajout de caractères à la séquence cible peut entraîner l'échec de la prochaine correspondance partielle. Toutefois, après l'échec d'une correspondance partielle, l'ajout de caractères à la séquence cible ne peut pas permettre la réussite de la prochaine correspondance partielle. Par exemple, avec une correspondance partielle, "ab" correspond à la séquence cible "a", mais pas à "ac".

## <a name="formatflags"></a> Indicateurs de format

|Règles de format ECMAScript|Règles de format sed|Texte de remplacement|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Séquence de caractères qui correspond à l'intégralité de l'expression régulière (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|« $\`» (signe dollar suivi d’apostrophe)||Séquence de caractères qui précède la sous-séquence correspondant à l'expression régulière (`[match.prefix().first, match.prefix().second)`)|
|"$'" (signe dollar suivi d'un guillemet)||Séquence de caractères qui suit la sous-séquence correspondant à l'expression régulière (`[match.suffix().first, match.suffix().second)`)|
|"$n"|"\n"|La séquence de caractères qui correspond au groupe de capture à la position `n`, où `n` est un nombre compris entre 0 et 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|"\n"|
|"$nn"||La séquence de caractères qui correspond au groupe de capture à la position `nn`, où `nn` est un nombre compris entre 10 et 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
