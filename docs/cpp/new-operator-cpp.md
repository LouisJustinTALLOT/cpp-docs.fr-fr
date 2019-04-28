---
title: new, opérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: bcb7784e59966510970bd9b3ae0157ae982e462d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245385"
---
# <a name="new-operator-c"></a>new, opérateur (C++)

Alloue de la mémoire pour un objet ou un tableau d’objets de *type-name* du magasin gratuit et retourne un pointeur différent de zéro, correctement typé vers l’objet.

> [!NOTE]
>  Microsoft C++ Component Extensions fournit la prise en charge pour le **nouveau** mot clé pour ajouter des entrées d’emplacement vtable. Pour plus d’informations, consultez [new (nouvel emplacement dans vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Syntaxe

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Notes

En cas d’échec, **nouveau** retourne zéro ou lève une exception ; consultez [le nouveau et supprimer des opérateurs](../cpp/new-and-delete-operators.md) pour plus d’informations. Vous pouvez modifier ce comportement par défaut en écrivant une routine de gestion des exceptions personnalisée et en appelant le [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) fonction de bibliothèque du run-time avec votre nom de fonction comme argument.

Pour plus d’informations sur la création d’un objet sur le tas managé, consultez [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Lorsque **nouveau** est utilisé pour allouer de la mémoire pour un objet de classe C++, constructeur de l’objet est appelé une fois que la mémoire est allouée.

Utilisez le [supprimer](../cpp/delete-operator-cpp.md) opérateur pour libérer la mémoire allouée avec la **nouveau** opérateur.

L'exemple suivant alloue, puis libère un tableau de caractères à deux dimensions de taille `dim` par 10. En allouant un tableau multidimensionnel, toutes les dimensions sauf la première doivent être des expressions constantes qui s'analysent comme valeurs positives ; la dimension du tableau la plus à gauche peut être une expression qui s'analyse comme valeur positive. Lors de l’allocation d’un tableau à l’aide la **nouveau** opérateur, la première dimension peut être égal à zéro, le **nouveau** opérateur retourne un pointeur unique.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

Le *type-name* ne peut pas contenir **const**, **volatile**, déclarations de classe ou des déclarations d’énumération. Par conséquent, l'expression suivante n'est pas conforme :

```cpp
volatile char *vch = new volatile char[20];
```

Le **nouveau** opérateur n’alloue pas de types référence, car ils ne sont pas des objets.

Le **nouveau** opérateur ne peut pas être utilisé pour allouer une fonction, mais il peut être utilisé pour allouer des pointeurs vers des fonctions. L'exemple suivant alloue, puis libère un tableau de sept pointeurs vers des fonctions qui retournent des entiers.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Si vous utilisez l’opérateur **nouveau** sans arguments supplémentaires et compilez avec le [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), ou [/EHs](../build/reference/eh-exception-handling-model.md) option, le compilateur va générer du code pour appeler l’opérateur **supprimer** si le constructeur lève une exception.

La liste suivante décrit les éléments de grammaire de **nouveau**:

*placement*<br/>
Offre un moyen de passer des arguments supplémentaires si vous surchargez **nouveau**.

*type-name*<br/>
Spécifie le type à allouer ; il peut s'agir d'un type intégré ou d'un type défini par l'utilisateur. Si la spécification de type est compliquée, elle peut être placée entre parenthèses pour forcer l'ordre de liaison.

*initializer*<br/>
Fournit une valeur pour l'objet initialisé. Les initialiseurs ne peuvent pas être spécifiés pour des tableaux. Le **nouveau** opérateur crée des tableaux d’objets uniquement si la classe a un constructeur par défaut.

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

Si vous utilisez la nouvelle forme positionnement de la **nouveau** opérateur, la forme avec arguments en plus de la taille de l’allocation, le compilateur ne prend pas en charge une forme positionnement de la **supprimer** opérateur si les constructeur lève une exception. Exemple :

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

Facultatif *initialiseur* champ est inclus dans la grammaire pour le **nouveau** opérateur. Cela permet aux nouveaux objets d'être initialisés avec les constructeurs définis par l'utilisateur. Pour plus d’informations sur la façon dont l’initialisation est effectuée, consultez [initialiseurs](../cpp/initializers.md). L’exemple suivant illustre comment utiliser une expression d’initialisation avec le **nouveau** opérateur :

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

Dans cet exemple, l’objet `CheckingAcct` est allouée en utilisant le **nouveau** opérateur, mais aucune initialisation par défaut est spécifié. Par conséquent, le constructeur par défaut pour la classe, `Acct()`, est appelé. Puis l'objet `SavingsAcct` est alloué de la même façon, mais il est initialisé explicitement à 34,98. Comme 34,98 est du type **double**, le constructeur qui accepte un argument de ce type est appelé pour traiter l’initialisation. Enfin, le type sans classe `HowMuch` est initialisé à 43,0.

Si un objet est d’un type de classe, et cette classe a des constructeurs (comme dans l’exemple précédent), l’objet peut être initialisé par le **nouveau** opérateur uniquement si une des conditions suivantes est remplie :

- Les arguments fournis dans l’initialiseur sont conformes à ceux d’un constructeur.

- La classe possède un constructeur par défaut (un constructeur pouvant être appelé sans argument).

Aucune initialisation explicite par élément ne peut être effectuée en allouant des tableaux à l’aide de la **nouveau** opérateur ; uniquement le constructeur par défaut, le cas échéant, est appelée. Consultez [Arguments par défaut](../cpp/default-arguments.md) pour plus d’informations.

Si l’allocation de mémoire échoue (**opérateur new** retourne une valeur de 0), aucune initialisation n’est effectuée. Cela empêche les tentatives d'initialisation de données qui n'existent pas.

Comme avec les appels de fonction, l'ordre dans lequel les expressions initialisées sont évaluées n'est pas défini. En outre, vous ne devez pas vous attendre à ce que ces expressions soient complètement évaluées avant que l'allocation de mémoire soit exécutée. Si l’allocation de mémoire échoue et le **nouveau** opérateur retourne la valeur zéro, certaines expressions dans l’initialiseur ne peuvent pas être évaluées complètement.

## <a name="lifetime-of-objects-allocated-with-new"></a>Durée de vie des objets alloués avec new

Objets alloués avec le **nouveau** opérateur ne sont pas détruits lorsque vous quittez la portée dans laquelle elles sont définies. Étant donné que le **nouveau** opérateur retourne un pointeur vers les objets qu’il alloue, le programme doit définir un pointeur avec une portée appropriée pour accéder à ces objets. Exemple :

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

Le *allocation-expression* : l’expression contenant le **nouveau** opérateur — effectue trois opérations :

- Localise et réserve le stockage pour les objets à allouer. Lorsque cette étape est terminée, la quantité correcte d'espace de stockage est allouée, mais ce n'est pas encore un objet.

- Initialise les objets. Une fois que l'initialisation est terminée, les informations disponibles sont suffisantes pour que le stockage alloué soit un objet.

- Retourne un pointeur vers les objets d’un type pointeur dérivé *new-type-name* ou *type-name*. Le programme utilise ce pointeur pour accéder au nouvel objet alloué.

Le **nouveau** opérateur appelle la fonction **opérateur new**. Pour les tableaux de n’importe quel type et pour les objets qui ne sont pas de **classe**, **struct**, ou **union** types, une fonction globale, **:: opérateur new**, est appelé pour allouer le stockage. Les objets de type de classe peuvent définir leurs propres **opérateur new** fonction membre statique sur une base par classe.

Lorsque le compilateur rencontre la **nouveau** opérateur pour allouer un objet de type **type**, il émet un appel à `type` **:: opérateur new (sizeof (** `type` **))** ou, si non défini par l’utilisateur **opérateur new** est défini, **:: opérateur new (sizeof (** `type` **))**. Par conséquent, le **nouveau** opérateur peut allouer la quantité correcte de mémoire pour l’objet.

> [!NOTE]
>  L’argument **opérateur new** est de type `size_t`. Ce type est défini dans \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, et \<time.h >.

Une option dans la grammaire autorise la spécification de *placement* (consultez la grammaire pour [nouvel opérateur](../cpp/new-operator-cpp.md)). Le *placement* paramètre peut être utilisé uniquement pour les implémentations définies par l’utilisateur de **opérateur new**; il permet d’obtenir des informations supplémentaires à passer à **opérateur new**. Une expression avec un *placement* champ comme `T *TObject = new ( 0x0040 ) T;` est traduite en `T *TObject = T::operator new( sizeof( T ), 0x0040 );` si la classe T comporte un opérateur membre new, sinon à `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.

L’intention d’origine de la *placement* champ a été pour permettre aux objets dépendent du matériel à allouer à des adresses spécifiées par l’utilisateur.

> [!NOTE]
>  Bien que l’exemple précédent ne montre qu’un seul argument dans le *placement* champ, il n’existe aucune restriction sur le nombre d’arguments supplémentaires peut être passé à **opérateur new** de cette façon.

Même lorsque **opérateur new** a été défini pour un type de classe, l’opérateur global peut être utilisé à l’aide de la forme de cet exemple :

```cpp
T *TObject =::new TObject;
```

L’opérateur de résolution de portée (`::`) force l’utilisation de global **nouveau** opérateur.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[nouveau et supprimer des opérateurs](../cpp/new-and-delete-operators.md)