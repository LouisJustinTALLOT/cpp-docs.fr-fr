---
title: Erreur BSCMAKE BK1517 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 941773fbcf65a3b1c1a6041a1e7a067cfc286823
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097053"
---
# <a name="bscmake-error-bk1517"></a>Erreur BSCMAKE BK1517

fichier de source de fichiersbr compilé avec /Yc et /Yu

Le fichier .sbr fait référence à lui-même. Il a probablement été recompilé avec /Yu après la compilation avec/Yc. Réinitialiser l’option de compilateur pour le fichier source à /Yc, puis sélectionnez **reconstruire** à générer de nouveaux fichiers .sbr. Ne recompilez pas le fichier source avec /Yu.