---
title: Erreur de ligne de commande D8045 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cf1248c072374cbe65d74136dfd1a8680e483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297087"
---
# <a name="command-line-error-d8045"></a>Erreur de ligne de commande D8045
Impossible de compiler le fichier C 'fichier' avec l’option /clr  
  
 Uniquement les fichiers de code source C++ peuvent être passés à une compilation qui utilise **/CLR**.  Utilisez **/TP** pour compiler un fichier .c en tant que fichier .cpp ; consultez [/Tc, / TP, /TP (spécifier le Type des fichiers Source)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) pour plus d’informations.  
  
 Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 L’erreur D8045 peut également se produire si vous compilez une application ATL à l’aide de Visual C++. Consultez [Comment : migrer vers/CLR](../../dotnet/how-to-migrate-to-clr.md) pour plus d’informations.