---
title: Erreur irrécupérable NMAKE U1100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ffd33a0a80056ee57f5f088823d7f8f6549c24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135754"
---
# <a name="nmake-fatal-error-u1100"></a>Erreur irrécupérable NMAKE U1100

la macro 'nom_macro' non conforme dans le contexte de la règle batch 'règle'

NMAKE génère cette erreur lorsque le bloc de commandes d’une règle en mode batch directement ou indirectement référence à une macro de fichier spécial qui n’est pas $<.

$< est le seul autorisé macro pour les règles en mode batch.