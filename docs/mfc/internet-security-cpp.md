---
title: Sécurité Internet (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4454eceae2cc5f2e6b46510fe95889c664a568a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348848"
---
# <a name="internet-security-c"></a>Sécurité Internet (C++)
Sécurité du code est un problème majeur pour les développeurs et les utilisateurs d’applications Internet. Il existe des risques : code malveillant, le code qui a été falsifié et code à partir des sites inconnus ou des auteurs.  
  
 Il existe deux approches de base à la sécurité lors du développement pour Internet. La première est appelée « sandboxing ». Dans cette approche, une application est limitée à un ensemble particulier d’API et exclue parmi ceux qui sont potentiellement dangereuses telles que les e/s de fichier où un programme risque de détruire les données sur l’ordinateur d’un utilisateur. La seconde est implémentée à l’aide de signatures numériques. Cette approche est appelée « film » pour Internet. Code est vérifié et signé à l’aide de la technologie de clé publique/privée. Avant que le code est exécuté, sa signature numérique est vérifiée pour s’assurer que le code provient d’une source authentifiée connue et que le code n’a pas été modifié depuis qu’il a été signé.  
  
 Dans le premier cas, vous faites confiance à l’application n’effectue aucun dommage que vous faites confiance à l’origine de l’application. Dans la seconde, les signatures numériques sont utilisées pour vérifier l’authenticité. La signature numérique est un standard utilisé pour identifier et fournissent des détails sur le serveur de publication du code. La technologie est basée sur des normes, notamment RSA et X.509. En règle générale, les navigateurs permettent aux utilisateurs de choisir s’ils veulent télécharger et exécuter le code d’origine inconnue.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

