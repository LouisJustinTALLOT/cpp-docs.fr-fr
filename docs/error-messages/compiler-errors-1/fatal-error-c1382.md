---
title: Erreur irrécupérable C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228562"
---
# <a name="fatal-error-c1382"></a>Erreur irrécupérable C1382

le fichier PCH 'fichier' recompilé depuis la « obj » a été généré. Régénérez cet objet

Lorsque vous utilisez [/LTCG](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un fichier .pch qui est plus récent qu’un fichier CIL .obj qui pointe vers elle. Les informations contenues dans le fichier CIL .obj sont obsolètes. Reconstruire l’objet.

C1382 peut également se produire si vous compilez avec **/Yc**, mais également passer source plusieurs fichiers de code pour le compilateur.  Pour corriger, n’utilisez pas **/Yc** lors du passage des fichiers de code source plusieurs au compilateur.  Pour plus d’informations, consultez [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md).