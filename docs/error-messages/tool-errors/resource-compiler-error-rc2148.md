---
title: Erreur RC2148 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2148
dev_langs:
- C++
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10e18eef4691c0a018feb583ffb93499e86ccb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320204"
---
# <a name="resource-compiler-error-rc2148"></a>Erreur RC2148 du compilateur de ressources 
ID de sous-langue trop grande  
  
 La valeur d’ID de sous-langue était hors limites.  
  
 L’instruction **LANGUAGE** doit utiliser la syntaxe suivante :  
  
 **LANGUAGE** *ID_langue_principale*,*ID_langue_secondaire*  
  
 ID de sous-langue valides sont définis en tant que **SUBLANG_** constantes dans le fichier WINNT.h.