---
title: Avertissement du compilateur (niveau 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174282"
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
