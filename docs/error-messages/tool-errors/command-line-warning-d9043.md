---
title: Avertissement de ligne de commande D9043 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9043
dev_langs:
- C++
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d29371e147c693b2aa49f8dcf838841af3c75c8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031864"
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