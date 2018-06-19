---
title: Erreur irrécupérable CVTRES CVT1100 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32085c4c37c82567eb78f46b52bcc4a6c41daae5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302657"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Erreur irrécupérable CVTRES CVT1100
une ressource dupliquée — type : type, nom : nom, langue :, indicateurs : indicateurs, taille :  
  
 La ressource donnée a été spécifiée plusieurs fois.  
  
 Vous pouvez obtenir cette erreur si vous n’avez pas spécifié et que l’éditeur de liens crée une bibliothèque de types [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) et une ressource de votre projet utilise déjà 1. Dans ce cas, spécifiez /TLBID et spécifiez un autre numéro à 65535.