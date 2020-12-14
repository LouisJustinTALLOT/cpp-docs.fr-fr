---
description: 'En savoir plus sur : erreur irrécupérable C1382'
title: Erreur irrécupérable C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: fd2b9f48030d558a880a787114848dd0551b68ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276515"
---
# <a name="fatal-error-c1382"></a>Erreur irrécupérable C1382

fichier PCH 'file' recompilé depuis la génération de 'obj'. Régénérez cet objet

Lors de l’utilisation de [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un fichier. pch qui est plus récent qu’un fichier CIL. obj qui pointe vers celui-ci. Les informations du fichier CIL. obj sont obsolètes. Régénérez l’objet.

C1382 peut également se produire si vous compilez avec **/Yc**, mais transmettez également plusieurs fichiers de code source au compilateur.  Pour résoudre ce cas, n’utilisez pas **/Yc** lors du passage de plusieurs fichiers de code source au compilateur.  Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).
