---
title: Opérateurs new et delete
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367884"
---
# <a name="new-and-delete-operators"></a>Opérateurs new et delete

CMD prend en charge l’attribution dynamique et la transaction d’objets à l’aide des [nouveaux](new-operator-cpp.md) opérateurs et [suppriment.](delete-operator-cpp.md) Ces opérateurs allouent de la mémoire pour les objets à partir d'un pool appelé magasin gratuit. Le **nouvel** opérateur appelle l’opérateur de fonction spéciale [nouveau](new-operator-cpp.md), et l’opérateur **de suppression** appelle l’opérateur de fonction spéciale [supprimer](delete-operator-cpp.md).

La **nouvelle** fonction de la Bibliothèque standard de CMD prend en charge le comportement spécifié dans la norme C, qui consiste à jeter une std : : bad_alloc exception si l’allocation de mémoire échoue. Si vous voulez toujours la version non-lancement de **nouveau**, liez votre programme avec nothrownew.obj. Toutefois, lorsque vous établissez un lien avec nothrownew.obj, **l’opérateur** par défaut nouveau dans la bibliothèque standard de CMD ne fonctionne plus.

Pour obtenir une liste des dossiers de bibliothèque qui comprennent la bibliothèque C Runtime et la Bibliothèque standard CD, consultez [les caractéristiques de la bibliothèque CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> Le nouvel opérateur

Lorsqu’une déclaration telle que la suivante est rencontrée dans un programme, elle se traduit par un appel à **l’opérateur**de fonction nouveau :

```cpp
char *pch = new char[BUFFER_SIZE];
```

Si la demande est pour zéro octets de stockage, **l’opérateur retourne un** pointeur à un objet distinct (c’est-à-dire, appels répétés à **l’opérateur de nouveaux** retour différents pointeurs). S’il n’y a pas suffisamment de `std::bad_alloc` mémoire pour la demande d’allocation, **l’opérateur lance une** nouvelle exception, ou retourne **nullptr** si vous avez lié dans non-lancer **opérateur nouveau** support.

Vous pouvez écrire une routine qui tente de libérer la mémoire et de réessayer l’allocation; voir [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) pour plus d’informations. Pour plus de détails sur le schéma de récupération, voir la section De mémoire de manipulation insuffisante de ce sujet.

Les deux portées pour les nouvelles fonctions **de l’opérateur** sont décrites dans le tableau suivant.

### <a name="scope-for-operator-new-functions"></a>Possibilité pour les nouvelles fonctions de l’opérateur

|Opérateur|Étendue|
|--------------|-----------|
|**::opérateur nouveau**|Global|
|*nom de classe* **::opérateur nouveau**|Classe|

Le premier argument pour **l’opérateur nouveau** doit être de `size_t` type (un type défini en \<stddef.h>), et le type de retour est toujours **nul** <strong>\*</strong>.

La nouvelle fonction **de l’opérateur** mondial s’appelle lorsque le **nouvel** opérateur est utilisé pour allouer des objets de types intégrés, des objets de type classe qui ne contiennent pas de nouvelles fonctions **d’opérateur** définies par l’utilisateur et des tableaux de tout type. Lorsque le **nouvel** opérateur est utilisé pour répartir des objets d’un type de classe où un **opérateur nouveau** est défini, **l’opérateur** nouveau de cette classe est appelé.

Une nouvelle fonction **d’opérateur** définie pour une classe est une fonction membre statique (qui ne peut donc pas être virtuelle) qui cache à l’opérateur mondial **une nouvelle** fonction pour les objets de ce type de classe. Considérez le cas où **le nouveau** est utilisé pour allouer et définir la mémoire à une valeur donnée :

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

L’argument fourni entre parenthèses `Blanks::operator new` à `chInit` **nouveau** est transmis à l’argument. Toutefois, la nouvelle fonction **de l’opérateur** mondial est cachée, ce qui provoque un code tel que ce qui suit pour générer une erreur:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Le compilateur prend en charge le tableau des **membres de nouveaux** opérateurs et **supprime** les opérateurs dans une déclaration de classe. Par exemple :

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

Les tests d’allocation de mémoire échoué peuvent être effectués comme indiqué ici :

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

Il existe une autre façon de traiter les demandes d’allocation de mémoire échouées. Écrivez une routine de récupération personnalisée pour gérer un tel échec, puis enregistrez votre fonction en appelant la fonction [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) temps d’exécution.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> L’opérateur de suppression

La mémoire qui est attribuée dynamiquement à l’aide du **nouvel** opérateur peut être libérée à l’aide de l’opérateur **de suppression.** L’opérateur de suppression appelle la fonction **de suppression de l’opérateur,** ce qui libère la mémoire vers le pool disponible. L’utilisation de l’opérateur **de suppression** provoque également le destructeur de classe (s’il y en a un) à être appelé.

Il existe des fonctions globales et de **suppression d’opérateurs** à portée de classe. Une seule fonction **de suppression d’opérateur** peut être définie pour une classe donnée; s’il est défini, il cache la fonction de suppression de **l’opérateur** mondial. La fonction de **suppression de l’opérateur** mondial est toujours appelée pour des tableaux de tout type.

L’opérateur mondial **supprime la** fonction. Il existe deux formulaires pour que **l’opérateur** mondial supprime et que **l’opérateur** membre de la classe supprime les fonctions :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Un seul des deux formulaires précédents peut être présent pour une classe donnée. La première forme prend un `void *`seul argument de type , qui contient un pointeur à l’objet de deallocate. La deuxième forme — la répartition de taille — prend deux arguments, dont le premier est un pointeur vers le bloc de mémoire à traiter et le second est le nombre d’octets à traiter. Le type de retour des deux formulaires est **nul** **(la suppression de l’opérateur** ne peut pas retourner une valeur).

L’intention du deuxième formulaire est d’accélérer la recherche de la catégorie de taille correcte de l’objet à supprimer, qui n’est souvent pas stocké près de l’allocation elle-même et probablement non plafonné. Le deuxième formulaire est utile lorsqu’un **opérateur supprime** la fonction d’une classe de base est utilisé pour supprimer un objet d’une classe dérivée.

La fonction **de suppression de l’opérateur** est statique; par conséquent, il ne peut pas être virtuel. La fonction **de suppression de l’opérateur** obéit au contrôle d’accès, tel que décrit dans [Le contrôle d’accès aux membres](member-access-control-cpp.md).

L’exemple suivant montre **l’opérateur défini** par l’utilisateur, nouveau et **l’opérateur supprime les** fonctions conçues pour enregistrer les allocations et les deallocations de mémoire :

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

Le code précédent peut être utilisé pour détecter les fuites de mémoire, c'est-à-dire la mémoire qui est allouée sur le magasin libre mais jamais récupérée. Pour effectuer cette détection, les opérateurs mondiaux **nouveaux** et **supprimer** sont redéfinis pour compter l’allocation et la répartition de la mémoire.

Le compilateur prend en charge le tableau des **membres de nouveaux** opérateurs et **supprime** les opérateurs dans une déclaration de classe. Par exemple :

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
