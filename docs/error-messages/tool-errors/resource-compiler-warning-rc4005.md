---
title: Avertissement RC4005 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724764e443d4ab999c1df1247e9f5572ebdb2078
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322482"
---
# <a name="resource-compiler-warning-rc4005"></a>Avertissement RC4005 du compilateur de ressources 
'identificateur' : redéfinition de macro  
  
 L’identificateur est défini à deux reprises. Le compilateur a utilisé la deuxième définition de macro.  
  
 Cet avertissement peut être provoqué par une macro est définie sur la ligne de commande et dans le code avec un `#define` la directive. Elle peut également être due par des macros importées à partir des fichiers include.  
  
 Pour éliminer l’avertissement, supprimez une des définitions ou utilisez un `#undef` directive avant la seconde définition.