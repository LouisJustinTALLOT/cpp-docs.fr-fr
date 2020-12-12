---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4160'
title: Avertissement du compilateur (niveau 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: afb9a0a30376a0e0b1c59b89e98a131ab5889017
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267194"
---
# <a name="compiler-warning-level-1-c4160"></a>Avertissement du compilateur (niveau 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (,... pop) : impossible de trouver l’identificateur'*identifier*'ayant précédemment fait l’objet d’un push

## <a name="remarks"></a>Notes

Une instruction pragma dans votre code source tente de dépiler un identificateur qui n’a pas fait l’objet d’un push. Pour éviter cet avertissement, vérifiez que l’identificateur dépilé a bien fait l’objet d’un push.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4160 et montre comment la corriger :

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```
