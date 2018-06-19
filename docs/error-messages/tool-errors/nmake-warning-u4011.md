---
title: Avertissement NMAKE U4011 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9c0f90c507eebe212a9c3cbfb2f2d21cded43d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320793"
---
# <a name="nmake-warning-u4011"></a>Avertissement NMAKE U4011
'target' : les dépendants pas tous disponibles ; cible non générée  
  
 Un dépendant de la cible spécifiée n’existe pas ou était obsolète, et une commande de mise à jour du dépendant a retourné un code de sortie différent de zéro. L’option /K a indiqué à NMAKE de poursuivre le traitement des parties non liées de la génération et d’émettre un code de sortie 1 quand la session NMAKE est terminée.  
  
 Cet avertissement est précédé par l’avertissement [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) pour chaque dépendant qui n’a pas pu être créé ou mis à jour.