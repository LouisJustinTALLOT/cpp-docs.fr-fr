---
title: Optimisation de point flottante MSVC
ms.date: 03/09/2018
ms.topic: conceptual
ms.openlocfilehash: 78c5c310f2f348b5cfa5a92feb65e265d28560d9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814369"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Optimisation à virgule flottante de Microsoft Visual C++

Obtenez un descripteur sur l’optimisation du code en virgule flottante à l’aide de la méthode du compilateur Microsoft C++ de la gestion de la sémantique en virgule flottante. Créer des programmes rapides tout en garantissant que seules les optimisations sécurisées sont effectuées sur le code en virgule flottante.

## <a name="optimization-of-floating-point-code-in-c"></a>Optimisation du code à virgule flottante en C++

Un compilateur C++ d’optimisation traduit non seulement le code source en code machine, mais organise également les instructions machine de façon à améliorer l’efficacité et/ou à réduire la taille. Malheureusement, de nombreuses optimisations courantes ne sont pas nécessairement sécurisées lorsqu’il est appliqué à des calculs en virgule flottante. Un bon exemple de ce qui peut être consulté avec l’algorithme de somme suivante, extraite de David Goldberg, « Ce que chaque ordinateur scientifique doit savoir sur Floating-Point Arithmetic », *Computing Surveys*, mars 1991, pg. 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Cette fonction ajoute n **float** valeurs du vecteur de tableau `A`. Dans le corps de la boucle, l’algorithme calcule une valeur de « correction » qui est ensuite appliquée à l’étape suivante de la somme. Cette méthode réduit considérablement les erreurs d’arrondi cumulés par rapport à une somme simple tout en conservant la complexité d’o (n) fois.

Un compilateur C++ naïf peut supposer qu’arithmétique à virgule flottante suit les mêmes règles algébriques que l’arithmétique des nombres réels. Un tel compilateur peut ensuite à tort la conclusion que

> C = T - sum - Y ==> (sum+Y)-sum-Y ==> 0;

Autrement dit, que la valeur perçue de C est toujours un zéro constant. Si cette valeur constante est propagée aux expressions suivantes, le corps de boucle est réduit à une simple somme. Pour être précis,

> Y = A[i] - C ==> Y = A[i]<br/>T = sum + Y ==> T = sum + A[i]<br/>sum = T ==> sum = sum + A[i]

Par conséquent, pour le compilateur naïf, une transformation logique de la `KahanSum` fonction serait :

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Bien que l’algorithme transformé soit plus rapide, *il n’est pas du tout une représentation exacte de l’intention du programmeur*. La correction d’erreur élaborée avec soin a été entièrement supprimée et nous obtenons un algorithme de somme simple et direct, avec toutes les erreurs correspondantes.

Bien entendu, un compilateur C++ perfectionné saurait autrement algébriques règles de réel arithmétique ne généralement s’appliquent pas à l’arithmétique à virgule flottante. Toutefois, même un compilateur C++ peut-être interpréter toujours correctement l’intention du programmeur.

Prenons une optimisation classique qui tente d’intégrer autant de valeurs dans les registres que possible (appelé « enregistrement » une valeur). Dans le `KahanSum` exemple, cette optimisation peut tenter d’inscrire dans les variables `C`, `Y` et `T` dans la mesure où ils sont utilisés uniquement dans le corps de boucle. Si la précision de Registre s’élève à 52 bits (double) au lieu de 23 (unique), cette optimisation efficacement type promeut `C`, `Y` et `T` à taper **double**. Si la variable sum n’est pas de même inscrites dans le Registre, elle reste codée en simple précision. La sémantique de `KahanSum` à ce qui suit

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

Bien que `Y`, `T` et `C` soient désormais calculées à une précision plus élevée, ce nouveau codage peut produire un résultat moins précis en fonction des valeurs de `A[]`. Ainsi même apparemment inoffensifs optimisations peuvent avoir des conséquences négatives.

Ces types de problèmes d’optimisation ne sont pas limitées à code en virgule flottante « complexe ». Les algorithmes à virgule flottante même simples peuvent échouer lors de l’optimisation est incorrecte. Prenez en compte un simple algorithme de somme directe :

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Étant donné que certaines unités de virgule flottante sont capables d’exécuter plusieurs opérations simultanément, un compilateur peut opter pour une optimisation de la réduction scalaire. Cette optimisation transforme effectivement la simple fonction Sum ci-dessus dans les éléments suivants :

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

La fonction comporte désormais quatre sommes distinctes qui peuvent être traitées simultanément à chaque étape. Bien que la fonction optimisée est désormais beaucoup plus rapide, les résultats optimisés peuvent être tout à fait différents à partir des résultats non optimisés. Dans cette modification, le compilateur a supposé associative addition à virgule flottante. Autrement dit, que ces deux expressions sont équivalentes : `(a + b) + c == a + (b + c)`. Toutefois, associativité n’est pas toujours vrai pour les nombres à virgule flottante. Au lieu de calculer la somme en tant que :

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

la fonction transformée calcule le résultat en tant que

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

Pour certaines valeurs de `A[]`, cette différence dans l’ordre des opérations d’addition peut produire des résultats inattendus. Pour compliquer encore les choses, certains programmeurs choisissent d’anticiper ces optimisations et de les compenser en conséquence. Dans ce cas, un programme peut créer le tableau `A` dans un ordre différent afin que la somme optimisée produise les résultats escomptés. En outre, dans de nombreux cas, la précision des résultats optimisés peut être « suffisamment proche ». Cela est particulièrement vrai lorsque l’optimisation offre l’avantage de vitesse intéressant. Jeux vidéo, par exemple, requièrent accélérer autant que possible, mais ne nécessitent souvent des calculs en virgule flottante extrêmement précis. Les éditeurs de compilateurs doivent donc fournir un mécanisme pour les programmeurs contrôler les objectifs, souvent disparates de vitesse et la précision.

Certains compilateurs répondent au compromis vitesse et la précision en fournissant un commutateur distinct pour chaque type d’optimisation. Cela permet aux développeurs de désactiver les optimisations qui affectent la précision à virgule flottante pour une application particulière. Bien que cette solution offre un degré élevé de contrôle sur le compilateur, il présente plusieurs problèmes supplémentaires :

- Il est souvent difficile de savoir quels commutateurs pour activer ou désactiver.
- La désactivation d’une optimisation particulière peut nuire aux performances du code non à virgule flottante.
- Chaque commutateur supplémentaire multiple de nombreuses nouvelles combinaisons de commutateurs ; le nombre de combinaisons devenir difficile à gérer.

Par conséquent, des commutateurs distincts pour chaque optimisation semble intéressante, à l’aide de ces compilateurs peut être lourde et peu fiable.

Nombre de compilateurs C++ offre un *cohérence* modèle de virgule flottante (via un **/Op** ou **/fltconsistency** basculer) qui permet à un développeur à créer des programmes conformes avec une sémantique à virgule flottante stricte. Une fois activé, ce modèle empêche le compilateur à l’aide de la plupart des optimisations sur des calculs en virgule flottante tout en autorisant ces optimisations pour le code non-virgule flottante. Le modèle de cohérence, cependant, a son revers. Afin de retourner des résultats prévisibles sur différentes architectures FPU, presque toutes les implémentations de **/Op** round expressions intermédiaires à l’utilisateur spécifié de précision ; par exemple, considérez l’expression suivante :

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

Afin de produire des résultats cohérents et reproductibles sous **/Op**, cette expression est évaluée comme si elle était implémentée comme suit :

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

Le résultat final souffre maintenant d’erreurs d’arrondi simple précision *à chaque étape de l’évaluation de l’expression*. Bien que cette interprétation n’arrête strictement les règles de sémantique C++, il est presque jamais la meilleure façon d’évaluer des expressions en virgule flottante. Il est généralement plus judicieux de calcul intermédiaires entraîne aussi élevée que la précision possible. Par exemple, il serait préférable de calcul de l’expression `a = b * c + d * e` dans une précision plus élevée, comme dans

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

ou mieux encore

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

Lors du calcul des résultats intermédiaires avec une précision plus élevée, le résultat final est sensiblement plus précis. Ironiquement, en adoptant un modèle de cohérence, la probabilité d’erreur augmente précisément lorsque l’utilisateur tente de réduire les erreurs en désactivant les optimisations non sécurisées. Par conséquent, le modèle de cohérence peut réduire nettement l’efficacité sans garantir aucune amélioration de la précision. Pour les programmeurs numériques graves, cela ne semble pas un très bon compromis et est la raison principale que le modèle est généralement pas bien accepté.

Depuis la version 8.0 (Visual C++® 2005), Microsoft C++ compilateur fournit une solution plus adaptée. Il permet aux programmeurs de choisir un des trois modes à virgule flottante générales : mode fp : precise, fp : Fast et fp : strict.

- En mode fp : precise, uniquement sécurisant les optimisations du code en virgule flottante et, contrairement à **/Op**, calculs intermédiaires sont effectués de manière cohérente à la précision plus élevé possible.
- mode fp : Fast assouplit les règles à virgule flottante, permettant ainsi d’une optimisation au détriment de la précision.
- mode fp : strict mode fournit tous les aspects d’exactitude du mode fp : precise lors de l’activation de la sémantique d’exceptions de virgule flottante et en empêchant de transformation non autorisée en présence de modifications de l’environnement FPU (par exemple, les modifications apportées à la précision de Registre, etc. de direction d’arrondi).

Sémantique d’exceptions à virgule flottante peut être contrôlée indépendamment par un commutateur de ligne de commande ou un pragma de compilateur ; par défaut, la sémantique d’exceptions à virgule flottante est désactivée en mode fp : precise et activée en mode fp : strict. Le compilateur fournit également un contrôle sur l’environnement FPU et certaines optimisations à virgule flottante spécifiques, telles que les contractions. Ce modèle simple offre aux développeurs un grand contrôle sur la compilation du code en virgule flottante sans le fardeau de trop nombreux commutateurs du compilateur ou de la perspective d’effets secondaires indésirables.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Le mode fp : precise mode de sémantique en virgule flottante

Le mode de sémantique en virgule flottante par défaut est le mode fp : precise. Lorsque ce mode est sélectionné, le compilateur respecte strictement un ensemble de règles de sécurité lors de l’optimisation des opérations à virgule flottante. Ces règles permettent au compilateur de générer un code machine efficace tout en conservant la précision des calculs en virgule flottante. Pour faciliter la production de fast programmes, le mode fp : precise modèle désactive la sémantique d’exceptions à virgule flottante (bien qu’ils peuvent être explicitement activées). Microsoft a choisi le mode fp : precise comme le mode en virgule flottante par défaut car il crée des programmes à la fois rapides et précises.

Pour demander explicitement le mode fp : mode précision à l’aide du compilateur de ligne de commande, utilisez le [/fp : precise](fp-specify-floating-point-behavior.md) basculer :

> / de CL fp : precise source.cpp

Cela indique au compilateur d’utiliser le mode fp : precise sémantique lors de la génération de code pour le fichier source.cpp. Le mode fp : precise modèle peut également être appelé fonction par fonction à l’aide la [du pragma de compilateur float_control](#the-float-control-pragma).

Le mode fp : precise mode, le compilateur n’effectue aucune optimisation risquant de compromettre l’exactitude des calculs à virgule flottante. Le compilateur correctement les arrondis lors des affectations, des conversions de type et les appels de fonction, et les arrondis intermédiaires sont effectués de façon cohérente à la même précision que les registres FPU. Les optimisations sécurisées, telles que les contractions, sont activées par défaut. Sémantique d’exceptions et l’environnement FPU sont désactivées par défaut.

|mode fp : precise sémantique|Explication|
|-|-|
|Sémantique d’arrondi|Arrondi explicite lors des affectations, des conversions de type, et les appels de fonction. Les expressions intermédiaires sont évaluées au degré de précision de Registre.|
|Transformations algébriques|Respect strict de l’algèbre non associatif, non distributif des nombres de virgule flottante, sauf si une transformation systématiquement produisent les mêmes résultats.|
|Contractions|Autorisée par défaut. Pour plus d’informations, consultez la section [le pragma fp_contract](#the-fp-contract-pragma).|
|Ordre d’évaluation à virgule flottante|Le compilateur peut réorganiser l’évaluation des expressions en virgule flottante autant que les résultats finaux ne sont pas modifiées.|
|Accès à l’environnement FPU|Désactivé par défaut. Pour plus d’informations, consultez la section [le pragma fenv_access](#the-fenv-access-pragma). La précision par défaut et le mode d’arrondi est supposé.|
|Sémantique d’exceptions de virgule flottante|Désactivé par défaut. Pour plus d’informations, consultez [/fp : sauf](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Arrondi sémantique pour les expressions en virgule flottante en mode fp : precise

Le mode fp : precise modèle effectue toujours les calculs intermédiaires avec la précision plus élevé possible, en arrondissant explicitement et uniquement à certains points dans l’évaluation d’expression. Arrondi à la précision spécifiée par l’utilisateur toujours se produit en quatre endroits : (a) lorsqu’une affectation est effectuée, (b) lors d’une conversion de type, (c) lorsqu’une valeur à virgule flottante est passée en tant qu’argument à une fonction et (d) lorsqu’une valeur à virgule flottante est retournée à partir d’un fonction. Étant donné que les calculs intermédiaires sont toujours effectués avec précision de Registre, la précision des résultats intermédiaires dépend de la plateforme (bien que la précision sera toujours au moins aussi élevée que celle de l’utilisateur spécifié précision).

Examinons l’expression d’assignation dans le code suivant. L’expression sur le côté droit de l’assignation opérateur '=' sera calculée à la précision de Registre et puis arrondie explicitement en fonction du type de la partie gauche de l’assignation.

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

est calculée en tant que

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Pour arrondir explicitement un résultat intermédiaire, introduire une conversion de type. Par exemple, si le code précédent est modifié en ajoutant une conversion de type explicite, l’expression intermédiaire (c * d) est arrondie conformément au type de la conversion de type.

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

est calculée en tant que

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Une conséquence de cette méthode d’arrondi est que certaines transformations apparemment équivalentes ne présentent pas la même sémantique. Par exemple, la transformation présentée ci-dessous divise une seule expression d’assignation dans les deux expressions d’assignation.

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

n’est pas équivalent à

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

De même :

```cpp
a = b*(c+d);
```

n’est pas équivalent à

```cpp
a = b*(a=c+d);
```

Ces codages ne partagent pas de sémantique car le deuxième codage introduit une opération d’affectation supplémentaire et, par conséquent, un arrondi en plus de point.

Lorsqu’une fonction retourne une valeur à virgule flottante, la valeur est arrondie au type de la fonction. Lorsqu’une valeur à virgule flottante est passée en tant que paramètre à une fonction, la valeur est arrondie au type du paramètre. Exemple :

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

est calculée en tant que

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

De même :

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

est calculée en tant que

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>Arrondi spécifique de l’architecture mode fp : precise

|Processeur|Arrondi de précision pour les expressions intermédiaires|
|-|-|
|x86|Les expressions intermédiaires sont calculées à la précision de 53 bits par défaut avec une plage étendue fournie par un exposant de 16 bits. Lorsque ces valeurs 53:16 sont « dispersées » dans la mémoire (peut se produire lors d’un appel de fonction), la plage étendue exposant est réduite à 11 bits. Autrement dit, les valeurs dispersées sont converties au format standard de double précision avec uniquement un exposant de 11 bits.<br/>Un utilisateur peut basculer vers la précision étendue de 64 bits pour l’arrondi intermédiaire en modifiant le mot de contrôle à virgule flottante à l’aide `_controlfp` et en activant l’accès à l’environnement FPU (voir [le pragma fenv_access](#the-fenv-access-pragma)). Toutefois, lorsque les valeurs de Registre de précision étendue sont dispersées dans la mémoire, les résultats intermédiaires sont toujours arrondis à la double précision.<br/>Cette sémantique particulière est susceptible de changer.|
|amd64|La sémantique FP du processeur AMD64 est différente de celle d’autres plateformes. Pour des raisons de performances, les opérations intermédiaires sont calculées au degré de précision plus large de des opérandes au lieu de sur le degré de précision disponible.  Pour forcer les calculs à l’aide d’une précision plus grande que celle des opérandes, les utilisateurs doivent présenter une opération de conversion au moins un opérande d’une sous-expression.<br/>Cette sémantique particulière est susceptible de changer.|

### <a name="algebraic-transformations-under-fpprecise"></a>Transformations algébriques en mode fp : precise

Lorsque fp : precise mode est activé, le compilateur n’effectue jamais de transformations algébriques *, sauf si le résultat final est prouvée identique*. Grand nombre de règles algébriques courante arithmétique des nombres réels ne sont pas valables pour l’arithmétique à virgule flottante. Par exemple, les expressions suivantes sont équivalentes pour les nombres, mais pas nécessairement à virgule flottante.

|Formulaire|Description|
|-|-|
|`(a+b)+c = a+(b+c)`|Règle d’addition associative|
|`(a*b)*c = a*(b*c)`|Règle de multiplication associative|
|`a*(b+c) = a*b + b*c`|Distribution de la multiplication sur l’addition|
|`(a+b)(a-b) = a*a-b*b`|Mise en facteur algébrique|
|`a/b = a*(1/b)`|Division par l’inverse multiplicatif|
|`a*1.0 = a`|Identité multiplicative|

Comme illustré dans l’exemple avec la fonction `KahanSum`, le compilateur peut être tenté d’effectuer diverses transformations algébriques afin de produire des programmes nettement plus rapides. Bien que les optimisations dépendant de telles transformations algébriques soient presque toujours incorrectes, il existe des occasions pour lequel elles soient parfaitement sûres. Par exemple, il est parfois souhaitable de remplacer la division par un *constante* valeur et une multiplication par l’inverse multiplicatif de la constante :

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Peut être transformé en

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Il s’agit une transformation sûre car l’optimiseur peut déterminer au moment de la compilation que x / 4.0 == x*(1/4.0) pour toutes les valeurs à virgule flottante de x, y compris les valeurs infinies et NaN. En remplaçant une opération de division par une multiplication, le compilateur peut économiser plusieurs cycles, en particulier dans les environnements FPU qui n’implémente pas directement division mais ont besoin du compilateur pour générer une combinaison de réciproque / approximation et de multiplication / addition obtenir des instructions. Le compilateur peut effectuer cette optimisation en mode fp : precise uniquement lorsque la multiplication de remplacement produit exactement le même résultat que la division. Le compilateur peut également effectuer des transformations triviales en mode fp : precise à condition que les résultats sont identiques. Elles incluent notamment :

|Formulaire|Description
|-|-|
|`(a+b) == (b+a)`|Règle d’addition commutative|
|`(a*b) == (b*a)`|Règle de multiplication commutative|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Multiplication par 1.0|
|`x/1.0*y == x*y/1.0 == x*y`|Division par 1.0|
|`2.0*x == x+x`|Multiplication par 2.0|

### <a name="contractions-under-fpprecise"></a>Contractions en mode fp : precise

Une fonctionnalité architecturale essentielle de nombreuses unités de virgule flottante modernes est la possibilité d’effectuer une multiplication suivie d’une addition en une seule opération aucune erreur d’arrondi intermédiaire. Par exemple, l’architecture Itanium d’Intel fournit des instructions pour combiner chacune de ces opérations ternaires, (un*b + c), (un*b-c) et (c-a * b), dans une seule instruction à virgule flottante (respectivement, fma, fms et fnma respectivement). Ces instructions uniques sont plus rapides que l’exécution distincte instructions multiplication / addition et sont plus précises car il n’est pas d’arrondi intermédiaire du produit. Cette optimisation peut considérablement accélérer les fonctions contenant plusieurs entrelacés multiplier et ajouter des opérations. Par exemple, considérez l’algorithme ci-dessous qui calcule le produit scalaire de deux vecteurs de dimension n.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Ce calcul peut être effectué une série de multiplication / addition d’instructions au format p = p + x [i] * y [i].

L’optimisation de la contraction peut être contrôlée indépendamment à l’aide de la `fp_contract` du pragma de compilateur. Par défaut, le mode fp : precise modèle tient compte des contractions car celles-ci améliorent la précision et la vitesse. En mode fp : precise, le compilateur ne contracte jamais une expression contient un arrondi explicite.
Exemples

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Ordre d’évaluation d’expression à virgule flottante en mode fp : precise

Les optimisations qui conservent l’ordre d’évaluation d’expression à virgule flottante sont toujours sûres et sont donc autorisées fp : precise mode. Examinons la fonction ci-dessous qui calcule le produit scalaire de deux vecteurs de dimension n en simple précision. Le premier bloc de code ci-dessous est la fonction d’origine car elle pourrait être codée par un programmeur, suivie par la fonction même après une optimisation par développement boucle partielle.

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

Le principal avantage de cette optimisation est qu’il réduit le nombre de branchement conditionnel boucle 75 %. En outre, en augmentant le nombre d’opérations dans le corps de la boucle, le compilateur a davantage d’opportunités pour optimiser davantage. Par exemple, certains FPU peut-être être en mesure d’effectuer la multiplication / addition dans p += x [i] * y [i] tout en récupérant simultanément les valeurs de x [i + 1] et y [i + 1] pour une utilisation dans l’étape suivante. Ce type d’optimisation est parfaitement sûr pour les calculs en virgule flottante car il préserve l’ordre des opérations.

Il est souvent préférable pour le compilateur de réordonner des opérations complètes afin de produire du code plus rapide. Examinons le code ci-dessous.

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

Règles de sémantique C++ indiquent que le programme doit produire des résultats comme si elle portait d’abord x, puis y et enfin sur z. Supposons que le compilateur a seulement quatre registres en virgule flottante disponibles. Si le compilateur est forcé de calculer x, y et z dans l’ordre, il peut choisir de générer du code avec la sémantique suivante :

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

Il existe plusieurs opérations redondantes est cet encodage. Si le compilateur suit strictement les règles de sémantique C++, cet ordre est nécessaire car le programme peut accéder à l’environnement FPU entre chaque affectation. Toutefois, les paramètres par défaut pour le mode fp : precise permettent au compilateur d’optimisation comme si le programme n’accède pas à l’environnement, lui permettant de réordonner ces expressions. Il est alors libre de supprimer les redondances en calculant les trois valeurs dans l’ordre inverse, comme suit :

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

Cet encodage est donc bien plus efficace, avoir diminué de près de 40 % le nombre d’instructions-fp. Les résultats de x, y et z sont les mêmes qu’avant, calculée, mais avec moins de surcharge.

En mode fp : precise, le compilateur peut également *entrelacé* sous-expressions communes afin de produire du code plus rapide. Par exemple, le code de calcul des racines d’une équation bicarrée peut être écrit comme suit :

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

Bien que ces expressions ne diffèrent que par une seule opération, le programmeur peut avoir écrit cette façon afin de garantir que chaque valeur de racine soit calculée avec la précision plus élevé possible. En mode fp : precise, le compilateur est libre d’imbriquer le calcul de root0 et de root1 pour supprimer les sous-expressions communes sans perte de précision. Par exemple, les éléments suivants a supprimé plusieurs étapes redondantes tout en produisant la même réponse.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Autres optimisations peuvent tenter de déplacer l’évaluation de certaines expressions indépendantes. Examinons l’algorithme suivant qui contient une ramification conditionnelle dans un corps de la boucle.

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

Le compilateur peut détecter que la valeur de l’expression (ABS > 1) est invariante dans le corps de boucle. Cela permet au compilateur if « sortir » l’instruction en dehors du corps de boucle, en transformant le code ci-dessus en ce qui suit :

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

Après la transformation, il n’est plus une branche conditionnelle dans un des corps de boucle, ce qui améliore considérablement les performances globales de la boucle. Ce type d’optimisation est parfaitement sûr, car la version d’évaluation de l’expression (ABS > 1.0) est indépendante des autres expressions.

En présence d’accès à l’environnement FPU ou des exceptions de virgule flottante, ces types d’optimisations sont contre-indiqués car ils modifient le flux sémantique. Ces optimisations sont uniquement disponibles sous le mode fp : precise mode, car l’accès à l’environnement FPU et sémantique d’exceptions à virgule flottante est désactivée par défaut. Les fonctions qui accèdent à l’environnement FPU peuvent désactiver explicitement ces optimisations en utilisant le `fenv_access` du pragma de compilateur. De même, les fonctions à l’aide des exceptions de virgule flottante doivent utiliser le `float_control(except ... )` du pragma de compilateur (ou utilisez le **/fp : sauf** commutateur de ligne de commande).

En résumé, le mode fp : precise mode permet au compilateur de réorganiser l’évaluation d’expressions en virgule flottante à condition que le résultat final n’est pas modifié et que les résultats ne sont pas dépendants sur l’environnement FPU ou sur les exceptions de virgule flottante.

### <a name="fpu-environment-access-under-fpprecise"></a>Accès à l’environnement FPU en mode fp : precise

Lorsque le mode fp : precise mode est activé, le compilateur suppose qu’un programme ne pas accéder ou modifier l’environnement FPU. Comme indiqué précédemment, cette hypothèse permet au compilateur de réorganiser ou de déplacer des opérations à virgule flottante pour améliorer l’efficacité en mode fp : precise.

Certains programmes peuvent modifier la direction d’arrondi à virgule flottante à l’aide de la `_controlfp` (fonction). Par exemple, certains programmes calculent supérieure et inférieure limites d’erreur pour les opérations arithmétiques en effectuant le même calcul à deux reprises, tout d’abord en arrondissant à l’infini négatif, en arrondissant à l’infini positif. Étant donné que le FPU offre un moyen pratique de contrôle des arrondis, un programmeur peut choisir de changer de mode d’arrondi en modifiant l’environnement FPU. Le code suivant calcule la que limite d’une erreur exacte d’une multiplication à virgule flottante en modifiant l’environnement FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

En mode fp : precise, le compilateur suppose toujours l’environnement FPU par défaut, par conséquent, l’optimiseur est libre d’ignorer les appels à `_controlfp` et réduire les affectations ci-dessus à cUpper = cLower = un * b ; cela produirait indéniablement des résultats incorrects. Pour empêcher ces optimisations, activez les accès à l’environnement FPU à l’aide de la `fenv_access` du pragma de compilateur.

Autres programmes peuvent tenter de détecter certaines erreurs à virgule flottante en vérifiant le mot d’état du FPU. Par exemple, le code suivant vérifie les conditions de division par zéro ou d’inexactitude

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

En mode fp : precise, les optimisations permettant de réorganiser l’évaluation de l’expression peuvent modifier les points à laquelle certaines erreurs se produisent. Le mot d’état de l’accès à des programmes doivent activer l’accès à l’environnement FPU à l’aide de la `fenv_access` du pragma de compilateur.

Pour plus d’informations, consultez la section [le pragma fenv_access](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>La sémantique d’exceptions à virgule flottante en mode fp : precise

Par défaut, la sémantique d’exceptions à virgule flottante est désactivée en mode fp : precise. La plupart des programmeurs C++ préfèrent gérer des conditions exceptionnelles à virgule flottante sans utiliser le système ou des exceptions C++. En outre, comme indiqué précédemment, la désactivation de la sémantique d’exceptions à virgule flottante permet le compilateur plus de souplesse lors de l’optimisation des opérations à virgule flottante. Utiliser le **/fp : à l’exception** basculer ou `float_control` pragma pour activer la sémantique d’exception de virgule flottante lorsque vous utilisez le mode fp : modèle précis.

Pour plus d’informations, consultez la section [activation de la sémantique d’exception de virgule flottante](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>Le mode fp : Fast pour la sémantique en virgule flottante

Lorsque le mode fp : fast est activé, le compilateur assouplit les règles mode fp : precise lors de l’optimisation des opérations à virgule flottante. Ce mode est permet au compilateur d’optimiser davantage le code en virgule flottante de vitesse aux dépens de sa précision et l’exactitude. Les programmes qui ne reposent pas sur des calculs en virgule flottante extrêmement précis peuvent rencontrer une amélioration significative de la vitesse en activant le mode fp : fast.

Le mode en virgule flottante fp : fast est activé à l’aide de la [Fast](fp-specify-floating-point-behavior.md) commutateur de compilateur de ligne de commande comme suit :

> cl /fp:fast source.cpp

Cet exemple indique au compilateur d’utiliser la sémantique fp : Fast lors de la génération de code pour le fichier source.cpp. Le modèle fp : fast peut également être appelé fonction par fonction à l’aide du `float_control` du pragma de compilateur.

Pour plus d’informations, consultez la section [le pragma float_control](#the-float-control-pragma).

En mode fp : fast, le compilateur peut effectuer des optimisations qui affectent l’exactitude des calculs en virgule flottante. Le compilateur ne peut pas correctement les arrondis lors des affectations, des conversions de type ou d’appels de fonction, et d’arrondi intermédiaire ne sera pas toujours effectué. Les optimisations spécifiques à virgule flottante, telles que les contractions, sont toujours activées. Sémantique d’exceptions à virgule flottante et l’environnement FPU sont désactivées et non disponibles.

|sémantique fp : Fast|Explication
|-|-|
|Sémantique d’arrondi|Arrondi explicite lors des affectations, des conversions de type, et les appels de fonction peuvent être ignorés.<br/>Les expressions intermédiaires peuvent être arrondies à un prix inférieur à celui des registres de précision en fonction des exigences de performances.|
|Transformations algébriques|Le compilateur peut transformer les expressions selon l’algèbre associatif et distributif de nombres réels ; Ces transformations ne sont pas garanties pour être exactes ou correctes.|
|Contractions|Toujours activée ; ne peut pas être désactivée par le pragma `fp_contract`|
|Ordre d’évaluation à virgule flottante|Le compilateur peut réorganiser l’évaluation des expressions en virgule flottante, même lorsque ces modifications peuvent modifier les résultats finaux.|
|Accès à l’environnement FPU|Désactivé. Non disponible|
|Sémantique d’exceptions de virgule flottante|Désactivé. Non disponible|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Sémantique des expressions à virgule flottante sous le mode fp : Fast d’arrondi

Contrairement à la mode fp : precise modèle, le modèle fp : fast effectue des calculs intermédiaires précision au plus pratique. Arrondi lors des affectations, des conversions de type et des appels de fonction ne sont pas toujours appliqués. Par exemple, la première fonction ci-dessous introduit trois variables en simple précision (`C`, `Y` et `T`). Le compilateur peut choisir d’inscrire ces variables, en vigueur de la promotion de type `C`, `Y` et `T` à double précision.

Fonction d’origine :

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Variables inscrites dans le Registre :

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

Dans cet exemple, le mode fp : Fast a bouleversé l’intention de la fonction d’origine. Le résultat final optimisé, contenu dans la variable `sum`, peut être assez différent du résultat correct.

Sous mode fp : fast, le compilateur tente généralement conserver au moins la précision spécifiée par le code source. Toutefois, dans certains cas, le compilateur peut choisir effectuer des expressions intermédiaires à un *diminuer la précision* que le nombre spécifié dans le code source. Par exemple, le premier bloc de code ci-dessous appelle une version en double précision de la fonction racine carrée. Sous mode fp : fast, dans certaines circonstances, par exemple lorsque le résultat et les opérandes de la fonction sont explicitement converties en simple précision, le compilateur peut choisir de remplacer l’appel à la double précision `sqrt` avec un appel à une simple précision `sqrtf`(fonction). Étant donné que les casts de garantir que la valeur aborder `sqrt` et la valeur sortantes sont arrondies à simple précision, cela modifie uniquement l’emplacement de l’arrondi. Si la valeur arrivant dans sqrt était une valeur double précision et le compilateur a effectué cette transformation, comme la moitié des bits de précision peut être incorrecte.

Fonction d’origine

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

Fonction optimisée

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

Bien que moins précise, cette optimisation peut être particulièrement utile lors du ciblage de processeurs fournissant des versions intrinsèques de fonctions simple précision comme `sqrt`. Moment précis lorsque le compilateur utilise ces optimisations dépend de la plate-forme et du contexte.

En outre, n’est pas garanti cohérent pour la précision des calculs intermédiaires, qui peuvent être effectués avec n’importe quel niveau de précision accessible au compilateur. Bien que le compilateur tente de conserver au moins le niveau de précision spécifiée par le code, mode fp : fast permet à l’optimiseur à effectuer un downcast calculs intermédiaires afin de produire le code machine plus rapide ou plus petits. Par exemple, le compilateur peut renforcer l’optimisation du code ci-dessus pour arrondir en simple précision les résultats de multiplications intermédiaires.

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

Ce type d’arrondi supplémentaires peut-être provenir d’à l’aide d’une plus faible précision unité de virgule flottante, telle que SSE2, pour effectuer certains calculs intermédiaires. La précision de l’arrondi du mode fp : fast est donc dépendante de la plateforme ; code se compile correctement pour un seul processeur ne peut pas nécessairement fonctionnent bien pour un autre processeur. Il incombe à l’utilisateur pour déterminer si les avantages de vitesse compensent les éventuels problèmes de précision.

Si l’optimisation de mode fp : fast est particulièrement problématique pour une fonction spécifique, le mode en virgule flottante permettre faire basculer localement fp : precise à l’aide du `float_control` du pragma de compilateur.

### <a name="algebraic-transformations-under-fpfast"></a>Transformations algébriques sous le mode fp : Fast

Le mode fp : fast permet au compilateur d’appliquer certaines transformations algébriques non fiables virgule flottante des expressions en virgule. Par exemple, les optimisations non fiables ci-dessous peuvent être utilisées en mode fp : fast.

||||
|-|-|-|
|Code d’origine|Étape #1|Étape #2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

À l’étape 1, le compilateur observe que `z = y – a – b` est toujours égale à zéro. Bien que cela soit techniquement une observation non valide, elle est autorisée en mode fp : fast. Le compilateur propage ensuite la valeur de constante zéro à chaque utilisation suivante de la variable z. À l’étape 2, le compilateur continue à optimiser en observant que `x - 0 == x`, `x * 0 == 0`, etc. Là encore, même si ces observations ne sont pas strictement valables, elles sont autorisées en mode fp : fast. Le code optimisé est désormais beaucoup plus rapide, mais peut également être nettement moins précis ou voire incorrect.

Les règles algébriques (non fiables) suivantes peuvent être employées par l’optimiseur lorsque le mode fp : fast est activé :

|||
|-|-|
|Formulaire|Description|
|`(a + b) + c = a + (b + c)`|Règle d’addition associative|
|`(a * b) * c = a * (b * c)`|Règle de multiplication associative|
|`a * (b + c) = a * b + b * c`|Distribution de la multiplication sur l’addition|
|`(a + b)(a - b) = a * a - b * b`|Mise en facteur algébrique|
|`a / b = a * (1 / b)`|Division par l’inverse multiplicatif|
|`a * 1.0 = a, a / 1.0 = a`|Identité multiplicative|
|`a ± 0.0 = a, 0.0 - a = -a`|Identité additive|
|`a / a = 1.0, a - a = 0.0`|Annulation|

Si l’optimisation de mode fp : fast est particulièrement problématique pour une fonction particulière, le mode en virgule flottante permettre faire basculer localement fp : precise à l’aide du `float_control` du pragma de compilateur.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Ordre d’évaluation d’expression à virgule flottante sous le mode fp : Fast

Contrairement au mode fp : precise, fp : fast permet au compilateur de réorganiser les opérations à virgule flottante afin de produire du code plus rapide. Par conséquent, certaines optimisations en mode fp : fast peut ne pas conservent l’ordre prévu d’expressions. Par exemple, considérez la fonction suivante qui calcule le produit scalaire de deux vecteurs de dimension n.

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Sous mode fp : fast, l’optimiseur peut effectuer une réduction scalaire de la `dotProduct` fonction transformant comme suit :

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

Dans la version optimisée de la fonction quatre sommes distinctes produit simultanément et sont ensuite ajoutés ensemble. Cette optimisation peut accélérer le calcul de la `dotProduct` par autant comme un facteur de quatre, en fonction du processeur cible, mais le résultat final peut être tellement imprécis que rendre inutilisable. Si ces optimisations sont avèrent particulièrement problématiques pour une fonction ou une unité de traduction, le mode en virgule flottante permettre faire basculer localement fp : precise à l’aide du `float_control` du pragma de compilateur.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Le mode fp : strict mode de sémantique en virgule flottante

Lorsque le mode fp : mode strict est activé, le compilateur respecte toutes les règles mode fp : precise lors de l’optimisation des opérations à virgule flottante. Également, ce mode permet la sémantique d’exceptions à virgule flottante et la sensibilité à l’environnement FPU et désactive certaines optimisations telles que les contractions. Il est le mode de fonctionnement le plus strict.

Fp : strict mode en virgule flottante est activé à l’aide de la [/fp : strict](fp-specify-floating-point-behavior.md) commutateur de compilateur de ligne de commande comme suit :

> / de CL fp : strict source.cpp

Cet exemple indique au compilateur d’utiliser le mode fp : stricte sémantique lors de la génération de code pour le fichier source.cpp. Le mode fp : strict modèle peut également être appelé fonction par fonction à l’aide du `float_control` du pragma de compilateur.

Pour plus d’informations, consultez la section [le pragma float_control](#the-float-control-pragma).

Fp : mode strict, le compilateur n’effectue aucune optimisation risquant de compromettre l’exactitude des calculs à virgule flottante. Le compilateur correctement les arrondis lors des affectations, des conversions de type et les appels de fonction, et les arrondis intermédiaires sont effectués de façon cohérente à la même précision que les registres FPU. Sémantique d’exceptions à virgule flottante et l’environnement FPU sont activées par défaut. Certaines optimisations, telles que les contractions, sont désactivées, car le compilateur ne peut pas garantir l’exactitude dans tous les cas.

|mode fp : stricte sémantique|Explication|
|-|-|
|Sémantique d’arrondi|Arrondi explicite lors des affectations, des conversions de type et les appels de fonction<br/>Les expressions intermédiaires sont évaluées au degré de précision de Registre.<br/>Identique au mode fp : precise|
|Transformations algébriques|Respect strict de l’algèbre non associatif, non distributif des nombres de virgule flottante, sauf si une transformation systématiquement produisent les mêmes résultats.<br/>Identique au mode fp : precise|
|Contractions|Toujours désactivé|
|Ordre d’évaluation à virgule flottante|Le compilateur ne réorganise pas l’évaluation des expressions à virgule flottante|
|Accès à l’environnement FPU|Toujours activé.|
|Sémantique d’exceptions de virgule flottante|Activé par défaut.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>La sémantique d’exceptions à virgule flottante en mode fp : strict

Par défaut, la sémantique d’exceptions à virgule flottante est activée fp : strict modèle. Pour désactiver cette sémantique, utilisez le **/fp : à l’exception de-** basculer ou d’introduire un `float_control(except, off)` pragma.

Pour plus d’informations, consultez les sections [activation de la sémantique d’exception de virgule flottante](#enabling-floating-point-exception-semantics) et [Pragma float_control](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>Le pragma fenv_access

Utilisation :

```cpp
#pragma fenv_access( [ on  | off ] )
```

Le [fenv_access](../../preprocessor/fenv-access.md) pragma permet au compilateur d’apporter certaines optimisations pouvant perturber les tests d’indicateur FPU et les changements de mode FPU. Lorsque l’état de `fenv_access` est désactivé, le compilateur peut prendre les modes FPU par défaut sont appliquées et que les indicateurs FPU ne sont pas testés. Par défaut, l’accès à l’environnement est désactivé pour le mode fp : precise mode, même si elle peut être explicitement activée à l’aide de ce pragma. En mode fp : strict, `fenv_access` est toujours activée et ne peut pas être désactivée. Sous mode fp : fast, `fenv_access` est toujours désactivé et ne peut pas être activée.

Comme décrit dans le mode fp : precise section, certains programmeurs peuvent modifier la direction d’arrondi à virgule flottante à l’aide du `_controlfp` (fonction). Par exemple, pour calculer les limites d’erreur supérieures et inférieures pour les opérations arithmétiques, certains programmes effectuent le même calcul à deux reprises, tout d’abord en arrondissant à l’infini négatif, puis en arrondissant à l’infini positif. Étant donné que le FPU offre un moyen pratique de contrôle des arrondis, un programmeur peut choisir de changer de mode d’arrondi en modifiant l’environnement FPU. Le code suivant calcule la que limite d’une erreur exacte d’une multiplication à virgule flottante en modifiant l’environnement FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Lorsque désactivé, le `fenv_access` pragma permet au compilateur de supposer l’environnement FPU par défaut ; par conséquent, l’optimiseur est libre d’ignorer les appels à `_controlfp` et réduire les affectations ci-dessus à `cUpper = cLower = a*b`. Lorsque activé, toutefois, `fenv_access` empêche ces optimisations.

Les programmes peuvent également vérifier le mot d’état FPU pour détecter certaines erreurs liées à virgule flottante. Par exemple, le code suivant vérifie les conditions de division par zéro ou d’inexactitude

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

Lorsque `fenv_access` est désactivé, le compilateur peut réorganiser l’ordre d’exécution des expressions à virgule flottante, compromettant probablement ainsi les vérifications d’état FPU. L’activation `fenv_access` empêche ces optimisations.

## <a name="the-fpcontract-pragma"></a>Le pragma fp_contract

Utilisation :

```cpp
#pragma fp_contract( [ on | off ] )
```

Comme décrit dans le mode fp : precise section contraction est une fonctionnalité architecturale essentielle pour le nombre d’unités de virgule flottante moderne. Contractions vous permettent d’effectuer une multiplication suivie d’une addition en une seule opération aucune erreur d’arrondi intermédiaire. Ces instructions uniques sont plus rapides que l’exécution distincte instructions multiplication / addition et sont plus précises car il n’est pas d’arrondi intermédiaire du produit. Une opération contractée permet de calculer la valeur de `(a*b+c)` comme si les deux opérations ont été calculées avec une précision infinie et ensuite arrondies à la plus proche du nombre à virgule flottante. Cette optimisation peut considérablement accélérer les fonctions contenant plusieurs entrelacés multiplier et ajouter des opérations. Par exemple, considérez l’algorithme ci-dessous qui calcule le produit scalaire de deux vecteurs de dimension n.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Ce calcul peut être effectué une série de multiplication / addition d’instructions du formulaire `p = p + x[i]*y[i]`.

Le [fp_contract](../../preprocessor/fp-contract.md) pragma Spécifie si les expressions en virgule flottante peuvent être contractées. Par défaut, le mode fp : precise mode tient compte des contractions car celles-ci améliorent la précision et la vitesse. Contractions sont toujours activées pour le mode fp : fast. Toutefois, étant donné que les contractions peuvent compromettre la détection explicite des conditions d’erreur, le `fp_contract` pragma est toujours désactivé fp : mode strict. Exemples d’expressions pouvant être contractées lorsque le `fp_contract` pragma est activé :

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>Le pragma float_control

Le **/fp : precise**, **Fast**, **/fp : strict** et **/fp : sauf** commutateurs contrôlent la sémantique en virgule flottante fichier par fichier base. Le [float_control](../../preprocessor/float-control.md) pragma offre un contrôle fonction par fonction.

Utilisation :

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Les pragmas `float_control(push)` et `float_control(pop)` respectivement push et pop l’état actuel du mode en virgule flottante et l’option d’exception dans une pile. Notez que l’état de la `fenv_access` et `fp_contract` n’est pas affecté par `pragma float_control(push/pop)`.

Appel du pragma `float_control(precise, on)` activera et `float_control(precise, off)` désactivera la sémantique du mode de précision. De même, le pragma `float_control(except, on)` activera et `float_control(except, off)` désactivera la sémantique d’exceptions. Sémantique d’exceptions ne peut être activée que lors de la sémantique de précision est également activée. Lorsque facultatif `push` argument est présent, les États de la `float_control` options sont envoyées avant le changement de sémantique.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Définition du mode de sémantique à virgule flottante fonction par fonction

Les commutateurs de ligne de commande sont en fait des raccourcis permettant de configurer les quatre pragmas en virgule flottante. Pour choisir explicitement un mode de sémantique à virgule flottante particulier fonction par fonction, sélectionnez chacun des quatre pragmas en virgule flottante comme décrit dans le tableau suivant :

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/fp:strict|sur|sur|Hors tension|sur|
|/fp:strict /fp:except-|sur|Hors tension|Hors tension|sur|
|/fp:precise|sur|Hors tension|sur|Hors tension|
|/fp:precise /fp:except|sur|sur|sur|Hors tension|
|/fp:fast|Hors tension|Hors tension|sur|Hors tension|

Par exemple, le code ci-dessous Active explicitement la sémantique fp : fast.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> Sémantique d’exceptions doit être désactivée avant de désactiver la sémantique de « précision ».

## <a name="enabling-floating-point-exception-semantics"></a>Activation de la sémantique d’exception de virgule flottante

Certaines conditions exceptionnelles à virgule flottante, telles que la division par zéro, peuvent provoquer une exception matérielle le FPU. Exceptions de virgule flottante sont désactivées par défaut. Exceptions de virgule flottante sont activées en modifiant le mot de contrôle FPU avec la `_controlfp` (fonction). Par exemple, le code suivant permet à l’exception de virgule flottante de division par zéro :

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Lorsque l’exception de division par zéro est activée, toute opération de division avec un dénominateur égal à zéro entraîne une exception FPU soit signalé.

Pour rétablir le mot de contrôle FPU en mode par défaut, appelez `_controlfp(_CW_DEFAULT, ~0)`.

Activation de la sémantique d’exception de virgule flottante avec la **/fp : sauf** indicateur n’est pas identique à l’activation des exceptions de virgule flottante. Lors de la sémantique d’exception de virgule flottante est activée, le compilateur doit tenir compte de la possibilité que toutes les opérations à virgule flottante peuvent lever une exception. Étant donné que le FPU est une unité de processeur distincte, les instructions s’exécutant sur le FPU peuvent être effectuées en même temps que des instructions sur d’autres unités.

Quand une exception de virgule flottante est activée, le FPU arrêtera l’exécution de l’instruction fautive et signale ensuite une condition exceptionnelle en définissant le mot d’état FPU. Lorsque le CPU atteint la prochaine instruction à virgule flottante, il vérifie d’abord toutes les exceptions FPU en attente. S’il existe une exception en attente, le processeur les détecte en appelant un gestionnaire d’exceptions fourni par le système d’exploitation. Cela signifie que lorsqu’une opération à virgule flottante rencontre une condition exceptionnelle, l’exception correspondante ne sera pas détectée jusqu'à ce que l’opération à virgule flottante suivante est exécutée. Par exemple, le code suivant intercepte une exception de division par zéro :

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

Si une condition de division par zéro se produit dans l’expression une = b/c, le FPU/lève l’exception jusqu'à la prochaine opération à virgule flottante dans l’expression 2.0 * b. Il en résulte dans la sortie suivante :

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Le printf correspondant à la première ligne de la sortie ne doit pas dû être atteinte ; elle a été atteinte car l’exception à virgule flottante provoquée par l’expression b/c n’a pas été déclenchée jusqu'à ce que l’exécution atteint 2.0 * b. Pour lever l’exception juste après l’exécution de b/c, le compilateur doit introduire une instruction « attendre » :

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

Cette instruction « attendre » force le processeur à synchroniser avec l’état du FPU et à gérer les exceptions en attente. Le compilateur génère uniquement ces instructions « attendre » lors de la sémantique en virgule flottante est activée. Lorsque cette sémantique est désactivée, qu’il y a par défaut, programmes peuvent rencontrer des erreurs de synchronisme, similaires à celui illustré ci-dessus, lors de l’utilisation des exceptions de virgule flottante.

Lors de la sémantique en virgule flottante est activée, le compilateur n’introduira pas uniquement des instructions « wait », il sera également empêcher le compilateur optimisation illégalement du code à virgule flottante en présence d’exceptions possibles. Cela inclut toutes les transformations qui modifient les points où les exceptions sont levées. En raison de ces facteurs, activation de la sémantique en virgule flottante peut réduire considérablement l’efficacité du code machine généré et donc nuire aux performances d’une application.

Sémantique d’exceptions à virgule flottante est activée par défaut le mode fp : mode strict. Pour activer cette sémantique dans le mode fp : mode précision, ajoutez le **/fp : sauf** basculer vers le compilateur de ligne de commande. Sémantique d’exceptions à virgule flottante peut également être activée et désactivée fonction par fonction à l’aide du `float_control` pragma.

### <a name="floating-point-exceptions-as-c-exceptions"></a>Exceptions de virgule flottante en tant qu’exceptions C++

En tant qu’avec toutes les exceptions de matériel, exceptions de virgule flottante ne provoquent pas intrinsèquement une exception C++ mais déclenchent une exception structurée. Pour mapper des exceptions à virgule flottante structurées sur des exceptions C++, les utilisateurs peuvent introduire un traducteur d’exceptions SEH personnalisé. Commencez par introduire une exception C++ correspondant à chaque exception de virgule flottante :

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

Introduisez ensuite une fonction de traduction qui détecte une exception de virgule flottante SEH et lever l’exception C++ correspondante. Pour utiliser cette fonction, définissez le traducteur du Gestionnaire d’exceptions structurées pour le thread de processus actuel avec le [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) fonction à partir de la bibliothèque runtime.

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

Une fois ce mappage est initialisé, les exceptions de virgule flottante seront comportent comme si elles étaient des exceptions C++. Exemple :

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>Références

[Ce que chaque authentique scientifique doit-elle savoir sur arithmétique à virgule flottante](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) par David Goldberg.

## <a name="see-also"></a>Voir aussi

[Optimisation du code](../optimizing-your-code.md)<br/>
