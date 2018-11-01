---
title: Erreur BSCMAKE BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476087"
---
# <a name="bscmake-error-bk1517"></a>Erreur BSCMAKE BK1517

fichier de source de fichiersbr compilé avec /Yc et /Yu

Le fichier .sbr fait référence à lui-même. Il a probablement été recompilé avec /Yu après la compilation avec/Yc. Réinitialiser l’option de compilateur pour le fichier source à /Yc, puis sélectionnez **reconstruire** à générer de nouveaux fichiers .sbr. Ne recompilez pas le fichier source avec /Yu.