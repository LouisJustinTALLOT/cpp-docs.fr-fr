---
description: 'En savoir plus sur : erreur du compilateur C2844'
title: Erreur du compilateur C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 030d8526e7bfd85e7bcca1c115f1b5ce5d45c3aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260277"
---
# <a name="compiler-error-c2844"></a>Erreur du compilateur C2844

'membre' : ne peut pas être membre de l’interface’interface'

Une [classe d’interface](../../extensions/interface-class-cpp-component-extensions.md) ne peut pas contenir de données membres à moins qu’il ne s’agit également d’une propriété.

Tout élément autre qu’une fonction de propriété ou de membre n’est pas autorisé dans une interface. En outre, les constructeurs, les destructeurs et les opérateurs ne sont pas autorisés.

L’exemple suivant génère l’C2844 :

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
