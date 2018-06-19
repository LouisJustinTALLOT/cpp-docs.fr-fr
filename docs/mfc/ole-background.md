---
title: Arrière-plan OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 262eee08e1bea410fd8e6d12d9209d35877e4a5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355559"
---
# <a name="ole-background"></a>Arrière-plan OLE
OLE est un mécanisme qui permet aux utilisateurs de créer et de modifier des documents contenant des éléments ou "objets" créés par plusieurs applications.  
  
> [!NOTE]
>  OLE est à l'origine un acronyme désignant la liaison et l'incorporation d'objets. Toutefois, il est maintenant appelé OLE. Les parties OLE non liées à la liaison et l'incorporation font partie de la technologie Active.  
  
 Les documents OLE, historiquement appelés documents composés, intègrent de façon transparente des types de données, ou composants. Les clips audio, les feuilles de calcul et les bitmaps sont des exemples typiques des composants détectés dans les documents OLE. La prise en charge OLE dans votre application permet aux utilisateurs d'utiliser des documents OLE sans vous préoccuper du basculement entre les différentes applications ; OLE effectue le basculement pour vous.  
  
 Utilisez une application conteneur pour créer des documents composés et une application serveur ou une application de composant pour créer des éléments dans le document conteneur. Toute application que vous écrivez peut être un conteneur, un serveur, ou les deux.  
  
 OLE incorpore différents concepts qui permettent d'atteindre l'objectif d'interaction transparente entre les applications. Ces domaines sont les suivants :  
  
 Liaison et incorporation  
 La liaison et l'incorporation sont les deux méthodes permettant de stocker des éléments créés dans un document OLE alors qu'ils ont été créés dans une autre application. Pour obtenir des informations générales sur les différences entre les deux, consultez l’article [arrière-plan OLE : liaison et incorporation](../mfc/ole-background-linking-and-embedding.md). Pour plus d’informations, consultez les articles [conteneurs](../mfc/containers.md) et [serveurs](../mfc/servers.md).  
  
 Activation en place (modification visuelle)  
 L'activation d'un élément incorporé dans le contexte du document conteneur est appelée activation en place ou modification visuelle. L’interface de l’application conteneur change afin d’incorporer les fonctionnalités de l’application du composant qui a créé l’élément incorporé. Les éléments liés ne sont jamais activés en place car les données réelles de l'élément sont contenues dans un fichier distinct, hors du contexte de l'application qui contient la liaison. Pour plus d’informations sur l’activation sur place, consultez l’article [Activation](../mfc/activation-cpp.md).  
  
> [!NOTE]
>  La liaison et l’incorporation, ainsi que l’activation en place fournissent les principales fonctionnalités de la modification visuelle OLE.  
  
 Automation  
 L'Automation permet à une application de piloter une autre application. L'application pilotante correspond à un client Automation, et l'application qui est contrôlée est appelée serveur Automation ou composant Automation. Pour plus d’informations sur l’automatisation, consultez les articles [Clients Automation](../mfc/automation-clients.md) et [serveurs Automation](../mfc/automation-servers.md).  
  
> [!NOTE]
>  L'automation s'exécute dans les contextes de technologie OLE et Active. Vous pouvez automatiser un objet basé sur un modèle COM.  
  
 Fichiers composés  
 Les fichiers composés fournissent un format de fichier standard qui simplifie le stockage structuré de documents composés pour les applications OLE. Dans un fichier composé, les stockages ont de nombreuses fonctionnalités de répertoires et les flux ont de nombreuses fonctionnalités de fichiers. Cette technologie est également appelée stockage structuré. Pour plus d’informations sur les fichiers composés, consultez l’article [conteneurs : fichiers composés](../mfc/containers-compound-files.md).  
  
 Transfert de données uniforme  
 Le transfert de données uniforme (UDT, Uniform Data Transfer) est un ensemble d'interfaces qui fournissent des données à envoyer et reçues en mode standard, quelle que soit la méthode active choisie pour transférer les données. Le transfert UDT forme la base des transferts de données via la méthode Glisser-déplacer. Elle sert de base pour transférer des données Windows existantes, tel que le Presse-papiers et l'échange dynamique de données (DDE). Pour plus d’informations sur UDT, consultez l’article [des objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Glisser-déposer  
 La fonction Glisser-déplacer est une technique simple d'utilisation, de manipulation directe pour transférer des données entre les applications, les fenêtres d'une application, ou même dans une seule fenêtre d'application. Les données à transférer sont sélectionnées et déposées à la destination souhaitée. La fonction Glisser-déposer est basée sur le transfert de données uniforme. Pour plus d’informations sur la fonction glisser- déposer, consultez l’article [glisser- déposer](../mfc/drag-and-drop-ole.md).  
  
 Component Object Model  
 Le modèle COM (Component Object Model) fournit le framework utilisée lorsque les objets OLE communiquent entre eux. Les classes OLE MFC simplifient le modèle COM du programmeur. Le modèle COM fait partie de la technologie Active, car les objets COM offrent les deux technologies, OLE et Active. Pour plus d’informations sur COM, consultez le [bibliothèque ATL (Active Template)](../atl/active-template-library-atl-concepts.md) rubriques.  
  
 Certaines des rubriques OLE les plus importantes sont traitées dans les articles suivants :  
  
-   [Arrière-plan OLE : liaison et incorporation](../mfc/ole-background-linking-and-embedding.md)  
  
-   [Arrière-plan OLE : conteneurs et serveurs](../mfc/ole-background-containers-and-servers.md)  
  
-   [Arrière-plan OLE : stratégies d’implémentation](../mfc/ole-background-implementation-strategies.md)  
  
-   [Arrière-plan OLE : implémentation MFC](../mfc/ole-background-mfc-implementation.md)  
  
 Pour obtenir d'autres informations OLE manquantes dans les articles ci-dessus, effectuez des recherches sur OLE dans MSDN.  
  
## <a name="see-also"></a>Voir aussi  
 [OLE](../mfc/ole-in-mfc.md)

