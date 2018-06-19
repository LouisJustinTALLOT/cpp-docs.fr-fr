---
title: 'Arrière-plan OLE : Conteneurs et serveurs | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f15ef532ba61a089f8adec9ed20f737c07eae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348545"
---
# <a name="ole-background-containers-and-servers"></a>Arrière-plan OLE : conteneurs et serveurs
Une application conteneur est une application qui peut incorporer des éléments liés ou incorporés dans ses propres documents. Les documents gérés par une application conteneur doivent être en mesure de stocker et afficher les composants de document OLE ainsi que les données créées par l’application elle-même. Une application conteneur doit également permettre aux utilisateurs d’insérer de nouveaux éléments ou de modifier des éléments existants en activant les applications serveur si nécessaire. Les exigences de l’interface utilisateur d’une application conteneur sont répertoriés dans l’article [conteneurs : problèmes d’Interface utilisateur](../mfc/containers-user-interface-issues.md).  
  
 Une application serveur ou une application du composant est une application qui peut créer des composants de document OLE pour une utilisation par les applications de conteneur. Serveur d’applications prend généralement en charge glisser-déplacer ou copier leurs données dans le Presse-papiers afin qu’une application conteneur peut insérer les données sous la forme d’un élément incorporé ou lié. Une application peut être un conteneur et un serveur.  
  
 La plupart des serveurs sont des applications autonomes ou des serveurs complets ; ils peuvent être exécutés en tant qu’applications autonomes ou peuvent être lancés par une application conteneur. Un mini-serveur est un type spécial d’application serveur qui peut être lancé uniquement par un conteneur. Il ne peut pas être exécuté comme une application autonome. Les serveurs Microsoft Draw et Microsoft Graph sont des exemples de mini-serveurs.  
  
 Conteneurs et les serveurs ne communiquent pas directement. Au lieu de cela, ils communiquent via les bibliothèques de liens dynamiques du système OLE (DLL). Ces DLL fournissent des fonctions qui appellent des conteneurs et les serveurs et les conteneurs et les serveurs fournissent des fonctions de rappel que l’appel des DLL.  
  
 À l’aide de ce moyen de communication, un conteneur n’a pas besoin de connaître les détails d’implémentation de l’application serveur. Il permet à un conteneur d’accepter les éléments créés par n’importe quel serveur sans avoir à définir les types de serveurs avec lesquels il peut fonctionner. Par conséquent, l’utilisateur d’une application conteneur peut profiter des applications futures et formats de données. Si ces nouvelles applications sont des composants OLE, un document composé sera en mesure d’incorporer des éléments créés par ces applications.  
  
## <a name="see-also"></a>Voir aussi  
 [Arrière-plan OLE](../mfc/ole-background.md)   
 [Arrière-plan OLE : Implémentation MFC](../mfc/ole-background-mfc-implementation.md)   
 [Conteneurs](../mfc/containers.md)   
 [Serveurs](../mfc/servers.md)   
 [Conteneurs : Éléments clients](../mfc/containers-client-items.md)   
 [Serveurs : éléments du serveur](../mfc/servers-server-items.md)

