---
title: Compilateur avertissement (niveau 1) C4291 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8c5f2fe57d26de4b4b2f88a85f20b99344ac201
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038046"
---
# <a name="compiler-warning-level-1-c4291"></a>Avertissement du compilateur (niveau 1) C4291

'déclaration' : opérateur delete correspondant est trouvé ; mémoire ne sera pas libérée si l’initialisation lève une exception

Un positionnement [nouveau](../../cpp/new-operator-cpp.md) est utilisé pour lequel il n’existe aucune sélection élective [supprimer](../../cpp/delete-operator-cpp.md).

Lorsque la mémoire est allouée pour un objet avec l’opérateur **nouveau**, constructeur de l’objet est appelé. Si le constructeur lève une exception, de mémoire qui a été alloué pour l’objet doit être libérée. Cela ne peut pas avoir lieu, sauf si un opérateur **supprimer** il existe une fonction correspond à l’opérateur **nouveau**.

Si vous utilisez l’opérateur **nouveau** sans argument supplémentaire et compilez avec [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md), ou /EHa pour activer la gestion des exceptions, le compilateur générera du code pour opérateur d’appel **supprimer** si le constructeur lève une exception.

Si vous utilisez la forme positionnement de la **nouveau** opérateur (forme avec arguments en plus de la taille d’allocation) et le constructeur de l’objet lève une exception, le compilateur génère toujours du code pour appeler l’opérateur **supprimer**; mais il le fait que si une forme de l’opérateur **supprimer** existe correspondant à la forme positionnement de l’opérateur **nouveau** que la mémoire allouée. Exemple :

```
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

L’exemple ci-dessus génère l’avertissement C4291, car aucune forme positionnement de l’opérateur **supprimer** a été défini qui correspond à la forme positionnement de l’opérateur **nouveau**. Pour résoudre le problème, insérez le code suivant au-dessus **principal**. Notez que toutes l’opérateur surchargé **supprimer** paramètres de la fonction correspondent à ceux de l’opérateur surchargé **nouveau**, sauf pour le premier paramètre.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```