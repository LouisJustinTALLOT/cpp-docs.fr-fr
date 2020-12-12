---
description: 'En savoir plus sur : erreur du compilateur C3803'
title: Erreur du compilateur C3803
ms.date: 11/04/2016
f1_keywords:
- C3803
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
ms.openlocfilehash: 23b3c9f38470bca471910bb31f7a0acbdf14693e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291556"
---
# <a name="compiler-error-c3803"></a>Erreur du compilateur C3803

'Property' : la propriété a un type qui est incompatible avec l’un de ses accesseurs’accessor'

Le type d’une propriété définie avec la [propriété](../../cpp/property-cpp.md) ne correspond pas au type de retour de l’une de ses fonctions d’accesseur.

L’exemple suivant génère l’C3803 :

```cpp
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```
