---
title: PRJ0006 d’erreur de Build de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151c22bf13c13de21e89a5c96185cf1c4c1ca349
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317477"
---
# <a name="project-build-error-prj0006"></a>Erreur de génération de projet PRJ0006
N’a pas pu ouvrir le fichier temporaire 'fichier'. Assurez-vous que le fichier existe et que le répertoire n’est pas protégé en écriture.  
  
 Visual C++ n’a pas pu créer un fichier temporaire pendant le processus de génération. Raisons sont les suivantes :  
  
-   Pas de répertoire temporaire.  
  
-   Répertoire temporaire en lecture seule.  
  
-   Espace disque insuffisant.  
  
-   Le dossier $ (IntDir) est en lecture seule ou contient des fichiers temporaires qui sont en lecture seule.  
  
 Cette erreur se produit également après l’erreur PRJ0007 : Impossible de créer le répertoire de sortie 'répertoire'. L’erreur PRJ0007 signifie que le répertoire $ (IntDir) n’a pas pu être créé, ce qui implique la création de fichiers temporaires échouera également.  
  
 Fichiers temporaires sont créés chaque fois que vous spécifiez :  
  
-   Un fichier réponse.  
  
-   Une étape de génération personnalisée.  
  
-   Un événement de build.