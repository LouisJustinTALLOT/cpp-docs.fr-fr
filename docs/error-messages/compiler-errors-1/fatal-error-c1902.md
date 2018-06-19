---
title: Erreur irrécupérable C1902 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23507b6531f9ee4e5ce5efd5b60a1977206635c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228197"
---
# <a name="fatal-error-c1902"></a>Erreur irrécupérable C1902
incompatibilité de gestionnaire de base de données de programme ; Veuillez vérifier votre installation  
  
Un fichier de base de données de programme (.pdb) a été créé à l’aide d’une version plus récente de mspdb*XXX*.dll que celui que le compilateur a trouvé sur votre système. Cette erreur indique habituellement que mspdbsrv.exe ou mspdbcore.dll sont manquants ou ont des versions différentes de mspdb*XXX*.dll. (Le *XXX* espace réservé dans le mspdb*XXX*nom de fichier .dll change avec chaque version du produit. Par exemple, dans Visual Studio 2015, le nom de fichier est mspdb140.dll.)  
  
Vérifiez les versions correspondantes de mspdbsrv.exe, mspdbcore.dll et mspdb*XXX*.dll sont installés sur votre système. Assurez-vous que les versions incompatibles n’ont pas été copiées vers le répertoire qui contient les outils du compilateur et des liens pour votre plateforme cible. Par exemple, vous pourrez avoir copié les fichiers afin de vous pouvez appeler le compilateur ou l’outil link à partir de l’invite de commandes sans définir la **chemin d’accès** variable d’environnement en conséquence.