---
title: Avertissement du compilateur (niveau 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754858"
---
# <a name="compiler-warning-level-1-c4291"></a>Avertissement du compilateur (niveau 1) C4291

'déclaration' : aucun opérateur correspondant supprimé trouvé; mémoire ne sera pas libérée si l’initialisation jette une exception

Un [nouveau](../../cpp/new-operator-cpp.md) placement est utilisé pour lequel il n’y a pas [de](../../cpp/delete-operator-cpp.md)suppression de placement .

Lorsque la mémoire est allouée pour un objet avec opérateur **nouveau,** le constructeur de l’objet est appelé. Si le constructeur lance une exception, toute mémoire qui a été allouée à l’objet doit être deallocated. Cela ne peut avoir lieu que si un opérateur **supprime** la fonction qui correspond à l’opérateur **nouveau**.

Si vous utilisez l’opérateur **nouveau** sans aucun argument supplémentaire et compilez avec [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md), ou /EHa options pour activer la manipulation d’exception, le compilateur générera du code pour appeler l’opérateur **supprimer** si le constructeur jette une exception.

Si vous utilisez le formulaire de placement du **nouvel** opérateur (le formulaire avec des arguments en plus de la taille de l’allocation) et que le constructeur de l’objet fait une exception, le compilateur continuera de générer du code pour appeler l’opérateur **supprimer**; mais il ne le fera que **delete** si une forme de suppression d’opérateur existe correspondant à la forme de placement de l’opérateur **nouveau** qui a alloué la mémoire. Par exemple :

```cpp
// C4291.cpp
// compile with: /EHsc /W1
#include <malloc.h>

class CList
{
public:
   CList(int)
   {
      throw "Fail!";
   }
};

void* operator new(size_t size, char* pszFilename, int nLine)
{
   return malloc(size);
}

int main(void)
{
   try
   {
      // This will call ::operator new(unsigned int) to allocate heap
      // memory. Heap memory pointed to by pList1 will automatically be
      // deallocated by a call to ::operator delete(void*) when
      // CList::CList(int) throws an exception.
      CList* pList1 = new CList(10);
   }
   catch (...)
   {
   }

   try
   {
      // This will call the overloaded ::operator new(size_t, char*, int)
      // to allocate heap memory. When CList::CList(int) throws an
      // exception, ::operator delete(void*, char*, int) should be called
      // to deallocate the memory pointed to by pList2. Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291
   }
   catch (...)
   {
   }
}
```

L’exemple ci-dessus génère l’avertissement C4291 parce qu’aucune forme de placement de **suppression** de l’opérateur n’a été définie qui correspond à la forme de placement de l’opérateur **nouveau**. Pour résoudre le problème, insérer le code suivant au-dessus **de la principale**. Notez que tous les paramètres de fonction de **suppression** de l’opérateur surchargé correspondent à ceux de l’opérateur surchargé **nouveau,** à l’exception du premier paramètre.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
