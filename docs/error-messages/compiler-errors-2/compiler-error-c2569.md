---
description: 'En savoir plus sur : erreur du compilateur C2569'
title: Erreur du compilateur C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: bf6b0670cfd90cadc939010a75f9faa9c7c25c30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209033"
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
