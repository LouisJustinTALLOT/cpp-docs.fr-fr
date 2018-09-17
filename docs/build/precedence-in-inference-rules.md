---
title: Priorité dans les règles d’inférence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725229"
---
# <a name="precedence-in-inference-rules"></a>Priorité dans les règles d'inférence

Si une règle d’inférence est définie plusieurs fois, NMAKE utilise la définition de la priorité la plus élevée. La liste suivante montre l’ordre de priorité, du plus élevé au plus bas :

1. Règle d’inférence définie dans un makefile ; définitions les plus récentes ont une priorité.

1. Règle d’inférence définie dans Tools.ini ; définitions les plus récentes ont une priorité.

1. Une règle d’inférence prédéfinies.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](../build/inference-rules.md)