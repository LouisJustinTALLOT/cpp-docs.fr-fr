---
title: Erreur irrécupérable NMAKE U1095 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13c819d18149e61bca71f6a4cb10ea851a2d485d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317243"
---
# <a name="nmake-fatal-error-u1095"></a>Erreur irrécupérable NMAKE U1095
ligne de commande développée 'ligne de commande' trop long  
  
 Après l’expansion macro, la ligne de commande donnée a dépassé la limite de longueur de lignes de commande pour le système d’exploitation.  
  
 MS-DOS autorise jusqu'à 128 caractères sur une ligne de commande.  
  
 Si la commande est d’un programme qui peut accepter l’entrée de ligne de commande à partir d’un fichier, modifiez la commande et fournissez l’entrée à partir d’un fichier sur disque ou d’un fichier inline. Par exemple, LINK et LIB acceptent l’entrée d’un fichier réponse.