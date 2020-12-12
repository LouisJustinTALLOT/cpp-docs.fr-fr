---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4099'
title: Avertissement du compilateur (niveau 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: c35ce10560ca81f9457f6a21c4c55d96996e7645
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326515"
---
# <a name="compiler-warning-level-2-c4099"></a>Avertissement du compilateur (niveau 2) C4099

'identificateur' : nom de type rencontré en premier avec’objecttype1 'maintenant à l’aide de’objecttype2 '

Un objet déclaré en tant que structure est défini en tant que classe, ou un objet déclaré en tant que classe est défini en tant que structure. Le compilateur utilise le type donné dans la définition.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4099.

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```
