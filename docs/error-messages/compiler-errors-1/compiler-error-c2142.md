---
title: Erreur du compilateur C2142 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2142
dev_langs:
- C++
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32301087ac1f06f1958ca8de7d2f66645dafb3d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032490"
---
# <a name="compiler-error-c2142"></a>Erreur du compilateur C2142

déclarations de fonction différentes, paramètres spécifiés seulement dans un d’eux

Une déclaration de la fonction contient une liste de paramètres de variables. Une autre déclaration ne fait pas. C ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) uniquement.

L’exemple suivant génère l’erreur C2142 :

```
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```