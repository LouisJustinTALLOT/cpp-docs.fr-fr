---
title: new, opérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367873"
---
# <a name="new-operator-c"></a>new, opérateur (C++)

Alloue la mémoire pour un objet ou un tableau d’objets de *type-nom* du magasin gratuit et renvoie un pointeur non zéro convenablement tapé à l’objet.

> [!NOTE]
> Les extensions de composants Microsoft CMD prennent en charge le **nouveau** mot clé pour ajouter des entrées de fente vtables. Pour plus d’informations, voir [nouveau (nouveau créneau dans vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Syntaxe

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Notes

En cas d’échec, **les nouveaux** renvois zéro ou jette une exception; voir [The new and delete Operators](../cpp/new-and-delete-operators.md) pour plus d’informations. Vous pouvez modifier ce comportement par défaut en écrivant une routine personnalisée de manipulation d’exception et en appelant la fonction de bibliothèque [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) en temps d’exécution avec votre nom de fonction comme argument.

Pour plus d’informations sur la façon de créer un objet sur le tas géré, voir [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Lorsque **de nouveaux** sont utilisés pour allouer la mémoire d’un objet de classe C, le constructeur de l’objet est appelé après l’attribution de la mémoire.

Utilisez l’opérateur [de suppression](../cpp/delete-operator-cpp.md) pour traiter la mémoire allouée au **nouvel** opérateur.

L'exemple suivant alloue, puis libère un tableau de caractères à deux dimensions de taille `dim` par 10. En allouant un tableau multidimensionnel, toutes les dimensions sauf la première doivent être des expressions constantes qui s'analysent comme valeurs positives ; la dimension du tableau la plus à gauche peut être une expression qui s'analyse comme valeur positive. Lors de l’attribution d’un tableau à l’aide du **nouvel** opérateur, la première dimension peut être nulle - le **nouvel** opérateur retourne un pointeur unique.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

Le *nom de type* ne peut pas contenir de **const,** **volatile,** déclarations de classe, ou déclarations d’énumération. Par conséquent, l'expression suivante n'est pas conforme :

```cpp
volatile char *vch = new volatile char[20];
```

Le **nouvel** opérateur n’alloue pas de types de référence parce qu’ils ne sont pas des objets.

Le **nouvel** opérateur ne peut pas être utilisé pour attribuer une fonction, mais il peut être utilisé pour allouer des pointeurs aux fonctions. L'exemple suivant alloue, puis libère un tableau de sept pointeurs vers des fonctions qui retournent des entiers.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Si vous utilisez l’opérateur **nouveau** sans aucun argument supplémentaire, et compilez avec le [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), ou [/EHs](../build/reference/eh-exception-handling-model.md) option, le compilateur générera du code pour appeler l’opérateur **supprimer** si le constructeur jette une exception.

La liste suivante décrit les éléments de grammaire des **nouveaux**:

*Placement*<br/>
Fournit un moyen de passer des arguments supplémentaires si vous surchargez **de nouveaux**.

*nom de type*<br/>
Spécifie le type à allouer ; il peut s'agir d'un type intégré ou d'un type défini par l'utilisateur. Si la spécification de type est compliquée, elle peut être placée entre parenthèses pour forcer l'ordre de liaison.

*initializer*<br/>
Fournit une valeur pour l'objet initialisé. Les initialiseurs ne peuvent pas être spécifiés pour des tableaux. Le **nouvel** opérateur ne créera des tableaux d’objets que si la classe a un constructeur par défaut.

## <a name="example"></a>Exemple

L'exemple de code suivant alloue un tableau de caractères et un objet de classe `CName`, puis les libère.

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>Exemple

Si vous utilisez le nouveau formulaire de placement du **nouvel** opérateur, le formulaire avec des arguments en plus de la taille de l’allocation, le compilateur ne prend pas en charge un formulaire de placement de l’opérateur de **suppression** si le constructeur lance une exception. Par exemple :

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>Initialisation des objets alloués avec new

Un champ *initialisateur* optionnel est inclus dans la grammaire pour le **nouvel** opérateur. Cela permet aux nouveaux objets d'être initialisés avec les constructeurs définis par l'utilisateur. Pour plus d’informations sur la façon dont l’initialisation est faite, voir [Initializers](../cpp/initializers.md). L’exemple suivant illustre comment utiliser une expression d’initialisation avec le **nouvel** opérateur :

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

Dans cet exemple, `CheckingAcct` l’objet est attribué à l’aide du **nouvel** opérateur, mais aucune initialisation par défaut n’est spécifiée. Par conséquent, le constructeur par défaut pour la classe, `Acct()`, est appelé. Puis l'objet `SavingsAcct` est alloué de la même façon, mais il est initialisé explicitement à 34,98. Parce que 34.98 est de type **double**, le constructeur qui prend un argument de ce type est appelé à gérer l’initialisation. Enfin, le type sans classe `HowMuch` est initialisé à 43,0.

Si un objet est d’un type de classe et que cette classe a des constructeurs (comme dans l’exemple précédent), l’objet ne peut être para initialisé par le **nouvel** opérateur que si l’une de ces conditions est remplie :

- Les arguments fournis dans l’initialiseur sont conformes à ceux d’un constructeur.

- La classe possède un constructeur par défaut (un constructeur pouvant être appelé sans argument).

Aucune initialisation explicite par élément ne peut être faite lors de l’attribution des tableaux à l’aide du **nouvel** opérateur; seul le constructeur par défaut, s’il est présent, est appelé. Voir [Arguments par défaut](../cpp/default-arguments.md) pour plus d’informations.

Si l’allocation de mémoire échoue **(opérateur nouveau** retourne une valeur de 0), aucune initialisation n’est effectuée. Cela empêche les tentatives d'initialisation de données qui n'existent pas.

Comme avec les appels de fonction, l'ordre dans lequel les expressions initialisées sont évaluées n'est pas défini. En outre, vous ne devez pas vous attendre à ce que ces expressions soient complètement évaluées avant que l'allocation de mémoire soit exécutée. Si l’allocation de mémoire échoue et que le **nouvel** opérateur retourne zéro, certaines expressions dans l’initialisateur peuvent ne pas être complètement évaluées.

## <a name="lifetime-of-objects-allocated-with-new"></a>Durée de vie des objets alloués avec new

Les objets attribués au **nouvel** opérateur ne sont pas détruits lorsque la portée dans laquelle ils sont définis est sortie. Étant donné que le **nouvel** opérateur retourne un pointeur aux objets qu’il attribue, le programme doit définir un pointeur avec une portée appropriée pour accéder à ces objets. Par exemple :

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

Une fois que le pointeur `AnotherArray` sort de la portée de l'exemple, l'objet ne peut plus être supprimé.

## <a name="how-new-works"></a>Fonctionnement de new

*L’expression d’allocation* — l’expression contenant le **nouvel** opérateur — fait trois choses :

- Localise et réserve le stockage pour les objets à allouer. Lorsque cette étape est terminée, la quantité correcte d'espace de stockage est allouée, mais ce n'est pas encore un objet.

- Initialise les objets. Une fois que l'initialisation est terminée, les informations disponibles sont suffisantes pour que le stockage alloué soit un objet.

- Retourne un pointeur à l’objet (s) d’un type de pointeur dérivé *d’un nouveau type de nom* ou de type *nom*. Le programme utilise ce pointeur pour accéder au nouvel objet alloué.

Le **nouvel** opérateur invoque l’opérateur de fonction **nouveau**. Pour les tableaux de tout type, et pour les objets qui ne sont pas de **classe,** **struct**, ou types **d’union,** une fonction globale, **::opérateur nouveau**, est appelé à allouer le stockage. Les objets de type classe peuvent définir leur propre **opérateur nouvelle** fonction de membre statique sur une base par classe.

Lorsque le compilateur rencontre le **nouvel** opérateur pour allouer un `type`objet de **type**type, il émet un appel à **::opérateur nouveau (** `type` **taille) )** ou, si aucun opérateur défini par l’utilisateur **nouveau** est défini, **::opérateur nouveau ( taille de** `type` ) **.** Par conséquent, le **nouvel** opérateur peut allouer la quantité correcte de mémoire pour l’objet.

> [!NOTE]
> L’argument de **l’opérateur nouveau** est de type `size_t`. Ce type est \<défini \<en direct.h>, \<malloc.h>, memory.h \<>, search.h \<>, stddef.h \<>, stdio.h \<>, stdlib.h>, \<string.h>, \<et time.h>.

Une option dans la grammaire permet la spécification du *placement* (voir la grammaire pour [le nouvel opérateur](../cpp/new-operator-cpp.md)). Le *paramètre de placement* ne peut être utilisé que pour les implémentations définies par l’utilisateur des nouveaux **opérateurs**; il permet de transmettre des informations supplémentaires à **l’opérateur nouveau**. Une expression avec un `T *TObject = new ( 0x0040 ) T;` champ de `T *TObject = T::operator new( sizeof( T ), 0x0040 );` *placement* tel que est traduite `T *TObject = ::operator new( sizeof( T ), 0x0040 );`si la classe T a l’opérateur membre nouveau, sinon à .

L’intention initiale du champ de *placement* était de permettre l’attribution d’objets dépendants du matériel aux adresses spécifiées par l’utilisateur.

> [!NOTE]
> Bien que l’exemple précédent ne montre qu’un seul argument dans le domaine du *placement,* il n’y a aucune restriction quant au nombre d’arguments supplémentaires qui peuvent être transmis à **l’opérateur de nouveau** de cette façon.

Même lorsque **l’opérateur nouveau** a été défini pour un type de classe, l’opérateur mondial peut être utilisé en utilisant la forme de cet exemple :

```cpp
T *TObject =::new TObject;
```

L’opérateur de`::`résolution de portée ( ) force l’utilisation du **nouvel** opérateur mondial.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[nouveaux opérateurs et supprimer](../cpp/new-and-delete-operators.md)
