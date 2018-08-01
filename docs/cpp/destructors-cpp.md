---
title: Destructeurs (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b16230d612ea7304e8bc06a9810838ce3f42ac8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405647"
---
# <a name="destructors-c"></a>Destructeurs (C++)

Un destructeur est une fonction membre qui est appelée automatiquement lorsque l’objet est hors de portée ou est détruite explicitement par un appel à **supprimer**. Un destructeur a le même nom que la classe précédé par un tilde (`~`). Par exemple, le destructeur de la classe `String` est déclaré : `~String()`.

Si vous ne définissez pas un destructeur, le compilateur fournit un par défaut ; Pour de nombreuses classes, cela est suffisant. Vous devez uniquement définir un destructeur personnalisé lors de la classe stocke les handles vers des ressources système qui doivent être libérées ou pointeurs qui possèdent la mémoire, ils pointent vers.

Prenons la déclaration suivante d'une classe `String` :

```cpp
// spec1_destructors.cpp
#include <string.h>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   if (_text)
      delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

Dans l’exemple précédent, le destructeur `String::~String` utilise le **supprimer** opérateur pour libérer l’espace dynamiquement alloué pour le stockage de texte.

## <a name="declaring-destructors"></a>Déclaration des destructeurs

Les destructeurs sont des fonctions ayant le même nom que la classe, mais précédé d'un tilde (`~`).

Plusieurs règles régissent la déclaration des destructeurs. Les destructeurs :

- n’acceptent pas d’arguments ;

- Ne retournent pas de valeur (ou **void**).

- Ne peut pas être déclaré en tant que **const**, **volatile**, ou **statique**. Toutefois, ils peuvent être appelés pour la destruction d’objets déclarés en tant que **const**, **volatile**, ou **statique**.

- Peut être déclaré comme **virtuel**. En utilisant des destructeurs virtuels, vous pouvez détruire des objets sans connaître leur type (le destructeur correct de l’objet est appelé via le mécanisme de fonction virtuelle). Notez que les destructeurs peuvent également être déclarés en tant que fonctions virtuelles pures pour les classes abstraites.

## <a name="using-destructors"></a>Utilisation de destructeurs

Les destructeurs sont appelés lorsque l'un des événements suivants se produit :

- Un objet (automatique) local avec portée de bloc passe hors de portée.

- Un objet alloué à l’aide de la **nouveau** opérateur est explicitement libéré aide **supprimer**.

- La durée de vie d'un objet temporaire se termine.

- Un programme se termine et des objets globaux ou statiques existent.

- Le destructeur est appelé explicitement à l'aide du nom complet de la fonction destructeur.

Les destructeurs peuvent librement appeler des fonctions membres de classe et accéder aux données de membres de classe.

Il existe deux restrictions sur l’utilisation de destructeurs :

- Vous ne pouvez pas prendre son adresse.

- Les classes dérivées n’héritent pas du destructeur de leur classe de base.

## <a name="order-of-destruction"></a>Ordre de destruction

Lorsqu'un objet bascule hors de portée ou est supprimé, la séquence d'événements de sa suppression complète est la suivante :

1. Le destructeur de la classe est appelé et le corps de la fonction destructeur est exécuté.

1. Les destructeurs des objets membres non statiques sont appelés dans l'ordre inverse dans lequel ils apparaissent dans la déclaration de classe. La liste d’initialisation de membre facultatif utilisée dans la construction de ces membres n’affecte pas l’ordre de construction ou destruction.

1. Les destructeurs pour les classes de base non virtuelles sont appelés dans l’ordre inverse de déclaration.

1. Les destructeurs pour les classes de base virtuelles sont appelés dans l'ordre inverse de leur déclaration.

```cpp
// order_of_destruction.cpp
#include <stdio.h>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor
```

### <a name="virtual-base-classes"></a>Classes de base virtuelles

Les destructeurs pour les classes de base virtuelles sont appelés dans l'ordre inverse d'apparition dans un graphique acyclique dirigé (balayage à profondeur prioritaire, de gauche à droite, post-ordre). L'illustration suivante représente un graphique d'héritage.

![Graphique d’héritage montrant des classes de base virtuelles](../cpp/media/vc392j1.gif "vc392J1")

Graphique d'héritage illustrant les classes de base virtuelles

L'exemple suivant répertorie les titres des classes représentées dans l'illustration.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Pour déterminer l'ordre de destruction des classes de base virtuelles d'un objet de type `E`, le compilateur génère une liste en appliquant l'algorithme suivant :

1. Balayez le graphique vers la gauche, en démarrant au point le plus élevé dans le graphique (dans ce cas, `E`).

1. Exécutez des balayages vers la gauche jusqu'à ce que tous les nœuds aient été consultés. Notez le nom du nœud actuel.

1. Reprenez le nœud précédent (en bas et à droite) pour déterminer si le nœud mémorisé est une classe de base virtuelle.

1. Si le nœud mémorisé est une classe de base virtuelle, analysez la liste pour voir si elle a déjà été entrée. Si ce n'est pas une classe de base virtuelle, ignorez-la.

1. Si le nœud mémorisé n'est pas encore dans la liste, ajoutez-le au bas de la liste.

1. Balayez le graphique vers le haut et le long du tracé suivant vers la droite.

1. Passez à étape 2.

1. Lorsque le dernier tracé vers le haut est écoulé, notez le nom du nœud actuel.

1. Passez à l'étape 3.

1. Continuez ainsi jusqu'à ce que le nœud inférieur soit de nouveau le nœud actuel.

Par conséquent, pour la classe `E`, l'ordre de destruction est le suivant :

1. La classe de base non virtuelle `E`.

1. La classe de base non virtuelle `D`.

1. La classe de base non virtuelle `C`.

1. Classe de base virtuelle `B`.

1. Classe de base virtuelle `A`.

Ce processus crée une liste triée d'entrées uniques. Aucun nom de classe n'apparaît deux fois. Une fois la liste construite, elle est parcourue dans l'ordre inverse, et le destructeur de chacune des classes de la liste est appelé du dernier au premier.

L'ordre de construction ou de destruction est particulièrement important lorsque les constructeurs ou les destructeurs d'une classe reposent sur l'autre composant créé en premier ou persistant plus longtemps (par exemple, si le destructeur de `A` (dans l'illustration ci-dessus) reposait sur la présence de `B` lors de l'exécution de son code, ou vice versa).

Ces interdépendances entre les classes dans un graphique d’héritage sont fondamentalement dangereuses car les classes dérivées ultérieurement peuvent modifier le tracé à l’extrême gauche, modifiant ainsi l’ordre de construction et de destruction.

### <a name="non-virtual-base-classes"></a>Classes de base non virtuelles

Les destructeurs pour les classes de base non virtuelles sont appelés dans l’ordre inverse dans lequel les noms de classe de base sont déclarés. Prenons la déclaration de classe suivante :

```cpp
class MultInherit : public Base1, public Base2
...
```

Dans l'exemple précédent, le destructeur de `Base2` est appelé avant le destructeur de `Base1`.

## <a name="explicit-destructor-calls"></a>Appels de destructeur explicites

Appeler un destructeur explicitement est rarement nécessaire. Toutefois, il peut être utile d'effectuer un nettoyage des objets placés à des adresses absolues. Ces objets sont couramment alloués à l’aide de défini par l’utilisateur **nouveau** opérateur qui accepte un argument de positionnement. Le **supprimer** opérateur ne peut pas libérer cette mémoire, car elle n’est pas allouée à partir du magasin gratuit (pour plus d’informations, consultez [le nouveau et supprimer des opérateurs](../cpp/new-and-delete-operators.md)). Un appel au destructeur, toutefois, permet d'effectuer un nettoyage approprié. Pour appeler explicitement le destructeur pour un objet, `s`, de classe `String`, utilisez l'une des instructions suivantes :

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

La notation pour les appels explicites aux destructeurs, illustrée dans l'exemple précédent, peut être utilisée que le type définisse ou non un destructeur. Vous pouvez ainsi effectuer ce type d'appels explicites sans savoir si un destructeur est défini pour le type. Un appel explicite à un destructeur n'a aucun effet lorsqu'aucun destructeur n'est défini.