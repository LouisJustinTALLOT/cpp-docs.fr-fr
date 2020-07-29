---
title: Avertissement du compilateur (niveau 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: e45856702eef7f24595d10b81f39047d8f9a08b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221001"
---
# <a name="compiler-warning-level-1-c4291"></a>Avertissement du compilateur (niveau 1) C4291

'declaration' : aucune suppression d’opérateur correspondante trouvée ; la mémoire ne sera pas libérée si l’initialisation lève une exception

Un [nouvel](../../cpp/new-operator-cpp.md) emplacement est utilisé pour lequel il n’y a pas de [suppression](../../cpp/delete-operator-cpp.md)de placement.

Lorsque la mémoire est allouée pour un objet avec **`new`** l’opérateur, le constructeur de l’objet est appelé. Si le constructeur lève une exception, toute mémoire qui a été allouée pour l’objet doit être désallouée. Cela ne peut pas être effectué à moins qu’une fonction d’opérateur **`delete`** qui corresponde à l’opérateur n’existe **`new`** .

Si vous utilisez l’opérateur **`new`** sans arguments supplémentaires et que vous compilez avec les options [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)ou/EHa pour activer la gestion des exceptions, le compilateur génère du code pour appeler **`delete`** l’opérateur si le constructeur lève une exception.

Si vous utilisez la forme de placement de l' **`new`** opérateur (le formulaire avec les arguments en plus de la taille de l’allocation) et que le constructeur de l’objet lève une exception, le compilateur générera toujours du code pour appeler l’opérateur ; Toutefois, il ne le fera **`delete`** que si une forme de placement d’opérateur **`delete`** correspond à la forme de positionnement de l’opérateur **`new`** qui a alloué la mémoire. Par exemple :

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

L’exemple ci-dessus génère l’avertissement C4291, car aucune forme de placement de **`delete`** l’opérateur n’a été définie et correspond à la forme de placement de l’opérateur **`new`** . Pour résoudre le problème, insérez le code suivant au-dessus de **main**. Notez que tous les paramètres de fonction d’opérateur surchargés **`delete`** correspondent à ceux de l’opérateur surchargé **`new`** , à l’exception du premier paramètre.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
