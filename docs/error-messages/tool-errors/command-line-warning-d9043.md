---
title: Avertissement de ligne de commande D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 62834c5f245bc1c0f6197638e4608b7fe71e7eb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586028"
---
# <a name="command-line-warning-d9043"></a>Avertissement de ligne de commande D9043

valeur non valide 'niveau_avertissement ' non valide pour 'option_compilateur' ; en supposant que '4999' ; Avertissements d’analyse du code ne sont pas associés à des niveaux d’avertissement

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C9043 :.

```
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```