---
title: PG0165 d’erreur de l’optimisation guidée par profil | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318413"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Erreur de l'optimisation guidée par profil PG0165
Lecture de 'Nomfichier.PGD' : ' version de PGD n’est pas pris en charge (incompatibilité de version)'.  
  
 Les fichiers PGD sont spécifiques à un ensemble d’outils du compilateur. Cette erreur est générée lorsque vous utilisez un compilateur autre que celui utilisé pour *nom de fichier*.pgd. Cette erreur indique que cet ensemble d’outils du compilateur ne peut pas utiliser les données à partir de *nom de fichier*.pgd pour optimiser le programme actuel.  
  
 Pour résoudre ce problème, régénérez *nom de fichier*.pgd à l’aide de l’ensemble d’outils du compilateur actuel.