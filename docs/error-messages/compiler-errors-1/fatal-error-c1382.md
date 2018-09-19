---
title: Erreur irrécupérable C1382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5a6ce312c5ef886ef25e8de46e6d3376eded2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030643"
---
# <a name="fatal-error-c1382"></a>Erreur irrécupérable C1382

le fichier PCH 'fichier' recompilé depuis la « obj » a été généré. Régénérez cet objet

Lorsque vous utilisez [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un fichier .pch qui est plus récent qu’un fichier CIL .obj qui pointe vers elle. Les informations contenues dans le fichier CIL .obj sont obsolètes. Reconstruire l’objet.

C1382 peut également se produire si vous compilez avec **/Yc**, mais également passer source plusieurs fichiers de code pour le compilateur.  Pour corriger, n’utilisez pas **/Yc** lors du passage des fichiers de code source plusieurs au compilateur.  Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).