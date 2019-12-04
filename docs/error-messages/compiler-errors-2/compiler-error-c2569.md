---
title: Erreur du compilateur C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 7299fe8daa1fa0fc6e1291bf8c683b33235e8bbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755523"
---
# <a name="compiler-error-c2569"></a>Erreur du compilateur C2569

'EnumOrUnion' : enum/Union ne peut pas être utilisé comme classe de base

Si vous devez dériver un type de l’Union ou de l’énumération spécifiée, remplacez l’Union ou l’énumération par une classe ou une structure.

L’exemple suivant génère l’C2569 :

```cpp
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```
