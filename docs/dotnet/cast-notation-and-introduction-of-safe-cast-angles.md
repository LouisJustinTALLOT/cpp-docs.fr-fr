---
title: Notation castée et Introduction de safe_cast&lt; &gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427861"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notation castée et Introduction de safe_cast&lt;&gt;

La notation de cast a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Modification d’une structure existante est une expérience différente et plus difficile que l’élaboration de la structure initiale. Il y a moins de degrés de liberté et la solution tend à un compromis entre une restructuration idéale et ce que possible étant donné les dépendances structurelles existantes.

Extension de langage est un autre exemple. Au début des années 1990 l’orientation des objets de programmation est devenu un véritable paradigme, la nécessité d’une fonctionnalité de cast aval de type sécurisé en C++ sont devenus en appuyant sur. Cast est la conversion explicite de l’utilisateur d’un pointeur de classe de base ou une référence à un pointeur ou une classe dérivée. Le cast aval requiert un cast explicite. La raison est que le type réel du pointeur de classe de base est un aspect de l’exécution ; le compilateur par conséquent ne peut pas vérifier cela. Ou, autrement dit, une fonctionnalité de cast aval, tout comme un appel de fonction virtuelle, nécessite une forme de résolution dynamique. Cela soulève deux questions :

- Pourquoi ne pourrait-on pas nécessaire dans le paradigme orienté objet ? N’est pas le mécanisme de fonction virtuelle suffisante ? Autrement dit, pourquoi ne pas considérer que toute nécessité un cast aval (ou un cast quelconque) est une erreur de conception ?

- Pourquoi la prise en charge d’un cast aval doit être un problème en C++ ? Après tout, il n’est pas un problème dans les langages orientés objet tels que Smalltalk (ou par la suite, Java et c#) ? Qu’il est sur C++ qui rend donc compliquer de prise en charge ?

Une fonction virtuelle représente un algorithme dépendant du type commun à une famille de types. (Nous envisageons pas interfaces, qui ne sont pas pris en charge dans la norme ISO C++, mais sont disponible dans la programmation CLR et qui représentent une alternative de conception intéressante). La conception de cette famille est généralement représentée par une hiérarchie de classe dans laquelle il est une classe de base abstraite déclarant l’interface commune (les fonctions virtuelles) et un ensemble de classes dérivées concrètes qui représentent les types réels de famille dans l’application domaine.

Un `Light` hiérarchie dans un domaine d’application IMAGERIE générée par ordinateur (CGI), par exemple, aura des attributs communs tels que `color`, `intensity`, `position`, `on`, `off`, et ainsi de suite. Un peut contrôler plusieurs lumières, à l’aide de l’interface commune sans se préoccuper si une lumière, en particulier est un projecteur, une lumière directionnelle, une lumière non directionnelle (pensez au soleil) ou peut-être une lumière de porte dérobée obturateur. Dans ce cas, un cast en un type de lumière particulier afin d’exercer son interface virtuelle n’est pas nécessaire. Toutefois, dans un environnement de production, vitesse est essentielle. Un peut effectuer un downcast et appeler explicitement chaque méthode si, en raison de l’exécution inline des appels peut donc être exécutée au lieu d’utiliser le mécanisme virtuel.

Par conséquent, une des raisons pour effectuer un downcast dans C++ consiste à supprimer le mécanisme virtuel en contrepartie d’un gain significatif de performances d’exécution. (Notez que l’automatisation de cette optimisation manuelle est une zone de recherche active. Toutefois, il est plus difficile à résoudre que de remplacer l’utilisation explicite de la `register` ou `inline` mot clé.)

Une deuxième raison pour effectuer un downcast se situe en dehors de la nature double du polymorphisme. Une façon de considérer le polymorphisme est en cours divisée en une paire de formes, passive et dynamique.

Un appel virtuel (et une fonctionnalité de cast aval) constitue une utilisation dynamique de polymorphisme : un effectue une action basée sur le type réel du pointeur de classe de base à cette instance particulière dans l’exécution du programme.

Assignation d’un objet de classe dérivée pour son pointeur de classe de base, toutefois, est une forme passive de polymorphisme ; Il utilise le polymorphisme comme mécanisme de transport. C’est l’utilisation principale de `Object`, par exemple, dans la programmation de CLR préalable générique. Lorsqu’il est utilisé passivement, le pointeur de la classe de base choisi pour le transport et de stockage en général, offre une interface qui est trop abstraite. `Object`, par exemple, fournit à peu près cinq méthodes via son interface ; tout comportement plus spécifique requiert explicite cast aval. Par exemple, si nous souhaitons régler l’angle de notre projecteur ou son taux de diminution, il faut effectuer un downcast explicitement. Une interface virtuelle au sein d’une famille de sous-types ne peut pas être pratiquement un sur-ensemble de toutes les méthodes possibles de ses nombreux enfants, et par conséquent, une fonctionnalité de cast aval est toujours nécessaires au sein d’un langage orienté objet.

Si un cast aval sécurisé fonctionnalité est nécessaire dans un langage orienté objet, alors pourquoi a-t-il fallu C++ autant en ajouter un ? Le problème réside dans la manière de rendre les informations concernant le type au moment de l’exécution du pointeur disponible. Dans le cas d’une fonction virtuelle, les informations d’exécution sont définies en deux parties par le compilateur :

- L’objet de classe contient un membre de pointeur de table virtuelle supplémentaire (au début ou fin de l’objet de classe ; c’est l’a un historique intéressant en soi) qui traite la table virtuelle appropriée. Par exemple, un objet projecteur adresse une table virtuelle spotlight, une lumière directionnelle, une table virtuelle de lumière directionnelle, etc.

- Chaque fonction virtuelle est associé à un emplacement dans le tableau fixe, et l’instance réelle à appeler est représenté par l’adresse stockée dans la table. Par exemple, le serveur virtuel `Light` destructeur peut-être être associé à l’emplacement 0, `Color` avec emplacement 1 et ainsi de suite. Il s’agit d’une stratégie efficace si peu flexibles, car il est configuré au moment de la compilation et représente une surcharge minimale.

Le problème, alors, est de rendre les informations de type disponibles au pointeur sans modifier la taille des pointeurs C++, en ajoutant une deuxième adresse ou en ajoutant directement une sorte de type de codage. Cela ne serait pas acceptable pour les programmeurs (et programmes) qui décidez de ne pas utiliser le paradigme orienté objet - était encore la Communauté des utilisateurs prédominante. Une autre possibilité consistait à introduire un pointeur spécial pour les types de classe polymorphe, mais cela serait prêter à confusion et rendre difficile la combinaison des deux, en particulier des problèmes de l’opération arithmétique de pointeur. Il également serait acceptable de conserver une table d’exécution qui associe chaque pointeur à son type actuellement associé et que la mise à jour dynamique.

Le problème est ensuite une paire de communautés d’utilisateurs qui ont les aspirations de programmation différentes mais légitimes. La solution doit être un compromis entre les deux groupes, permettant à chacun non seulement leur aspiration, mais la possibilité d’interagir. Cela signifie que les solutions proposées par les deux côtés sont susceptibles d’être irréalisable et que la solution implémentée enfin être inférieure à parfaite. La résolution réelle tourne autour de la définition d’une classe polymorphe : une classe polymorphe est une qui contient une fonction virtuelle. Une classe polymorphe prend en charge une dynamique de type sécurisé cast aval. Cette action a résolu le problème de tenir à jour-the--comme-adresse du pointeur, car toutes les classes polymorphes contiennent ce membre pointeur supplémentaire à leur table virtuelle associée. Les informations de type associé, par conséquent, peuvent être stockées dans une structure de table virtuelle développée. Le coût de l’effectuer un downcast de type sécurisé est (presque) que les utilisateurs de l’installation.

Le problème suivant avec le cast aval de type sécurisé était sa syntaxe. S’agissant d’un cast, la proposition d’origine au comité ISO-C++ utilisé la syntaxe de cast sans ornement, comme dans cet exemple :

```
spot = ( SpotLight* ) plight;
```

mais cela a été rejeté par le comité, car il n’a pas permis l’utilisateur de contrôler le coût du cast. Si la dynamique de type sécurisé effectuer un downcast a la même syntaxe que précédemment unsafe mais statique notation de cast, il devient alors une substitution, et l’utilisateur ne dispose d’aucune possibilité de supprimer la surcharge d’exécution lorsqu’il est inutile, voire trop coûteux.

En général, en C++, il existe toujours un mécanisme permettant de supprimer des fonctionnalités prises en charge du compilateur. Par exemple, nous pouvons désactiver le mécanisme virtuel en utilisant l’opérateur de portée de classe (`Box::rotate(angle)`) ou en appelant la méthode virtuelle via un objet de classe (plutôt que d’un pointeur ou référence de cette classe). Cette dernière suppression n’est pas requis par le langage, mais est une qualité de problème d’implémentation, semblable à la suppression de la construction d’une table temporaire dans une déclaration de la forme :

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

Pour que la proposition a été effectuée pour un examen complémentaire et plusieurs autres notations, et l’affiche de nouveau le comité était sous la forme (`?type`), qui indiqué son indéterminé - autrement dit, la nature dynamique. Celle-ci permettait à l’utilisateur la possibilité de basculer entre les deux formes - statiques ou dynamiques - mais aucune autre était réellement satisfait. Par conséquent, il a été renvoyée à la planche à dessin. La notation ayant réussie et troisième est désormais standard `dynamic_cast<type>`, ce qui a été généralisé à un ensemble de quatre notations de cast du nouveau style.

Dans la norme ISO-C++, `dynamic_cast` retourne `0` lorsque appliqué à un type pointeur inapproprié et lève un `std::bad_cast` exception lorsqu’il est appliqué à un type référence. Dans les Extensions managées pour C++, appliquant `dynamic_cast` à un type de référence managée (en raison de sa représentation de pointeur) toujours retourné `0`. `__try_cast<type>` a été présenté comme un analogue à l’exception qui lève la variante de la `dynamic_cast`, sauf qu’elle lève une exception `System::InvalidCastException` si le cast échoue.

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

Dans la nouvelle syntaxe, `__try_cast` a été remaniée en tant que `safe_cast`. Voici le même fragment de code dans la nouvelle syntaxe :

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

Dans le monde géré, il est important autoriser pour le code vérifiable en limitant la capacité des programmeurs de cast entre types de manière à laisser le code non vérifiable. Il s’agit d’un aspect essentiel du paradigme de programmation dynamique représenté par la nouvelle syntaxe. Pour cette raison, les instances de casts de style ancien sont transformées en interne comme casts d’exécution, ainsi que, par exemple :

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

En revanche, le polymorphisme offrant un actif et un mode passif, il est parfois nécessaire d’effectuer un cast aval simplement pour accéder à l’API non virtuelle d’un sous-type. Cela peut se produire, par exemple, avec les membres d’une classe qui veulent adresse tout type dans la hiérarchie (polymorphisme passif utilisé comme un mécanisme de transport), mais dont l’instance réelle dans un contexte de programme particulier est connu. Dans ce cas, avoir un contrôle à l’exécution de la conversion peut être une surcharge inacceptable. Si la nouvelle syntaxe est de servir en tant que les langage de programmation de systèmes gérés, elle doit fournir des moyens de permettre à un moment de la compilation (autrement dit, statique) effectuer un downcast. C’est pourquoi l’application de la `static_cast` notation est autorisée à rester un cast aval à la compilation :

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

Le problème est qu’il n’existe aucun moyen de faire en sorte que le programmeur effectuant le `static_cast` est correct et bien intentionné ; autrement dit, il n’existe aucun moyen de forcer le code managé à être vérifiable. Est une préoccupation plus urgente sous le paradigme de programme dynamique que sous native, ce n’est pas suffisant au sein d’un système de langage de programmation pour empêcher l’utilisateur la possibilité de basculer entre un cast statique et effectuer un cast d’exécution.

Il existe cependant une interruption de performances et un piège dans la nouvelle syntaxe. Dans la programmation native, il n’existe aucune différence de performances entre la notation de cast de style ancien et le nouveau style `static_cast` notation. Mais dans la nouvelle syntaxe, la notation de cast de style ancien est plus coûteuse que l’utilisation du nouveau style `static_cast` notation. La raison est que le compilateur transforme en interne l’utilisation de la notation de style ancien dans un contrôle d’exécution qui lève une exception. En outre, il modifie également le profil d’exécution du code, car il provoque une exception non interceptée vers le bas de l’application - peut-être avec raison, mais la même erreur ne provoquerait pas cette exception si le `static_cast` notation ont été utilisés. On pourrait soutenir que cela contribuera aux utilisateurs de la nouvelle notation. Mais uniquement en cas d’échec ; Sinon, elle entraîne des programmes qui utilisent la notation de style ancien pour exécuter beaucoup plus lentement sans comprendre pourquoi, visible similaire pour les pièges de programmeur C suivants :

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>Voir aussi

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[Les Casts de Style C avec /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)