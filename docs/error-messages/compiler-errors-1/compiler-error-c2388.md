---
description: 'En savoir plus sur : erreur du compilateur C2388'
title: Erreur du compilateur C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 63a2758b4e214b38c7d999bdc2a33d328709ea67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123979"
---
# <a name="compiler-error-c2388"></a>Erreur du compilateur C2388

'Symbol' : un symbole ne peut pas être déclaré avec __declspec (AppDomain) et \_ _declspec (processus)

Les `appdomain` `process` **`__declspec`** modificateurs et ne peuvent pas être utilisés sur le même symbole. Le stockage d’une variable existe par processus ou par domaine d’application.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

L’exemple suivant génère l’erreur C2388 :

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
