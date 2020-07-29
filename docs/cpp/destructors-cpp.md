---
title: Destructeurs (C++)
ms.date: 07/20/2019
helpviewer_keywords:
- objects [C++], destroying
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
ms.openlocfilehash: 5da7659d2d45bca9efba21be2cd0bf581d539780
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221664"
---
# <a name="destructors-c"></a>Destructeurs (C++)

Un destructeur est une fonction membre qui est appelée automatiquement lorsque l’objet est hors de portée ou est détruite explicitement par un appel à **`delete`** . Un destructeur porte le même nom que la classe, précédé d’un tilde ( `~` ). Par exemple, le destructeur de la classe `String` est déclaré : `~String()`.

Si vous ne définissez pas de destructeur, le compilateur fournira un destructeur par défaut ; pour de nombreuses classes, cela suffit. Il vous suffit de définir un destructeur personnalisé lorsque la classe stocke des handles vers des ressources système qui doivent être libérées, ou des pointeurs qui possèdent la mémoire à laquelle elles pointent.

Prenons la déclaration suivante d'une classe `String` :

```cpp
// spec1_destructors.cpp
#include <string>

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
   delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

Dans l’exemple précédent, le destructeur `String::~String` utilise l' **`delete`** opérateur pour libérer l’espace alloué dynamiquement au stockage de texte.

## <a name="declaring-destructors"></a>Déclarer des destructeurs

Les destructeurs sont des fonctions ayant le même nom que la classe, mais précédé d'un tilde (`~`).

Plusieurs règles régissent la déclaration des destructeurs. Les destructeurs :

- n'acceptent pas d'arguments ;

- Ne pas retourner de valeur (ou **`void`** ).

- Ne peut pas être déclaré comme **`const`** , **`volatile`** ou **`static`** . Toutefois, elles peuvent être appelées pour la destruction d’objets déclarés comme **`const`** , **`volatile`** ou **`static`** .

- Peut être déclaré comme **`virtual`** . En utilisant des destructeurs virtuels, vous pouvez détruire des objets sans connaître leur type (le destructeur correct de l’objet est appelé via le mécanisme de fonction virtuelle). Notez que les destructeurs peuvent également être déclarés en tant que fonctions virtuelles pures pour les classes abstraites.

## <a name="using-destructors"></a>Utilisation de destructeurs

Les destructeurs sont appelés lorsque l'un des événements suivants se produit :

- Un objet (automatique) local avec portée de bloc passe hors de portée.

- Un objet alloué à l’aide de l' **`new`** opérateur est désalloué explicitement à l’aide de **`delete`** .

- La durée de vie d'un objet temporaire se termine.

- Un programme se termine et des objets globaux ou statiques existent.

- Le destructeur est appelé explicitement à l'aide du nom complet de la fonction destructeur.

Les destructeurs peuvent librement appeler des fonctions membres de classe et accéder aux données de membres de classe.

Il existe deux restrictions sur l’utilisation des destructeurs :

- Vous ne pouvez pas prendre son adresse.

- Les classes dérivées n’héritent pas du destructeur de leur classe de base.

## <a name="order-of-destruction"></a>Ordre de destruction

Lorsqu'un objet bascule hors de portée ou est supprimé, la séquence d'événements de sa suppression complète est la suivante :

1. Le destructeur de la classe est appelé et le corps de la fonction destructeur est exécuté.

1. Les destructeurs des objets membres non statiques sont appelés dans l'ordre inverse dans lequel ils apparaissent dans la déclaration de classe. La liste facultative d’initialisation de membre utilisée dans la construction de ces membres n’affecte pas l’ordre de construction ou de destruction.

1. Les destructeurs pour les classes de base non virtuelles sont appelés dans l’ordre inverse de déclaration.

1. Les destructeurs pour les classes de base virtuelles sont appelés dans l'ordre inverse de leur déclaration.

```cpp
// order_of_destruction.cpp
#include <cstdio>

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

![Graphique d'héritage montrant des classes de base virtuelles](../cpp/media/vc392j1.gif "Graphique d'héritage montrant des classes de base virtuelles") <br/>
Graphique d'héritage montrant des classes de base virtuelles

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

1. Passez à l’étape 2.

1. Lorsque le dernier tracé vers le haut est écoulé, notez le nom du nœud actuel.

1. Passez à l’étape 3.

1. Continuez ainsi jusqu'à ce que le nœud inférieur soit de nouveau le nœud actuel.

Par conséquent, pour la classe `E`, l'ordre de destruction est le suivant :

1. Classe de base non virtuelle `E` .

1. Classe de base non virtuelle `D` .

1. Classe de base non virtuelle `C` .

1. Classe de base virtuelle `B`.

1. Classe de base virtuelle `A`.

Ce processus crée une liste triée d'entrées uniques. Aucun nom de classe n'apparaît deux fois. Une fois la liste construite, elle est parcourue dans l'ordre inverse, et le destructeur de chacune des classes de la liste est appelé du dernier au premier.

L'ordre de construction ou de destruction est particulièrement important lorsque les constructeurs ou les destructeurs d'une classe reposent sur l'autre composant créé en premier ou persistant plus longtemps (par exemple, si le destructeur de `A` (dans l'illustration ci-dessus) reposait sur la présence de `B` lors de l'exécution de son code, ou vice versa).

Ces interdépendances entre les classes dans un graphique d'héritage sont fondamentalement dangereuses car les classes dérivées ultérieurement peuvent modifier le tracé à l'extrême gauche, modifiant ainsi l'ordre de construction et de destruction.

### <a name="non-virtual-base-classes"></a>Classes de base non virtuelles

Les destructeurs pour les classes de base non virtuelles sont appelés dans l’ordre inverse dans lequel les noms de classe de base sont déclarés. Prenons la déclaration de classe suivante :

```cpp
class MultInherit : public Base1, public Base2
...
```

Dans l'exemple précédent, le destructeur de `Base2` est appelé avant le destructeur de `Base1`.

## <a name="explicit-destructor-calls"></a>Appels de destructeur explicites

Appeler un destructeur explicitement est rarement nécessaire. Toutefois, il peut être utile d'effectuer un nettoyage des objets placés à des adresses absolues. Ces objets sont généralement alloués à l’aide d’un opérateur défini par l’utilisateur **`new`** qui prend un argument de positionnement. L' **`delete`** opérateur ne peut pas libérer cette mémoire, car elle n’est pas allouée à partir du magasin gratuit (pour plus d’informations, consultez [les opérateurs New et Delete](../cpp/new-and-delete-operators.md)). Un appel au destructeur, toutefois, permet d'effectuer un nettoyage approprié. Pour appeler explicitement le destructeur pour un objet, `s`, de classe `String`, utilisez l'une des instructions suivantes :

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

La notation pour les appels explicites aux destructeurs, illustrée dans l'exemple précédent, peut être utilisée que le type définisse ou non un destructeur. Vous pouvez ainsi effectuer ce type d'appels explicites sans savoir si un destructeur est défini pour le type. Un appel explicite à un destructeur n'a aucun effet lorsqu'aucun destructeur n'est défini.

## <a name="robust-programming"></a>Programmation fiable

Une classe a besoin d’un destructeur si elle acquiert une ressource, et pour gérer en toute sécurité la ressource, elle doit probablement implémenter un constructeur de copie et une assignation de copie.

Si ces fonctions spéciales ne sont pas définies par l’utilisateur, elles sont définies implicitement par le compilateur. Les constructeurs et les opérateurs d’assignation générés implicitement effectuent une copie superficielle, membre, qui est presque certainement erronée si un objet gère une ressource.

Dans l’exemple suivant, le constructeur de copie généré implicitement crée les pointeurs `str1.text` et `str2.text` fait référence à la même mémoire et, lorsque nous retournons à partir de `copy_strings()` , cette mémoire est supprimée deux fois, ce qui correspond à un comportement indéfini :

```cpp
void copy_strings()
{
   String str1("I have a sense of impending disaster...");
   String str2 = str1; // str1.text and str2.text now refer to the same object
} // delete[] _text; deallocates the same memory twice
  // undefined behavior
```

La définition explicite d’un destructeur, d’un constructeur de copie ou d’un opérateur d’assignation de copie empêche la définition implicite du constructeur de déplacement et de l’opérateur d’assignation de déplacement. Dans ce cas, le fait de ne pas fournir d’opérations de déplacement est généralement, si la copie est coûteuse, une opportunité d’optimisation manquée.

## <a name="see-also"></a>Voir aussi

[Constructeurs de copie et opérateurs d’assignation de copie](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)</br>
[Constructeurs de déplacement et opérateurs d’assignation de déplacement](../cpp/move-constructors-and-move-assignment-operators-cpp.md)
