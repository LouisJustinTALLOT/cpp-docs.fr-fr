---
title: Opérateurs new et delete
description: Les opérateurs New et Delete du langage C++ permettent de contrôler l’allocation.
ms.date: 07/07/2020
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.openlocfilehash: e609d1fdbd4f945ab8709c554d1396100027c4c1
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127862"
---
# <a name="new-and-delete-operators"></a>Opérateurs `new` et `delete`

C++ prend en charge l’allocation et la désallocation dynamiques d’objets à l’aide des [`new`](new-operator-cpp.md) [`delete`](delete-operator-cpp.md) opérateurs et. Ces opérateurs allouent de la mémoire pour les objets à partir d'un pool appelé magasin gratuit. L' **`new`** opérateur appelle la fonction spéciale [`operator new`](new-operator-cpp.md) et l' **`delete`** opérateur appelle la fonction spéciale [`operator delete`](delete-operator-cpp.md) .

La **`new`** fonction de la bibliothèque C++ standard prend en charge le comportement spécifié dans la norme c++, qui consiste à lever une `std::bad_alloc` exception en cas d’échec de l’allocation de mémoire. Si vous souhaitez toujours la version sans déclenchement de **`new`** , liez votre programme à *`nothrownew.obj`* . Toutefois, lorsque vous liez avec *`nothrownew.obj`* , la valeur par défaut **`operator new`** de la bibliothèque C++ standard ne fonctionne plus.

Pour obtenir la liste des fichiers de bibliothèque de la bibliothèque Runtime C et de la bibliothèque C++ standard, consultez fonctionnalités de la [bibliothèque CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> `new` Opérateur

Le compilateur traduit une instruction telle que celle-ci en un appel à la fonction **`operator new`** :

```cpp
char *pch = new char[BUFFER_SIZE];
```

Si la demande concerne un espace de stockage de zéro octet, **`operator new`** retourne un pointeur vers un objet distinct. Autrement dit, les appels répétés pour **`operator new`** retourner des pointeurs différents. Si la mémoire est insuffisante pour la demande d’allocation, **`operator new`** lève une `std::bad_alloc` exception. Ou retourne **`nullptr`** si vous avez lié à la prise en charge de la non-levée **`operator new`** .

Vous pouvez écrire une routine qui tente de libérer de la mémoire et retenter l’allocation. Pour plus d’informations, consultez [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md). Pour plus d’informations sur le mode de récupération, consultez la section gestion de la [mémoire insuffisante](#handling-insufficient-memory) .

Les deux étendues des **`operator new`** fonctions sont décrites dans le tableau suivant.

### <a name="scope-for-operator-new-functions"></a>Portée des `operator new` fonctions

| Opérateur | Étendue |
|--|--|
| **`::operator new`** | Global |
| *nom de classe***`::operator new`** | Classe |

Le premier argument de **`operator new`** doit être de type `size_t` , défini dans \<stddef.h> , et le type de retour est toujours **`void*`** .

La **`operator new`** fonction globale est appelée lorsque l' **`new`** opérateur est utilisé pour allouer des objets de types intégrés, des objets de type classe qui ne contiennent pas de **`operator new`** fonctions définies par l’utilisateur et des tableaux de tout type. Lorsque l' **`new`** opérateur est utilisé pour allouer des objets d’un type de classe où un **`operator new`** est défini, cette classe **`operator new`** est appelée.

Une **`operator new`** fonction définie pour une classe est une fonction membre statique (qui ne peut pas être virtuelle) qui masque la **`operator new`** fonction globale pour les objets de ce type de classe. Considérez le cas où **`new`** est utilisé pour allouer et définir la mémoire à une valeur donnée :

```cpp
#include <malloc.h>
#include <memory.h>

class Blanks
{
public:
    Blanks(){}
    void *operator new( size_t stAllocateBlock, char chInit );
};
void *Blanks::operator new( size_t stAllocateBlock, char chInit )
{
    void *pvTemp = malloc( stAllocateBlock );
    if( pvTemp != 0 )
        memset( pvTemp, chInit, stAllocateBlock );
    return pvTemp;
}
// For discrete objects of type Blanks, the global operator new function
// is hidden. Therefore, the following code allocates an object of type
// Blanks and initializes it to 0xa5
int main()
{
   Blanks *a5 = new(0xa5) Blanks;
   return a5 != 0;
}
```

L’argument fourni entre parenthèses à **`new`** est passé à `Blanks::operator new` comme `chInit` argument. Toutefois, la **`operator new`** fonction globale est masquée, ce qui provoque la génération d’un code tel que le suivant pour générer une erreur :

```cpp
Blanks *SomeBlanks = new Blanks;
```

Le compilateur prend en charge les opérateurs et le tableau membres **`new`** **`delete`** dans une déclaration de classe. Par exemple :

```cpp
class MyClass
{
public:
   void * operator new[] (size_t)
   {
      return 0;
   }
   void   operator delete[] (void*)
   {
   }
};

int main()
{
   MyClass *pMyClass = new MyClass[5];
   delete [] pMyClass;
}
```

### <a name="handling-insufficient-memory"></a>Gestion d'une mémoire insuffisante

Le test de l’allocation de mémoire en échec peut être effectué comme indiqué ici :

```cpp
#include <iostream>
using namespace std;
#define BIG_NUMBER 100000000
int main() {
   int *pI = new int[BIG_NUMBER];
   if( pI == 0x0 ) {
      cout << "Insufficient memory" << endl;
      return -1;
   }
}
```

Il existe une autre façon de gérer les demandes d’allocation de mémoire qui ont échoué. Écrivez une routine de récupération personnalisée pour gérer un tel échec, puis enregistrez votre fonction en appelant la [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md) fonction Runtime.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> `delete` Opérateur

La mémoire allouée dynamiquement à l’aide de l' **`new`** opérateur peut être libérée à l’aide de l' **`delete`** opérateur. L’opérateur delete appelle la **`operator delete`** fonction, qui libère de la mémoire dans le pool disponible. L’utilisation de l' **`delete`** opérateur entraîne également l’appel du destructeur de classe (s’il en existe un).

Il existe des fonctions globales et de portée de classe **`operator delete`** . Une seule **`operator delete`** fonction peut être définie pour une classe donnée ; si elle est définie, elle masque la **`operator delete`** fonction globale. La **`operator delete`** fonction globale est toujours appelée pour les tableaux de tout type.

Fonction globale **`operator delete`** . Deux formes existent pour les fonctions globales **`operator delete`** et les fonctions membres de classe **`operator delete`** :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Seul l’un des deux formulaires ci-dessus peut être présent pour une classe donnée. Le premier formulaire accepte un argument unique de type **`void *`** , qui contient un pointeur vers l’objet à libérer. La deuxième forme, la désallocation dimensionnée, prend deux arguments : le premier est un pointeur vers le bloc de mémoire à libérer et le second est le nombre d’octets à libérer. Le type de retour des deux formes est **`void`** ( **`operator delete`** ne peut pas retourner de valeur).

L’objectif de la deuxième forme est d’accélérer la recherche de la catégorie de taille correcte de l’objet à supprimer. Ces informations ne sont généralement pas stockées près de l’allocation elle-même et sont probablement non mises en cache. La deuxième forme est utile quand une **`operator delete`** fonction d’une classe de base est utilisée pour supprimer un objet d’une classe dérivée.

La **`operator delete`** fonction est statique. elle ne peut donc pas être virtuelle. La **`operator delete`** fonction obéit au contrôle d’accès, comme décrit dans [Access Control membres](member-access-control-cpp.md).

L’exemple suivant montre les fonctions définies par l’utilisateur **`operator new`** et **`operator delete`** conçues pour consigner les allocations et les désallocations de mémoire :

```cpp
#include <iostream>
using namespace std;

int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?
int cBlocksAllocated = 0;  // Count of blocks allocated.

// User-defined operator new.
void *operator new( size_t stAllocateBlock ) {
   static int fInOpNew = 0;   // Guard flag.

   if ( fLogMemory && !fInOpNew ) {
      fInOpNew = 1;
      clog << "Memory block " << ++cBlocksAllocated
          << " allocated for " << stAllocateBlock
          << " bytes\n";
      fInOpNew = 0;
   }
   return malloc( stAllocateBlock );
}

// User-defined operator delete.
void operator delete( void *pvMem ) {
   static int fInOpDelete = 0;   // Guard flag.
   if ( fLogMemory && !fInOpDelete ) {
      fInOpDelete = 1;
      clog << "Memory block " << cBlocksAllocated--
          << " deallocated\n";
      fInOpDelete = 0;
   }

   free( pvMem );
}

int main( int argc, char *argv[] ) {
   fLogMemory = 1;   // Turn logging on
   if( argc > 1 )
      for( int i = 0; i < atoi( argv[1] ); ++i ) {
         char *pMem = new char[10];
         delete[] pMem;
      }
   fLogMemory = 0;  // Turn logging off.
   return cBlocksAllocated;
}
```

Le code précédent peut être utilisé pour détecter la « fuite de mémoire », c’est-à-dire la mémoire allouée sur le magasin libre mais jamais libérée. Pour détecter les fuites, les **`new`** opérateurs global et **`delete`** sont redéfinis pour compter l’allocation et la désallocation de mémoire.

Le compilateur prend en charge les opérateurs et le tableau membres **`new`** **`delete`** dans une déclaration de classe. Par exemple :

```cpp
// spec1_the_operator_delete_function2.cpp
// compile with: /c
class X  {
public:
   void * operator new[] (size_t) {
      return 0;
   }
   void operator delete[] (void*) {}
};

void f() {
   X *pX = new X[5];
   delete [] pX;
}
```
