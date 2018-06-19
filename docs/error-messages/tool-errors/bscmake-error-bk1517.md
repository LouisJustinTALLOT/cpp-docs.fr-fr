---
title: Erreur BSCMAKE BK1517 | Documents Microsoft
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
ms.openlocfilehash: c6f5619a7c2a6ccf671845b27bbedf93d8eb2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298549"
---
# <a name="bscmake-error-bk1517"></a>Erreur BSCMAKE BK1517
fichier source de fichiersbr compilé avec /Yc et /Yu  
  
 Le fichier .sbr fait référence à elle-même. Il a probablement été recompilé avec /Yu après la compilation avec/Yc. Réinitialiser l’option de compilateur pour le fichier source à /Yc, puis sélectionnez **reconstruire** pour générer de nouveaux fichiers .sbr. Ne recompilez pas le fichier source avec /Yu.