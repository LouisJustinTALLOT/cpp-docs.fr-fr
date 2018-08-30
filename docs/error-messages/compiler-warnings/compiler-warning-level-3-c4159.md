---
title: Compilateur avertissement (niveau 3) C4159 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4159
dev_langs:
- C++
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43e3d63ad1d482222c4ffa7aa7435d0e660f3985
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223316"
---
# <a name="compiler-warning-level-3-c4159"></a>Compilateur avertissement (niveau 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma(pop,...) : a exécuté un POP l’identificateur '*identificateur*'

## <a name="remarks"></a>Notes

Votre code source contient un **push** instruction avec un identificateur pour un pragma suivi d’un **pop** instruction sans identificateur. Par conséquent, *identificateur* est la fenêtre et les utilisations de *identificateur* peuvent provoquer un comportement inattendu.

## <a name="example"></a>Exemple

Pour éviter cet avertissement, donnez un identificateur dans le **pop** instruction. Exemple :

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```