---
description: 'En savoir plus sur : priorité dans les règles d’inférence'
title: Priorité dans les règles d'inférence
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: b56d01cce63aaaac92e011630e45bcf43e7fe0b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225906"
---
# <a name="precedence-in-inference-rules"></a>Priorité dans les règles d'inférence

Si une règle d’inférence est définie par multiplication, NMAKE utilise la définition de priorité la plus élevée. La liste suivante indique l’ordre de priorité du plus élevé au plus bas :

1. Une règle d’inférence définie dans un Makefile ; les définitions ultérieures ont la priorité.

1. Une règle d’inférence définie dans Tools.ini ; les définitions ultérieures ont la priorité.

1. Règle d’inférence prédéfinie.

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
