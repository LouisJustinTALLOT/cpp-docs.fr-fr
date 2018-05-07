---
title: Erreur irrécupérable C1905 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1905
dev_langs:
- C++
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15bf00432cab6900c252d85cd642c414bdbbb22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1905"></a>Erreur irrécupérable C1905
Front-end et back end non compatibles (doivent cibler le même processeur)  
  
 Cette erreur se produit quand un fichier .obj est généré par un compilateur frontal (C1.dll) qui cible un processeur, tel que x86, ARM ou [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], mais qui est lu par un compilateur principal (C2.dll) qui cible un processeur différent.  
  
 Pour résoudre ce problème, assurez-vous d'utiliser un compilateur frontal et un compilateur principal qui correspondent. Il s'agit du paramétrage par défaut pour les projets créés dans Visual Studio. Cette erreur peut se produire si vous avez modifié le fichier projet et utilisé des chemins d'accès aux outils de compilateur différents. Si vous n'avez pas spécifiquement défini de chemin d'accès pour les outils du compilateur, cette erreur peut survenir si votre installation de Visual Studio est endommagée. Par exemple, vous pouvez avoir copié les fichiers .dll du compilateur d'un emplacement à un autre. Utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.