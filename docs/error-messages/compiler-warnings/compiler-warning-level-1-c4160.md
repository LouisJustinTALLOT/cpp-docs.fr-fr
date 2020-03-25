---
title: Avertissement du compilateur (niveau 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 8eb53d3f00c717df0e657ede3de6dd71d4a0bb47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176167"
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
