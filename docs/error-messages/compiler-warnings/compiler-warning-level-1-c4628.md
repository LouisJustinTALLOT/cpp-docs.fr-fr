---
title: Avertissement du compilateur (niveau 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: 6063755db5ac517d868bc47d2c417356ccef5d58
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051443"
---
# <a name="compiler-warning-level-1-c4628"></a>Avertissement du compilateur (niveau 1) C4628

digrammes non pris en charge avec -Ze. Séquence de caractères 'digramme' non interprétée comme jeton de remplacement pour 'car'

Les digrammes ne sont pas pris en charge sous [/Ze](../../build/reference/za-ze-disable-language-extensions.md). Cet avertissement est suivi d’une erreur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4628 :

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```