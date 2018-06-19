---
title: LNK1241 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b02b1d9d06706c70478d958dd3c2af8dbc9c2c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299173"
---
# <a name="linker-tools-error-lnk1241"></a>Erreur des outils Éditeur de liens LNK1241
fichier de ressources 'fichier de ressources' déjà spécifié  
  
 Cette erreur est générée si vous exécutez **cvtres** manuellement à partir de la ligne de commande et si vous passez le fichier .obj résultant du fichier à l’éditeur de liens en outre d’autres fichiers .res.  
  
 Pour spécifier plusieurs fichiers .res, les passer à l’éditeur de liens en tant que fichiers .res, et non depuis des fichiers .obj créés par **cvtres**.