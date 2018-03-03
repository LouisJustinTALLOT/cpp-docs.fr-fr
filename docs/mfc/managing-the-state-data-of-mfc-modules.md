---
title: "Gestion des données d’état des Modules MFC | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d070bb91d9c1c229feaa563123c12702a7b5027
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Gestion des données d'état des modules MFC
Cet article décrit les données d’état des modules MFC et le mode de mise à jour de cet état lorsque le flux d’exécution (code du chemin d’accès via une application lors de l’exécution) accède à un module, puis le quitte. L'échange des états de modules avec les macros `AFX_MANAGE_STATE` et `METHOD_PROLOGUE` est également présenté.  
  
> [!NOTE]
>  Le terme "module" fait référence à un programme exécutable ou à une DLL (ou un ensemble de DLL) qui s'exécute indépendamment du reste de l'application, mais utilise une copie partagée de la DLL MFC. Un contrôle ActiveX est un exemple de module classique.  
  
 Comme illustré ci-dessous, MFC contient des données d'état pour chaque module utilisé dans une application. Les exemples de ces données sont les handles d'instance Windows (permettant de charger les ressources), les pointeurs vers les objets `CWinApp` et `CWinThread` actuels d'une application, le nombre de références de module OLE et plusieurs mappages qui maintiennent les connexions entre les handles d'objet Windows et les instances correspondantes d'objets MFC. Toutefois, lorsqu'une application utilise plusieurs modules, les données d'état de chaque module ne concernent pas toute l'application. En revanche, chaque module possède sa propre copie privée des données d'état de MFC.  
  
 ![Données d’état d’un seul module &#40; application &#41; ] (../mfc/media/vc387n1.gif "vc387n1")  
Données d'état d'un module unique (application)  
  
 Les données d'état d'un module sont contenus dans une structure et sont toujours disponibles via un pointeur à cette structure. Lorsque le flux d'exécution entre dans un module particulier, comme le montre l'illustration suivante, l'état du module doit être "actuel" ou "effectif". Par conséquent, chaque objet thread a un pointeur vers la structure d'état effectif de cette application. Conserver ce pointeur mis à niveau à tout moment est essentiel pour gérer l'état global de l'application et maintenir l'intégrité de l'état de chaque module. La gestion incorrecte de l'état global peut provoquer un comportement imprévisible de l'application.  
  
 ![État des données de plusieurs modules](../mfc/media/vc387n2.gif "vc387n2")  
Données d'état de plusieurs modules  
  
 En d'autres termes, chaque module est chargé de basculer correctement entre les états de module à tous ses points d'entrée. Un "point d'entrée" correspond à n'importe quel emplacement où le flux d'exécution peut accéder au code du module. Les points d'entrée sont les suivants :  
  
-   [Fonctions exportées dans une DLL](../mfc/exported-dll-function-entry-points.md)  
  
-   [Fonctions membres des interfaces COM](../mfc/com-interface-entry-points.md)  
  
-   [Procédures de fenêtre](../mfc/window-procedure-entry-points.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

