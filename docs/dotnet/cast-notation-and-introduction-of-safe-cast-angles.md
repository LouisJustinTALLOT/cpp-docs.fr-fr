---
title: Notation castée et Introduction de safe_cast&lt; &gt; | Documents Microsoft
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
ms.openlocfilehash: 6b9432b40099f9893d7fd270faf5375646fb0493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111638"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notation de cast et l’Introduction de safe_cast&lt;&gt;
La notation de cast a changé entre les Extensions managées pour C++ vers Visual C++.  
  
 Modification d’une structure existante est une expérience différente et plus difficile que l’élaboration de la structure initiale. Il existe moins de degrés de liberté et la solution tend à un compromis entre une restructuration idéale et possible étant donné les dépendances structurelles existantes.  
  
 Extension de langage est un autre exemple. Dans le début des années 1990 comme l’orientation des objets de programmation est devenue un véritable paradigme, la nécessité d’une fonctionnalité de cast aval de type sécurisé en C++ est devenu en appuyant sur. Cast descendant est la conversion explicite de l’utilisateur d’un pointeur de classe de base ou une référence à un pointeur ou une classe dérivée. Le cast aval requiert un cast explicite. La raison est que le type réel du pointeur de classe de base est un aspect de l’exécution ; le compilateur donc ne peut pas vérifier. Ou bien, autrement dit, une fonctionnalité de cast aval, tout comme un appel de fonction virtuelle nécessite une forme de résolution dynamique. Cela génère deux questions :  
  
-   Pourquoi un cast aval convient nécessaire dans le modèle orienté objet ? N’est pas le mécanisme de fonction virtuelle suffisante ? Autrement dit, pourquoi ne pas considérer que le besoin d’un cast aval (ou un cast quelconque) est une erreur de conception ?  
  
-   Pourquoi la prise en charge d’un cast aval doit être un problème en C++ ? Après tout, il n’est pas un problème dans les langages orientés objet tels que Smalltalk (ou, par la suite, Java et c#) ? Qu’il est sur C++ qui rend donc compliquer de prise en charge ?  
  
 Une fonction virtuelle représente un algorithme dépendant du type commun à une famille de types. (Nous envisageons pas les interfaces qui ne sont pas pris en charge en ISO-C++, mais sont disponible dans la programmation CLR et représentent une alternative de conception intéressante). La conception de cette famille est généralement représentée par une hiérarchie de classe dans laquelle il existe une classe de base abstraite déclarant l’interface commune (les fonctions virtuelles) et un ensemble de classes dérivées concrètes qui représentent la famille de types réelle dans l’application domaine.  
  
 A `Light` hiérarchie dans un domaine d’application IMAGERIE générée par ordinateur (CGI), par exemple, aura des attributs communs tels que `color`, `intensity`, `position`, `on`, `off`, et ainsi de suite. Un peut contrôler plusieurs indicateurs, à l’aide de l’interface commune préoccuper si la lumière est un projecteur, une lumière directionnelle, une lumière non directionnelle (pensez au soleil) ou même une lumière une porte de la barre. Dans ce cas, un cast en un type particulier de lumière exercer son interface virtuelle n’est pas nécessaire. Toutefois, dans un environnement de production, vitesse est essentielle. Une peut castée en aval et appeler explicitement chaque méthode si en procédant ainsi, l’exécution inline des appels peut être effectuée au lieu d’utiliser le mécanisme virtuel.  
  
 L’une des raisons d’un cast aval en C++ est donc supprimer le mécanisme virtuel en augmentation significative des performances d’exécution. (Notez que l’automatisation de cette optimisation manuelle est une zone active de la recherche. Toutefois, il est plus difficile de résoudre que de remplacer l’utilisation explicite de la `register` ou `inline` (mot clé).)  
  
 Une autre raison d’effectuer un cast aval se situe hors de la nature double du polymorphisme. Une façon de considérer le polymorphisme comme divisée en une paire de formes, passive et dynamique.  
  
 Un appel virtuel (et une fonctionnalité de cast aval) représentent l’utilisation dynamique du polymorphisme : une effectue une action basée sur le type réel du pointeur de classe de base à cette instance particulière de l’exécution du programme.  
  
 Assignation d’un objet de classe dérivée à son pointeur de classe de base, toutefois, est une forme passive de polymorphisme ; Il est à l’aide du polymorphisme comme mécanisme de transport. C’est l’utilisation principale de `Object`, par exemple, dans la programmation de CLR des générique. Lorsqu’il est utilisé passivement, le pointeur de la classe de base choisi pour le transport et de stockage, généralement offre une interface trop abstraite. `Object`, par exemple, fournit environ cinq méthodes via son interface ; tout comportement plus spécifique requiert explicite castée en aval. Par exemple, si vous souhaitez ajuster l’angle de notre projecteur ou son taux de diminution, il faut downcast explicitement. Une interface virtuelle au sein d’une famille de sous-types ne peut pas être pratiquement un sur-ensemble de toutes les méthodes possibles de ses nombreux enfants, et par conséquent, une fonctionnalité de cast aval sera toujours nécessaire dans un langage orienté objet.  
  
 Si un cast aval sécurisé fonctionnalité est nécessaire dans un langage orienté objet, puis pourquoi que C++ temps et en ajouter un ? Le problème est de rendre les informations sur le type au moment de l’exécution du pointeur disponibles. Dans le cas d’une fonction virtuelle, les informations d’exécution sont définies dans deux parties par le compilateur :  
  
-   L’objet de classe contient un membre de pointeur de table virtuelle supplémentaire (au début ou à la fin de l’objet de classe qui a un historique intéressant en soi) qui traite la table virtuelle appropriée. Par exemple, un objet projecteur adresse une table virtuelle de projecteur, une lumière directionnelle, une table virtuelle de lumière directionnelle, etc.  
  
-   Chaque fonction virtuelle est associé à un emplacement dans le tableau fixe, et l’instance réelle à appeler est représenté par l’adresse stockée dans la table. Par exemple, le serveur virtuel `Light` destructeur peut-être être associée à l’emplacement 0, `Color` avec emplacement 1 et ainsi de suite. Il s’agit d’une stratégie efficace si fixe, car il est configuré au moment de la compilation et représente une charge minimale.  
  
 Le problème, alors, est de rendre les informations de type disponibles au pointeur sans modifier la taille des pointeurs C++, en ajoutant une deuxième adresse ou en ajoutant directement une sorte de type de codage. Cela ne serait pas acceptable pour les programmeurs (et des programmes) qui décidez de ne pas utiliser le paradigme orienté objet - a été encore la Communauté des utilisateurs prédominant. Une autre possibilité consistait à introduire un pointeur spécial pour les types de classe polymorphe, mais cela serait prêter à confusion et rend difficile la combinaison des deux, en particulier des problèmes de l’opération arithmétique de pointeur. Il également serait pas acceptable pour mettre à jour une table de l’exécution qui associe chaque pointeur à son type actuellement associé et que la mise à jour dynamique.  
  
 Le problème est ensuite une paire de communautés d’utilisateurs qui ont les aspirations de programmation différentes mais légitimes. La solution doit être un compromis entre ces deux groupes, en permettant à chacun non seulement de leur aspiration, mais la possibilité d’interagir. Cela signifie que les solutions offertes par les deux côtés sont susceptibles d’être irréalisable et que la solution implémentée enfin être inférieur à parfait. La résolution réelle tourne autour de la définition d’une classe polymorphe : une classe polymorphe est un objet qui contient une fonction virtuelle. Une classe polymorphe prend en charge un dynamique de type sécurisé castée en aval. Cette action a résolu le problème de tenir à jour le-pointeur-/ adresse, car toutes les classes polymorphes contiennent ce membre pointeur supplémentaire à leur table virtuelle associée. Les informations de type associé, par conséquent, peuvent être stockées dans une structure de table virtuelle développée. Le coût du cast de type sécurisé est (presque) que les utilisateurs de l’installation.  
  
 Le problème suivant concernant le cast de type sécurisé était sa syntaxe. S’agissant d’un cast, la proposition d’origine au comité ISO-C++ utilisé la syntaxe de cast sans ornement, comme dans cet exemple :  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 mais cela a été rejeté par le comité, car il n’a pas permis l’utilisateur de contrôler le coût de la conversion. Si la dynamique de type sécurisé downcast a la même syntaxe comme la précédemment dangereuses mais statique notation de cast, il devient alors une substitution, et l’utilisateur ne dispose d’aucun moyen de supprimer la surcharge d’exécution lorsqu’il est inutile, voire trop coûteux.  
  
 En général, en C++, il existe toujours un mécanisme permettant de supprimer des fonctionnalités de prise en charge du compilateur. Par exemple, nous pouvons désactiver le mécanisme virtuel à l’aide de l’opérateur de portée de classe (`Box::rotate(angle)`) ou en appelant la méthode virtuelle via un objet de classe (plutôt qu’un pointeur ou une référence de cette classe). Cette dernière suppression n’est pas requis par le langage, mais est une qualité de problème d’implémentation, semblable à la suppression de la construction d’une variable temporaire dans une déclaration de la forme :  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 Pour que la proposition a été effectuée antérieurement pour un examen complémentaire et plusieurs autres notations, et l’affiche de nouveau le comité était sous la forme (`?type`), qui indiqué son indéterminée - autrement dit, la nature dynamique. Cela a donné à l’utilisateur la possibilité de basculer entre les deux formes - statiques ou dynamiques - mais n’a été réellement satisfait. Par conséquent, il était sur le tableau de dessin. La notation de tiers et réussie est désormais standard `dynamic_cast<type>`, ce qui a été généralisé à un jeu de quatre notations de cast du nouveau style.  
  
 ISO-c++, `dynamic_cast` retourne `0` lorsque appliqué à un type pointeur inapproprié et lève un `std::bad_cast` exception quand il est appliqué à un type référence. Dans les Extensions managées pour C++, application `dynamic_cast` à un type de référence managée (en raison de sa représentation de pointeur) toujours retourné `0`. `__try_cast<type>` a été présenté comme un analogue à l’exception qui lève la variante de la `dynamic_cast`, excepté qu’elle lève `System::InvalidCastException` si la conversion échoue.  
  
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
  
 Dans l’environnement managé, il est important autoriser pour le code vérifiable en limitant la possibilité aux programmeurs d’effectuer un cast entre types de manière à laisser le code non vérifiable. Il s’agit d’un aspect essentiel du paradigme de programmation dynamique représenté par la nouvelle syntaxe. Pour cette raison, les instances de casts de style ancien sont transformées en interne comme casts d’exécution, ainsi que, par exemple :  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 En revanche, le polymorphisme offrant un actif et un mode passif, il est parfois nécessaire d’effectuer un cast aval simplement pour accéder à l’API non virtuelle d’un sous-type. Cela peut se produire, par exemple, avec les membres d’une classe qui veulent adresse tout type dans la hiérarchie (polymorphisme passif utilisé comme mécanisme de transport) mais pour lesquels l’instance réelle dans un contexte de programme particulier est connu. Dans ce cas, avoir un contrôle à l’exécution de la conversion en peut être une charge mémoire inacceptable. Si la nouvelle syntaxe est pour servir les systèmes gérés, langage de programmation, elle doit fournir un moyen de permettre à un moment de la compilation (c'est-à-dire statique) castée en aval. C’est pourquoi l’application de la `static_cast` notation est autorisée à rester un cast aval à la compilation :  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 Le problème est qu’il n’existe aucun moyen de garantir que le programmeur effectuant le `static_cast` est correct et bien intentionné ; autrement dit, il n’existe aucun moyen de forcer le code managé à être vérifiable. Ceci est un problème plus urgent sous le paradigme de programme dynamique qu’en natif, mais n’est pas suffisant dans un système de la possibilité de basculer entre un statique et l’exécution si vous effectuez un cast de langage pour empêcher l’utilisateur de programmation.  
  
 Il existe toutefois une interruption de performances et le piège dans la nouvelle syntaxe. Dans la programmation native, il n’existe aucune différence de performances entre la notation de cast de style ancien et le nouveau style `static_cast` notation. Mais dans la nouvelle syntaxe, la notation de cast de style ancien est beaucoup plus onéreuse qu’utiliser le nouveau style `static_cast` notation. La raison est que le compilateur transforme en interne de l’utilisation de la notation de style ancien dans un contrôle d’exécution qui lève une exception. En outre, il modifie également le profil d’exécution du code, car il provoque une exception non interceptée qui interrompt l’application - peut-être avec raison, mais la même erreur ne provoquerait pas cette exception si le `static_cast` notation ont été utilisés. On pourrait soutenir que cela contribuera aux utilisateurs de la nouvelle notation. Mais uniquement en cas d’échec ; dans le cas contraire, elle entraîne des programmes qui utilisent la notation de style ancien pour exécuter beaucoup plus lente sans comprendre pourquoi, visible similaire pour les pièges de programmeur C suivants :  
  
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
 [Modifications du langage général (C + c++ / CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Les Casts de Style C avec /clr (C + c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)