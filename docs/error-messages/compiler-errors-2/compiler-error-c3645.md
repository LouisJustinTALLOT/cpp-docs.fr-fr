---
description: 'En savoir plus sur : erreur du compilateur C3645'
title: Erreur du compilateur C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: 198b22b80a4975d8bd6fab130c075621f248a93c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203768"
---
# <a name="compiler-error-c3645"></a>Erreur du compilateur C3645

'fonction' : __clrcall ne peut pas être utilisé sur des fonctions compilées en code natif

La présence de certains mots clés dans une fonction entraîne la compilation de la fonction en mode natif.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3645.

```cpp
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```
