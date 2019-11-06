---
title: Avertissement du compilateur (niveau 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c8dc35a58d40d2619f6e035e07b4ad0b3351c45d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626642"
---
# <a name="compiler-warning-level-1-c4291"></a>Avertissement du compilateur (niveau 1) C4291

'declaration' : aucune suppression d’opérateur correspondante trouvée ; la mémoire ne sera pas libérée si l’initialisation lève une exception

Un [nouvel](../../cpp/new-operator-cpp.md) emplacement est utilisé pour lequel il n’y a pas de [suppression](../../cpp/delete-operator-cpp.md)de placement.

Lorsque la mémoire est allouée pour un objet avec l’opérateur **New**, le constructeur de l’objet est appelé. Si le constructeur lève une exception, toute mémoire qui a été allouée pour l’objet doit être désallouée. Cela ne peut pas être effectué à moins qu’une fonction d’opérateur **Delete** ne corresponde à l’opérateur **New**.

Si vous utilisez l’opérateur **New** sans argument supplémentaire et compilez avec les options [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)ou/EHa pour activer la gestion des exceptions, le compilateur génère du code pour appeler l’opérateur **Delete** si le constructeur lève une exception.

Si vous utilisez la forme positionnement de l’opérateur **New** (le formulaire avec les arguments en plus de la taille de l’allocation) et que le constructeur de l’objet lève une exception, le compilateur génère toujours du code pour appeler l’opérateur **Delete**. Toutefois, il ne le fera que si une forme de placement de l’opérateur **Delete** existe et correspond à la forme de placement de l’opérateur **New** qui a alloué la mémoire. Exemple :

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

L’exemple ci-dessus génère l’avertissement C4291, car aucune forme de placement de l’opérateur **Delete** n’a été définie et correspond à la forme de placement de Operator **New**. Pour résoudre le problème, insérez le code suivant au-dessus de **main**. Notez que tous les paramètres de fonction **Delete** de l’opérateur surchargé correspondent à ceux de l’opérateur surchargé **New**, à l’exception du premier paramètre.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```