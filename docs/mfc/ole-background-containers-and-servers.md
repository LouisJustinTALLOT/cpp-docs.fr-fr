---
description: 'En savoir plus sur : arrière-plan OLE : conteneurs et serveurs'
title: 'Arrière-plan OLE : conteneurs et serveurs'
ms.date: 11/04/2016
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
ms.openlocfilehash: 3ea578ce14165b16e84520b22bc545fc5d2a8882
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254773"
---
# <a name="ole-background-containers-and-servers"></a>Arrière-plan OLE : conteneurs et serveurs

Une application conteneur est une application qui peut incorporer des éléments incorporés ou liés dans ses propres documents. Les documents gérés par une application de conteneur doivent être en mesure de stocker et d’afficher des composants de document OLE, ainsi que les données créées par l’application elle-même. Une application conteneur doit également permettre aux utilisateurs d’insérer de nouveaux éléments ou de modifier des éléments existants en activant des applications serveur si nécessaire. Les spécifications de l’interface utilisateur d’une application conteneur sont répertoriées dans l’article [conteneurs : User-Interface problèmes](containers-user-interface-issues.md).

Une application serveur ou une application de composant est une application qui peut créer des composants de document OLE pour une utilisation par les applications de conteneur. Les applications serveur prennent généralement en charge le glisser-déplacer ou la copie de leurs données dans le presse-papiers afin qu’une application conteneur puisse insérer les données sous la forme d’un élément incorporé ou lié. Une application peut être à la fois un conteneur et un serveur.

La plupart des serveurs sont des applications autonomes ou des serveurs complets. ils peuvent être exécutés en tant qu’applications autonomes ou peuvent être lancés par une application de conteneur. Un mini-serveur est un type spécial d’application serveur qui peut être lancé uniquement par un conteneur. Il ne peut pas être exécuté en tant qu’application autonome. Les serveurs Microsoft Draw et Microsoft Graph sont des exemples de miniservers.

Les conteneurs et les serveurs ne communiquent pas directement. Au lieu de cela, ils communiquent via les bibliothèques de liens dynamiques (DLL) du système OLE. Ces dll fournissent des fonctions que les conteneurs et les serveurs appellent, et les conteneurs et les serveurs fournissent des fonctions de rappel appelées par les dll.

À l’aide de ce moyen de communication, un conteneur n’a pas besoin de connaître les détails de l’implémentation de l’application serveur. Il permet à un conteneur d’accepter des éléments créés par n’importe quel serveur sans avoir à définir les types de serveurs avec lesquels il peut fonctionner. Par conséquent, l’utilisateur d’une application de conteneur peut tirer parti des applications et des formats de données futurs. Si ces nouvelles applications sont des composants OLE, un document composé peut incorporer des éléments créés par ces applications.

## <a name="see-also"></a>Voir aussi

[Arrière-plan OLE](ole-background.md)<br/>
[Arrière-plan OLE : implémentation MFC](ole-background-mfc-implementation.md)<br/>
[Containers](containers.md)<br/>
[Serveurs](servers.md)<br/>
[Conteneurs : éléments clients](containers-client-items.md)<br/>
[Serveurs : éléments du serveur](servers-server-items.md)
