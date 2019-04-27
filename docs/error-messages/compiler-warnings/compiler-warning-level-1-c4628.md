---
title: Avertissement du compilateur (niveau 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: ebb71155774ce32d6b4fc2b9920fdd31dd466841
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221204"
---
# <a name="compiler-warning-level-1-c4628"></a>Avertissement du compilateur (niveau 1) C4628

digrammes non pris en charge avec -Ze. Séquence de caractères 'digramme' non interprétée comme jeton de remplacement pour 'car'

Digrammes ne sont pas pris en charge sous [/Ze](../../build/reference/za-ze-disable-language-extensions.md). Cet avertissement sera suivi d’une erreur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4628 :

```
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```