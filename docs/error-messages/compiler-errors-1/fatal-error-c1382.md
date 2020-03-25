---
title: Erreur irrécupérable C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203097"
---
# <a name="fatal-error-c1382"></a>Erreur irrécupérable C1382

le fichier PCH’file’a été reconstruit depuis la génération de’obj'. Régénérez cet objet

Lors de l’utilisation de [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un fichier. pch qui est plus récent qu’un fichier CIL. obj qui pointe vers celui-ci. Les informations du fichier CIL. obj sont obsolètes. Régénérez l’objet.

C1382 peut également se produire si vous compilez avec **/Yc**, mais transmettez également plusieurs fichiers de code source au compilateur.  Pour résoudre ce cas, n’utilisez pas **/Yc** lors du passage de plusieurs fichiers de code source au compilateur.  Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).
