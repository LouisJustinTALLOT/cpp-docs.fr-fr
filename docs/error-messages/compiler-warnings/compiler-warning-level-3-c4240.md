---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4240'
title: Avertissement du compilateur (niveau 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 95e704b6ad91ff77c4def0b4fa1fe8fad002e5ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344196"
---
# <a name="compiler-warning-level-3-c4240"></a>Avertissement du compilateur (niveau 3) C4240

extension non standard utilisée : accès à’ClassName’défini à présent comme’spécificateur d’accès', précédemment défini comme’spécificateur d’accès'

Sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), vous ne pouvez pas modifier l’accès à une classe imbriquée. Sous les extensions Microsoft par défaut (/Ze), vous pouvez, avec cet avertissement.

## <a name="example"></a>Exemple

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```
