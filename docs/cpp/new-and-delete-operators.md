---
title: Opérateurs new et delete
ms.date: 11/19/2019
f1_keywords:
- delete_cpp
- new
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: c64b15f1e1e63b1e743743883429ffd11007de0a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246451"
---
# <a name="new-and-delete-operators"></a>Opérateurs new et delete

C++prend en charge l’allocation dynamique et la désallocation d’objets à l’aide des opérateurs [New](new-operator-cpp.md) et [Delete](delete-operator-cpp.md) . Ces opérateurs allouent de la mémoire pour les objets à partir d'un pool appelé magasin gratuit. Le **nouvel** opérateur appelle la fonction spéciale [operator new](new-operator-cpp.md), et l’opérateur **Delete** appelle la fonction spéciale [Delete](delete-operator-cpp.md).

La **nouvelle** fonction dans la C++ bibliothèque standard prend en charge le comportement spécifié C++ dans la norme, qui consiste à lever une exception std :: bad_alloc si l’allocation de mémoire échoue. Si vous souhaitez toujours la version sans déclenchement de la **nouvelle**, liez votre programme à nothrownew. obj. Toutefois, lorsque vous liez nothrownew. obj, l’opérateur par défaut **New** dans la C++ bibliothèque standard ne fonctionne plus.

Pour obtenir la liste des fichiers de bibliothèque qui composent la bibliothèque Runtime C C++ et la bibliothèque standard, consultez fonctionnalités de la [bibliothèque CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"></a> Nouvel opérateur

Lorsqu’une instruction telle que la suivante est rencontrée dans un programme, elle se traduit par un appel à la fonction **operator new**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Si la demande concerne un espace de stockage de zéro octet, **operator new** retourne un pointeur vers un objet distinct (autrement dit, les appels répétés à **operator new** retournent des pointeurs différents). Si la mémoire est insuffisante pour la demande d’allocation, **operator new** lève une exception `std::bad_alloc` ou retourne **nullptr** si vous avez lié dans une nouvelle prise en charge de l' **opérateur** de non levée.

Vous pouvez écrire une routine qui tente de libérer de la mémoire et retenter l’allocation. Pour plus d’informations, consultez [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) . Pour plus d’informations sur le mode de récupération, consultez la section gestion de la mémoire insuffisante de cette rubrique.

Les deux étendues pour les **nouvelles fonctions opérateur** sont décrites dans le tableau suivant.

### <a name="scope-for-operator-new-functions"></a>Étendue pour les nouvelles fonctions opérateur

|Opérateur|Portée|
|--------------|-----------|
|**:: operator new**|Global|
|*Class-Name* **:: operator new**|Classe|

Le premier argument de **operator new** doit être de type `size_t` (un type défini dans \<STDDEF. h >) et le type de retour est toujours **void** <strong>\*</strong>.

La fonction globale **operator new** est appelée lorsque l’opérateur **New** est utilisé pour allouer des objets de types intégrés, des objets de type classe qui ne contiennent pas de fonctions **operator new** définies par l’utilisateur, et des tableaux de tout type. Lorsque l’opérateur **New** est utilisé pour allouer des objets d’un type de classe où un **opérateur New** est défini, l' **opérateur New** de cette classe est appelé.

Une fonction **operator new** définie pour une classe est une fonction membre statique (qui ne peut pas, par conséquent, être virtuelle) qui masque la fonction **operator new** globale pour les objets de ce type de classe. Considérez le cas où **New** est utilisé pour allouer et définir la mémoire à une valeur donnée :

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

L’argument fourni entre parenthèses à **New** est passé à `Blanks::operator new` comme argument `chInit`. Toutefois, la fonction globale **operator new** est masquée, ce qui provoque la génération d’une erreur dans le code suivant :

```cpp
Blanks *SomeBlanks = new Blanks;
```

Le compilateur prend en charge les opérateurs **New** et **Delete** du tableau membre dans une déclaration de classe. Exemple :

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

Il existe une autre façon de gérer les demandes d’allocation de mémoire qui ont échoué. Écrivez une routine de récupération personnalisée pour gérer un tel échec, puis enregistrez votre fonction en appelant la fonction runtime [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) .

##  <a id="delete_operator"></a> Opérateur delete

La mémoire allouée dynamiquement à l’aide de l’opérateur **New** peut être libérée à l’aide de l’opérateur **Delete** . L’opérateur delete appelle la fonction **operator delete** , qui libère de la mémoire dans le pool disponible. L’utilisation de l’opérateur **Delete** entraîne également l’appel du destructeur de classe (le cas échéant).

Il existe **des fonctions** globales et de portée de classe. Une seule fonction d' **opérateur delete** peut être définie pour une classe donnée ; Si elle est définie, elle masque la fonction globale **operator delete** . La fonction globale **operator delete** est toujours appelée pour les tableaux de tout type.

Fonction globale **operator delete** . Deux formes existent pour les fonctions opérateur global **Delete** et **opérateur** de membre de classe :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Seul l’un des deux formulaires ci-dessus peut être présent pour une classe donnée. Le premier formulaire accepte un argument unique de type `void *`, qui contient un pointeur vers l’objet à libérer. La deuxième forme (désallocation dimensionnée) accepte deux arguments, le premier étant un pointeur vers le bloc de mémoire à libérer et le second étant le nombre d’octets à libérer. Le type de retour des deux formes est **void** (l'**opérateur delete** ne peut pas retourner de valeur).

L’objectif de la deuxième forme est d’accélérer la recherche de la catégorie de taille correcte de l’objet à supprimer, ce qui n’est souvent pas stocké près de l’allocation elle-même et probablement non mis en cache. La deuxième forme est utile lorsqu’une fonction **operator delete** d’une classe de base est utilisée pour supprimer un objet d’une classe dérivée.

La fonction d' **opérateur delete** est statique ; par conséquent, il ne peut pas être virtuel. La fonction **operator delete** obéit au contrôle d’accès, comme décrit dans [member-Access Control](member-access-control-cpp.md).

L’exemple suivant montre les fonctions **operator new** et opérateur **Delete** définies par l’utilisateur, conçues pour consigner les allocations et les désallocations de mémoire :

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

Le code précédent peut être utilisé pour détecter les fuites de mémoire, c'est-à-dire la mémoire qui est allouée sur le magasin libre mais jamais récupérée. Pour effectuer cette détection, les opérateurs **New** et **Delete** globaux sont redéfinis pour compter l’allocation et la désallocation de mémoire.

Le compilateur prend en charge les opérateurs **New** et **Delete** du tableau membre dans une déclaration de classe. Exemple :

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
