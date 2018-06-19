---
title: Erreur irrécupérable C1305 | Documents Microsoft
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
ms.openlocfilehash: 3cb1cf19d0fc4152fbb458d684972bb5a4418f37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227145"
---
# <a name="fatal-error-c1305"></a>Erreur irrécupérable C1305
la base de données de profil 'pgd_file ' du correspond à une architecture différente  
  
 Un fichier .pgd généré à partir de l’opération/LTCG : PGINSTRUMENT pour une autre plateforme a été passée à [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md) sont disponibles pour x86 et [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] plateformes. Toutefois, un fichier .pgd généré avec une opération de/LTCG : PGINSTRUMENT pour une plateforme n’est pas valid en tant qu’entrée à un/LTCG : PGOPTIMIZE pour une plateforme différente.  
  
 Pour résoudre cette erreur, seulement passez un fichier .pgd créé avec/LTCG : PGINSTRUMENT à/LTCG : PGOPTIMIZE sur la même plateforme.