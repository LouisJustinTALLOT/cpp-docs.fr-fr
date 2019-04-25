---
title: Priorité dans les règles d'inférence
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319679"
---
# <a name="precedence-in-inference-rules"></a>Priorité dans les règles d'inférence

Si une règle d’inférence est définie plusieurs fois, NMAKE utilise la définition de la priorité la plus élevée. La liste suivante montre l’ordre de priorité, du plus élevé au plus bas :

1. Règle d’inférence définie dans un makefile ; définitions les plus récentes ont une priorité.

1. Règle d’inférence définie dans Tools.ini ; définitions les plus récentes ont une priorité.

1. Une règle d’inférence prédéfinies.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
