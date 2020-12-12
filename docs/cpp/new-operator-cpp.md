---
description: 'En savoir plus sur : nouvel opérateur (C++)'
title: new, opérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 5bfc6fdc59348defc87d26dae1056ae80dab3ec5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268624"
---
# <a name="new-operator-c"></a>new, opérateur (C++)

Alloue de la mémoire pour un objet ou un tableau d’objets de *type-name* à partir du magasin gratuit et retourne un pointeur de type différent de zéro et typé approprié à l’objet.

> [!NOTE]
> Les extensions de composant Microsoft C++ prennent en charge le **`new`** mot clé pour ajouter des entrées d’emplacement vtable. Pour plus d’informations, voir [New (nouvel emplacement dans vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

## <a name="syntax"></a>Syntaxe

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Notes

En cas d’échec, **`new`** retourne zéro ou lève une exception ; consultez [les opérateurs New et Delete](../cpp/new-and-delete-operators.md) pour plus d’informations. Vous pouvez modifier ce comportement par défaut en écrivant une routine de gestion des exceptions personnalisée et en appelant la fonction de la bibliothèque Runtime [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) avec le nom de votre fonction comme argument.

Pour plus d’informations sur la création d’un objet sur le tas managé, consultez [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Lorsque **`new`** est utilisé pour allouer de la mémoire pour un objet de classe C++, le constructeur de l’objet est appelé après que la mémoire a été allouée.

Utilisez l’opérateur [Delete](../cpp/delete-operator-cpp.md) pour libérer la mémoire allouée avec l' **`new`** opérateur.

L'exemple suivant alloue, puis libère un tableau de caractères à deux dimensions de taille `dim` par 10. En allouant un tableau multidimensionnel, toutes les dimensions sauf la première doivent être des expressions constantes qui s'analysent comme valeurs positives ; la dimension du tableau la plus à gauche peut être une expression qui s'analyse comme valeur positive. Lors de l’allocation d’un tableau à l’aide de l' **`new`** opérateur, la première dimension peut être zéro : l' **`new`** opérateur retourne un pointeur unique.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

Le *nom de type* ne peut pas contenir les **`const`** **`volatile`** déclarations,, de classe ou d’énumération. Par conséquent, l'expression suivante n'est pas conforme :

```cpp
volatile char *vch = new volatile char[20];
```

L' **`new`** opérateur n’alloue pas de types référence, car il ne s’agit pas d’objets.

L' **`new`** opérateur ne peut pas être utilisé pour allouer une fonction, mais il peut être utilisé pour allouer des pointeurs aux fonctions. L'exemple suivant alloue, puis libère un tableau de sept pointeurs vers des fonctions qui retournent des entiers.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Si vous utilisez l’opérateur **`new`** sans arguments supplémentaires, et que vous compilez avec l’option [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)ou [/EHS](../build/reference/eh-exception-handling-model.md) , le compilateur génère du code pour appeler l’opérateur **`delete`** si le constructeur lève une exception.

La liste suivante décrit les éléments de grammaire de **`new`** :

*importation*<br/>
Fournit un moyen de passer des arguments supplémentaires si vous surchargez **`new`** .

*nom du type*<br/>
Spécifie le type à allouer ; il peut s'agir d'un type intégré ou d'un type défini par l'utilisateur. Si la spécification de type est compliquée, elle peut être placée entre parenthèses pour forcer l'ordre de liaison.

*initializer*<br/>
Fournit une valeur pour l'objet initialisé. Les initialiseurs ne peuvent pas être spécifiés pour des tableaux. L' **`new`** opérateur crée des tableaux d’objets uniquement si la classe a un constructeur par défaut.

## <a name="example-allocate-and-free-a-character-array"></a>Exemple : allouer et libérer un tableau de caractères

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

## <a name="example-new-operator"></a>Exemple : `new` opérateur

Si vous utilisez la nouvelle forme positionnement de l' **`new`** opérateur, le formulaire avec des arguments en plus de la taille de l’allocation, le compilateur ne prend pas en charge une forme de placement de l' **`delete`** opérateur si le constructeur lève une exception. Par exemple :

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

Un champ d' *initialiseur* facultatif est inclus dans la grammaire de l' **`new`** opérateur. Cela permet aux nouveaux objets d'être initialisés avec les constructeurs définis par l'utilisateur. Pour plus d’informations sur la façon dont l’initialisation est effectuée, consultez [initialiseurs](../cpp/initializers.md). L’exemple suivant illustre l’utilisation d’une expression d’initialisation avec l' **`new`** opérateur :

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

Dans cet exemple, l’objet `CheckingAcct` est alloué à l’aide de l' **`new`** opérateur, mais aucune initialisation par défaut n’est spécifiée. Par conséquent, le constructeur par défaut pour la classe, `Acct()`, est appelé. Puis l'objet `SavingsAcct` est alloué de la même façon, mais il est initialisé explicitement à 34,98. Étant donné que 34,98 est de type **`double`** , le constructeur qui accepte un argument de ce type est appelé pour gérer l’initialisation. Enfin, le type sans classe `HowMuch` est initialisé à 43,0.

Si un objet est d’un type de classe et que cette classe a des constructeurs (comme dans l’exemple précédent), l’objet peut être initialisé par l' **`new`** opérateur uniquement si l’une des conditions suivantes est remplie :

- Les arguments fournis dans l’initialiseur sont conformes à ceux d’un constructeur.

- La classe possède un constructeur par défaut (un constructeur pouvant être appelé sans argument).

Aucune initialisation explicite par élément ne peut être effectuée lors de l’allocation de tableaux à l’aide de l' **`new`** opérateur ; seul le constructeur par défaut, s’il est présent, est appelé. Pour plus d’informations, consultez [arguments par défaut](../cpp/default-arguments.md) .

Si l’allocation de mémoire échoue (**operator new** retourne la valeur 0), aucune initialisation n’est effectuée. Cela empêche les tentatives d'initialisation de données qui n'existent pas.

Comme avec les appels de fonction, l'ordre dans lequel les expressions initialisées sont évaluées n'est pas défini. En outre, vous ne devez pas vous attendre à ce que ces expressions soient complètement évaluées avant que l'allocation de mémoire soit exécutée. Si l’allocation de mémoire échoue et que l' **`new`** opérateur retourne la valeur zéro, certaines expressions de l’initialiseur ne peuvent pas être complètement évaluées.

## <a name="lifetime-of-objects-allocated-with-new"></a>Durée de vie des objets alloués avec new

Les objets alloués avec l' **`new`** opérateur ne sont pas détruits lors de la sortie de l’étendue dans laquelle ils sont définis. Étant donné que l' **`new`** opérateur retourne un pointeur vers les objets qu’il alloue, le programme doit définir un pointeur avec une portée appropriée pour accéder à ces objets. Par exemple :

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

L' *expression d’allocation* (l’expression contenant l' **`new`** opérateur) effectue trois opérations :

- Localise et réserve le stockage pour les objets à allouer. Lorsque cette étape est terminée, la quantité correcte d'espace de stockage est allouée, mais ce n'est pas encore un objet.

- Initialise les objets. Une fois que l'initialisation est terminée, les informations disponibles sont suffisantes pour que le stockage alloué soit un objet.

- Retourne un pointeur vers le ou les objets d’un type pointeur dérivé de *New-type-name* ou *type-name*. Le programme utilise ce pointeur pour accéder au nouvel objet alloué.

L' **`new`** opérateur appelle la fonction **operator new**. Pour les tableaux de tout type, et pour les objets qui ne sont pas de type **`class`** , **`struct`** ou **`union`** , une fonction globale, **:: operator new**, est appelée pour allouer le stockage. Les objets de type classe peuvent définir leur propre **opérateur** de fonction membre statique pour chaque classe.

Lorsque le compilateur rencontre l' **`new`** opérateur pour allouer un objet de **type type**, il émet un appel à `type` **:: operator new (sizeof (** `type` **))** ou, si aucun opérateur défini par l’utilisateur **New** n’est défini, **:: operator new (sizeof (** `type` **))**. Par conséquent, l' **`new`** opérateur peut allouer la quantité de mémoire correcte pour l’objet.

> [!NOTE]
> L’argument de l' **opérateur New** est de type `size_t` . Ce type est défini dans \<direct.h> , \<malloc.h> , \<memory.h> , \<search.h> , \<stddef.h> , \<stdio.h> , \<stdlib.h> , \<string.h> et \<time.h> .

Une option dans la grammaire permet de spécifier le *placement* (voir la grammaire pour l' [opérateur New](../cpp/new-operator-cpp.md)). Le paramètre *placement* ne peut être utilisé que pour les implémentations définies par l’utilisateur de **operator new**. Il permet de passer des informations supplémentaires à **operator new**. Une expression avec un champ d' *emplacement* tel que `T *TObject = new ( 0x0040 ) T;` est traduite en `T *TObject = T::operator new( sizeof( T ), 0x0040 );` si la classe T a un opérateur membre New, sinon pour `T *TObject = ::operator new( sizeof( T ), 0x0040 );` .

L’objectif initial du champ d' *emplacement* était de permettre l’allocation des objets dépendants du matériel aux adresses spécifiées par l’utilisateur.

> [!NOTE]
> Bien que l’exemple précédent n’affiche qu’un seul argument dans le champ *placement* , il n’existe aucune restriction quant au nombre d’arguments supplémentaires qui peuvent être passés à **operator new** de cette façon.

Même lorsque l' **opérateur New** a été défini pour un type de classe, l’opérateur global peut être utilisé à l’aide de la forme de cet exemple :

```cpp
T *TObject =::new TObject;
```

L’opérateur de résolution de portée ( `::` ) force l’utilisation de l' **`new`** opérateur global.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Opérateurs new et delete](../cpp/new-and-delete-operators.md)
