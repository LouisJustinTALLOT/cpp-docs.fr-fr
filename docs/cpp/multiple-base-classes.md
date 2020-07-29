---
title: Plusieurs classes de base
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 0e663f33213a5fd57f2adbdcc53233c6af29954e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227372"
---
# <a name="multiple-base-classes"></a>Plusieurs classes de base

Une classe peut être dérivée de plusieurs classes de base. Dans un modèle d’héritage multiple (où les classes sont dérivées de plusieurs classes de base), les classes de base sont spécifiées à l’aide de l’élément de grammaire *de liste de base* . Par exemple, la déclaration de classe pour `CollectionOfBook`, dérivé de `Collection` et `Book`, peut être spécifiée :

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

L'ordre dans lequel les classes de base sont spécifiées n'a pas d'importance sauf dans certains cas où les constructeurs et les destructeurs sont appelés. Dans ces cas, l'ordre dans lequel les classes de base sont spécifiées a une incidence sur ce qui suit :

- L'ordre dans lequel l'initialisation du constructeur est exécutée. Si votre code repose sur la partie `Book` de `CollectionOfBook` à initialiser avant la partie `Collection`, l'ordre des spécifications est important. L’initialisation a lieu dans l’ordre dans lequel les classes sont spécifiées dans la *liste de base*.

- L'ordre dans lequel les destructeurs sont appelés pour effectuer le nettoyage. Là encore, si un « élément » particulier de la classe doit être présent lorsque l'autre élément est détruit, l'ordre a une importance. Les destructeurs sont appelés dans l’ordre inverse des classes spécifiées dans la *liste de base*.

    > [!NOTE]
    >  L'ordre de spécification des classes de base peut avoir une incidence sur la disposition de mémoire de la classe. Ne prenez aucune décision de programmation concernant l'ordre des membres de base en mémoire.

Lorsque vous spécifiez la *liste de base*, vous ne pouvez pas spécifier plusieurs fois le même nom de classe. Toutefois, il est possible qu'une classe représente plusieurs fois une base indirecte par rapport à une classe dérivée plusieurs fois.

## <a name="virtual-base-classes"></a>Classes de base virtuelles

Comme une classe peut être une classe de base indirecte à une classe dérivée plusieurs fois, C++ offre un moyen d'optimiser la façon dont fonctionnent de telles classes de base. Les classes de base virtuelles permettent d'économiser de l'espace et d'éviter les ambiguïtés dans les hiérarchies de classes qui utilisent un héritage multiple.

Chaque objet non virtuel contient une copie des données membres définies dans la classe de base. Cette duplication gaspille de l'espace et vous oblige à spécifier quelle copie des membres de classe de base vous souhaitez chaque fois que vous accédez à eux.

Lorsqu'une classe de base est spécifiée comme base virtuelle, elle peut agir comme base indirecte plusieurs fois sans duplication de ses données membres. Une copie unique de ses données membres est partagée par toutes les classes de base qui l'utilisent comme base virtuelle.

Lors de la déclaration d’une classe de base virtuelle, le **`virtual`** mot clé apparaît dans les listes de base des classes dérivées.

Dans la figure ci-dessous, la hiérarchie de classes illustre un objet Lunch-Line simulé.

![Graphique Lunch-Line simulé](../cpp/media/vc38xp1.gif "Graphique Lunch-Line simulé") <br/>
Graphique en courbes de déjeuner simulé

Dans la figure, `Queue` représente la classe de base de `CashierQueue` et `LunchQueue`. Toutefois, lorsque les deux classes sont combinées pour former `LunchCashierQueue`, le problème suivant survient : la nouvelle classe contient deux sous-objets de type `Queue`, l'un provenant de `CashierQueue` et l'autre de `LunchQueue`. La figure suivante montre la disposition de mémoire conceptuelle (la disposition de mémoire réelle peut être optimisée).

![Objet de ligne&#45;déjeuner simulé](../cpp/media/vc38xp2.gif "Objet de ligne&#45;déjeuner simulé") <br/>
Objet Lunch-Line simulé

Notez que deux sous-objets `Queue` figurent dans l'objet `LunchCashierQueue`. Le code suivant déclare `Queue` en tant que classe de base virtuelle :

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

Le **`virtual`** mot clé garantit qu’une seule copie du sous-objet `Queue` est incluse (voir la figure suivante).

![Objet de ligne&#45;déjeuner simulé, classes de base virtuelles](../cpp/media/vc38xp3.gif "Objet de ligne&#45;déjeuner simulé, classes de base virtuelles") <br/>
Objet de ligne de déjeuner simulé avec des classes de base virtuelles

Une classe peut avoir à la fois un composant virtuel et un composant non virtuel d'un type donné. Cela se produit dans les conditions illustrées à la figure suivante.

![Composants virtuels et non&#45;d’une classe](../cpp/media/vc38xp4.gif "Composants virtuels et non&#45;d’une classe") <br/>
Composants virtuels et non virtuels de la même classe

Dans cette figure, `CashierQueue` et `LunchQueue` utilisent `Queue` comme classe de base virtuelle. Toutefois, `TakeoutQueue` spécifie `Queue` en tant que classe de base, et non pas comme classe de base virtuelle. Par conséquent, `LunchTakeoutCashierQueue` a deux sous-objets de type `Queue` : l’un provenant du chemin d’héritage qui inclut `LunchCashierQueue` et l’autre provenant du chemin qui inclut `TakeoutQueue`. La figure ci-dessous illustre cela.

![Héritage virtuel non&#45;& virtuel dans la disposition des objets](../cpp/media/vc38xp5.gif "Héritage virtuel non&#45;& virtuel dans la disposition des objets") <br/>
Disposition des objets avec héritage virtuel et non virtuel

> [!NOTE]
> L'héritage virtuel fournit des avantages de taille significatifs par rapport à l'héritage non virtuel. Toutefois, il peut introduire une certaine surcharge de traitement.

Si une classe dérivée remplace une fonction virtuelle qu'elle hérite d'une classe de base virtuelle, et si un constructeur ou un destructeur pour la classe de base dérivée appelle cette fonction à l'aide d'un pointeur désignant la classe de base virtuelle, le compilateur peut introduire des champs « vtordisp » masqués supplémentaires dans les classes dotées de bases virtuelles. L' `/vd0` option de compilateur supprime l’ajout du membre de déplacement du constructeur/destructeur vtordisp masqué. L' `/vd1` option de compilateur, la valeur par défaut, les active là où elles sont nécessaires. Désactivez les paramètres vtordisp seulement si vous êtes certain que tous les constructeurs et destructeurs de classe appellent virtuellement les fonctions virtuelles.

L' `/vd` option de compilateur affecte un module de compilation entier. Utilisez le `vtordisp` pragma pour supprimer, puis réactiver les `vtordisp` champs classe par classe :

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Ambiguïtés au niveau du nom

L'héritage multiple présente le risque que les noms soient hérités le long de plusieurs chemins. Les noms de membre de classe le long de ces chemins d'accès ne sont pas nécessairement uniques. Ces conflits de nom sont appelés « ambiguïtés. »

Toute expression qui fait référence à un membre de classe doit faire une référence qui ne soit pas ambigu. L'exemple suivant montre comment développer les ambiguïtés :

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

Compte tenu des déclarations de classe précédentes, le code (tel que celui qui suit) est ambigu parce qu'il est vague si `b` fait référence à `b` dans `A` ou dans `B`:

```cpp
C *pc = new C;

pc->b();
```

Prenons l'exemple précédent. Comme le nom `a` est membre de la classe `A` et de la classe `B`, le compilateur ne peut pas discerner lequel `a` désigne la fonction à appeler. L'accès à un membre est ambigu s'il peut faire référence à plusieurs fonctions, objets, types ou énumérateurs.

Le compilateur détecte les ambiguïtés en exécutant des tests dans cet ordre :

1. Si l'accès au nom est ambigu (comme il vient d'être décrit), un message d'erreur est généré.

1. Si les fonctions surchargées ne sont pas ambiguës, elles sont résolues.

1. Si l'accès au nom ne respecte pas l'autorisation accès-membre, un message d'erreur est généré. (Pour plus d’informations, consultez [member-Access Control](../cpp/member-access-control-cpp.md).)

Lorsqu'une expression génère une ambiguïté par héritage, vous pouvez manuellement la résoudre en qualifiant le nom en question avec son nom de classe. Pour que l'exemple précédent se compile correctement sans ambiguïtés, utilisez par exemple ce code :

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> Lorsque `C` est déclaré, il a la possibilité de provoquer des erreurs lorsque `B` est référencé dans la portée de `C`. Aucune erreur n'est publiée, toutefois, jusqu'à ce qu'une référence non qualifiée à `B` soit effectuée en réalité dans la portée de `C`.

### <a name="dominance"></a>Dominance

Il est possible que plusieurs noms (fonction, objet ou énumérateur) soient accessibles via un graphique d'héritage. Ces cas sont jugés équivoques par rapport aux classes de base non virtuelles. Ils sont également équivoques par rapport aux classes de base virtuelles sauf si l'un des noms domine les autres.

Un nom domine un autre nom s'il est défini dans les deux classes et qu'une classe est dérivée de l'autre. Le nom dominant est le nom figurant dans la classe dérivée. Ce nom est utilisé lorsqu'une ambiguïté serait autrement apparue, comme indiqué dans l'exemple suivant :

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>Conversions ambiguës

Les conversions explicites et implicites à partir de pointeurs ou de références vers des types classe peuvent provoquer des ambiguïtés. L'illustration suivante, Conversion ambiguë des pointeurs vers des classes de base, montre ce qui suit :

- La déclaration d'un objet de type `D`.

- Effet de l’application de l’opérateur d’adresse ( **&** ) à cet objet. Notez que l'opérateur d'adresse fournit toujours l'adresse de base de l'objet.

- L'effet de la conversion explicite du pointeur obtenu à l'aide de l'opérateur d'adresse vers le type de classe de base `A`. Notez que forcer l'adresse de l'objet en type `A*` ne fournit pas toujours au compilateur suffisamment d'informations concernant le sous-objet de type `A` à sélectionner ; dans ce cas, deux sous-objets existent.

![Conversion ambiguë de pointeurs vers les classes de base](../cpp/media/vc38xt1.gif "Conversion ambiguë de pointeurs vers les classes de base") <br/>
Conversion ambiguë de pointeurs vers les classes de base

La conversion vers le type `A*` (pointeur vers `A`) est ambiguë car il n'y a aucun moyen de déterminer quel est le sous-objet de type `A` correct. Notez que vous pouvez éviter toute ambiguïté en spécifiant explicitement le sous-objet que vous souhaitez utiliser, comme suit :

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Ambiguïtés et classes de base virtuelles

Si des classes de base virtuelles sont utilisées, les fonctions, les objets, les types et les énumérateurs sont accessibles via plusieurs chemins d’héritage. Comme il n'existe qu'une instance de la classe de base, il n'y a aucune ambiguïté lors de l'accès à ces noms.

L'illustration suivante montre comment les objets sont composés à l'aide de l'héritage virtuel et non virtuel.

![Dérivation virtuelle et dérivation virtuelle non&#45;](../cpp/media/vc38xr1.gif "Dérivation virtuelle et dérivation virtuelle non&#45;") <br/>
Dérivation virtuelle et non virtuelle

Dans l'illustration, accéder à un membre de classe `A` via des classes de base non virtuelles provoque une ambiguïté ; le compilateur ne propose aucune information indiquant s'il convient d'utiliser le sous-objet associé à `B` ou le sous-objet associé à `C`. Toutefois, lorsque `A` est spécifié comme classe de base virtuelle, il n'y a aucune interrogation quant au sous-objet faisant l'objet d'un accès.

## <a name="see-also"></a>Voir aussi

[Héritage](../cpp/inheritance-cpp.md)
