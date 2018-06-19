---
title: Valeur de la sémantique de Type | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44662f2ad8e79712b4aab17e2784a72e01ec4116
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171848"
---
# <a name="value-type-semantics"></a>Sémantique de type valeur
Sémantique des types valeur ont été modifiés à partir des Extensions managées pour C++ vers Visual C++.  
  
 Voici le type de valeur canonique simple utilisé dans les Extensions managées pour la spécification de C++ :  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 Dans les Extensions managées, nous pouvons ont des quatre variantes syntaxiques d’un type valeur (où les formulaires 2 et 3 sont sémantiquement identiques) :  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>Appel de méthodes virtuelles héritées  
 `Form (1)` est l’objet de valeur canonique, et il est assez bien compris, sauf lorsque quelqu'un tente d’appeler une méthode virtuelle héritée comme `ToString()`. Par exemple :  
  
```  
v.ToString(); // error!  
```  
  
 Pour appeler cette méthode, car elle n’est pas substituée dans `V`, le compilateur doit avoir accès à la table virtuelle associée de la classe de base. Étant donné que les types valeur sont de stockage dans l’état sans un pointeur associé vers sa table virtuelle (vptr), ceci nécessite que `v` être boxed. Dans la conception du langage des Extensions managées, la conversion boxing implicite n’est pas prise en charge mais doit être spécifié explicitement par le programmeur, comme dans  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 La motivation principale de cette conception est pédagogique : mécanisme sous-jacent doit être visible au programmeur afin qu’il comprenne le coût de ne pas fournir une instance dans son type valeur. Ont été `V` pour contenir une instance de `ToString`, la conversion boxing ne seraient pas nécessaire.  
  
 La complexité lexicale de boxing explicite de l’objet, mais pas le coût sous-jacent de la conversion boxing elle-même, est supprimée de la nouvelle syntaxe :  
  
```  
v.ToString(); // new syntax  
```  
  
 mais égarer éventuellement le Concepteur de classes quant au coût de n’avoir ne pas fourni d’instance explicite de la `ToString` méthode `V`. La préférence pour la conversion boxing implicite s’est généralement qu’un concepteur de classes, il existe un nombre illimité d’utilisateurs, dont aucun serait libre de modifier `V` pour éliminer la zone explicite éventuellement onéreuse.  
  
 Les critères servant à déterminer s’il faut ou non fournir une instance de substitution de `ToString` au sein d’une valeur de la classe doit être la fréquence et l’emplacement de ses utilisations. Si elle est appelée de manière très rarement, il est bien sûr peu d’intérêt dans sa définition. De même, si elle est appelée dans les zones non performantes de l’application, il sera également pas sensiblement ajout aux performances générales de l’application. Vous pouvez également, à conserver un handle de suivi de la valeur boxed et appels via ce handle ne sont pas besoin boxing.  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Il n’est plus un constructeur par défaut de classe de valeur  
 Une autre différence avec un type de valeur entre les Extensions managées et la nouvelle syntaxe est la suppression de la prise en charge un constructeur par défaut. Il s’agit, car il existe parfois pendant l’exécution dans lequel le CLR peut créer une instance du type valeur sans appeler le constructeur par défaut associé. Autrement dit, la tentative sous les Extensions managées pour prendre en charge un constructeur par défaut dans un type valeur impossible dans la pratique être garantie. Étant donné cette absence de garantie, il a été jugé préférable de supprimer complètement de la prise en charge au lieu qu’elle soit non déterministe dans son application.  
  
 Ce n’est pas aussi grave qu’il peut sembler initialement. C’est parce que chaque objet d’un type valeur est automatiquement annulé (autrement dit, chaque type est initialisé à sa valeur par défaut). Par conséquent, les membres d’une instance locale ne sont jamais indéfinis. Dans ce sens, la perte de la capacité à définir un constructeur trivial par défaut n’est pas réellement une perte de tout - et en fait est plus efficace lorsque exécutée par le CLR.  
  
 Le problème est lorsqu’un utilisateur des Extensions managées définit un constructeur par défaut non trivial. Cela n’est mappé à la nouvelle syntaxe. Le code dans le constructeur doit être migré dans une méthode d’initialisation nommée qui devra ensuite être appelé explicitement par l’utilisateur.  
  
 Sinon, la déclaration d’un objet de type valeur dans la nouvelle syntaxe est inchangée. L’inconvénient de cela est que les types valeur ne sont pas satisfaisantes pour l’encapsulation des types natifs pour les raisons suivantes :  
  
-   Il n’existe aucune prise en charge du destructeur dans un type valeur. Autrement dit, il n’existe aucun moyen d’automatiser un ensemble d’actions déclenchées par la fin de la durée de vie d’un objet.  
  
-   Une classe native peut contenir uniquement au sein d’un type managé en tant que pointeur ultérieurement alloué sur le tas natif.  
  
 Nous souhaitons encapsuler une petite classe native dans un type valeur plutôt qu’un type référence afin d’éviter une double allocation de tas : le tas natif pour contenir le type natif et le tas CLR pour stocker le wrapper managé. Encapsule une classe native dans un type valeur vous permet d’éviter le tas managé, mais n’offre aucun moyen d’automatiser la récupération de la mémoire de tas natif. Les types référence sont le type managé uniquement possible dans lequel habiller des classes natives non trivial.  
  
## <a name="interior-pointers"></a>Pointeurs intérieurs  
 `Form (2)` et `Form (3)` ci-dessus peuvent presque tout adresser dans ce monde ou dans l’autre (autrement dit, toute valeur managé ou natif). Ainsi, par exemple, les conditions suivantes sont autorisées dans les Extensions managées :  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
V *pv = 0;  // Form (2)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0;  // Form (4)  
  
R* r;  
  
pv = &v;            // address a value type on the stack  
pv = __nogc new V;  // address a value type on native heap  
pv = pvgc;          // we are not sure what this addresses  
pv = pvbx;          // address a boxed value type on managed heap  
pv = &r->vr;        // an interior pointer to value type within a  
                    //    reference type on the managed heap  
```  
  
 Par conséquent, un `V*` peut adresser un emplacement dans un bloc local (et par conséquent peut être non résolu), dans une portée globale, dans natif du segment de mémoire (par exemple, si l’objet qu’il adresse a déjà été supprimé), dans le tas du CLR (et par conséquent de suivi s’il doit déplacé pendant le garbage collection) et à l’intérieur d’un objet de référence sur le tas CLR (un pointeur intérieur, comme cela est appelée, est également suivi de façon transparente).  
  
 Dans les Extensions managées, il n’existe aucun moyen de séparer les aspects natifs d’une `V*`; autrement dit, il est traité son inclusif, qui gère la possibilité qu’il traite un objet ou un sous-objet sur le tas managé.  
  
 Dans la nouvelle syntaxe, un pointeur de type valeur est pris en compte dans les deux types : `V*`, qui est limité aux emplacements de tas non CLR et le pointeur intérieur, `interior_ptr<V>`, qui permet, mais qui ne requiert pas une adresse dans le tas managé.  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)` et `Form (3)` des Extensions managées mappent dans `interior_ptr<V>`. `Form (4)` est un handle de suivi. Il traite l’objet entier a été convertie (boxed) dans le tas managé. Il est traduit dans la nouvelle syntaxe dans une `V^`,  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Les déclarations suivantes dans les Extensions managées correspondent à des pointeurs intérieurs dans la nouvelle syntaxe. (Ils sont des types de valeur dans la `System` espace de noms.)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 Les types intégrés ne sont pas considérés comme des types managés, bien qu’ils servent d’alias aux types dans les `System` espace de noms. Par conséquent, les mappages suivants vraie entre les Extensions managées et la nouvelle syntaxe :  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 Lors de la traduction un `V*` dans un programme existant, la stratégie la plus conservatrice est toujours le transforme en un `interior_ptr<V>`. C’est la façon dont il a été traité sous les Extensions managées. Dans la nouvelle syntaxe, le programmeur a la possibilité de restreindre un type valeur à des adresses de tas non managé en spécifiant `V*` au lieu d’un pointeur intérieur. Si, en traduisant votre programme, vous pouvez effectuer une fermeture transitive de toutes ses utilisations et assurez-vous qu’aucune adresse assignée n’est dans le tas managé, puis laisser sous la forme `V*` est correct.  
  
## <a name="pinning-pointers"></a>Pointeurs épingle  
 Le garbage collector peut éventuellement déplacer les objets qui résident sur le tas CLR à différents emplacements dans le tas, en général pendant la phase de compactage. Ce déplacement n’est pas un problème pour le suivi des handles, des références de suivi et des pointeurs intérieurs qui mettent à jour ces entités de façon transparente. Ce déplacement est un problème, toutefois, si l’utilisateur a passé l’adresse d’un objet sur le tas CLR en dehors de l’environnement d’exécution. Dans ce cas, le déplacement volatil de l’objet est susceptible de provoquer un échec d’exécution. Pour exempter certains objets, telles que celles-ci soient déplacés, nous devons les épingler localement sur leur emplacement pour l’étendue de leur utilisation externe.  
  
 Dans les Extensions managées, un *pointeur épingle* est déclaré en qualifiant une déclaration de pointeur avec le `__pin` (mot clé). Voici un exemple légèrement modifié à partir de la spécification d’Extensions managées :  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 Dans la nouvelle conception de langage, un pointeur épingle est déclaré avec une syntaxe similaire à celle d’un pointeur intérieur.  
  
```  
ref struct H  
{  
public:  
   int j;  
};  
  
int main()  
{  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
  
   // ...  
}  
```  
  
 Un pointeur épingle dans la nouvelle syntaxe est un cas spécial d’un pointeur intérieur. Les contraintes d’origine sur un pointeur épingle restent. Par exemple, il ne peut pas être utilisé en tant que paramètre ou type de retour d’une méthode ; Il peut être déclaré que sur un objet local. Plusieurs contraintes supplémentaires, toutefois, ont été ajoutées dans la nouvelle syntaxe.  
  
 La valeur par défaut d’un pointeur épingle est `nullptr`, et non `0`. A `pin_ptr<>` ne peut pas être initialisé ou recevoir `0`. Toutes les attributions de `0` dans le code existant doit être modifié pour `nullptr`.  
  
 Un pointeur épingle sous les Extensions managées était autorisé à adresser un objet entier, comme dans l’exemple suivant extrait de la spécification d’Extensions managées :  
  
```  
__gc class G {  
public:  
   void incr(int* pi) { pi += 1; }  
};  
__gc struct H { int j; };  
void f( G * g ) {  
   H __pin * pH = new H;     
   g->incr(& pH -> j);     
};  
```  
  
 Dans la nouvelle syntaxe, l’épinglage de l’objet entier retourné par la `new` expression n’est pas prise en charge. Au lieu de cela, l’adresse du membre intérieur doit être épinglée. Par exemple :  
  
```  
ref class G {  
public:  
   void incr(int* pi) { *pi += 1; }  
};  
ref struct H { int j; };  
void f( G^ g ) {  
   H ^ph = gcnew H;  
   Console::WriteLine(ph->j);  
   pin_ptr<int> pj = &ph->j;  
   g->incr(  pj );  
   Console::WriteLine(ph->j);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types valeur et leurs comportements (C + c++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C + c++ / CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)