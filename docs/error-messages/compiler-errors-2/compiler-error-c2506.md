---
title: Erreur du compilateur C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746836"
---
# <a name="compiler-error-c2506"></a>Erreur du compilateur C2506

'membre' : ' __declspec (modificateur) 'ne peut pas être appliqué à ce symbole

Vous ne pouvez pas déclarer par processus ou par AppDomain pour les membres statiques d’une classe managée.

Pour plus d'informations, voir [appdomain](../../cpp/appdomain.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2506.

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
