---
title: Erreur irrécupérable C1305 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90d73003d9f19eb41f9eb34cd47c7b90b1e6164f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540816"
---
# <a name="fatal-error-c1305"></a>Erreur irrécupérable C1305
la base de données de profil 'pgd_file ' du correspond à une architecture différente  
  
 Un fichier .pgd qui a été généré à partir de l’opération/LTCG : PGINSTRUMENT pour une autre plateforme a été passée au [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md) sont disponibles pour les plateformes x86 et x64. Toutefois, un fichier .pgd généré avec une opération de/LTCG : PGINSTRUMENT pour une plateforme n’est pas valide en tant qu’entrée à un/LTCG : PGOPTIMIZE pour une autre plateforme.  
  
 Pour résoudre cette erreur, seulement passez un fichier .pgd qui est créé avec/LTCG : PGINSTRUMENT pour/LTCG : PGOPTIMIZE sur la même plateforme.