---
title: Relation contenant-contenu de Document actif | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74ad16aa453c6fa0df2c84bd0a0a789b05f83169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332671"
---
# <a name="active-document-containment"></a>Relation contenant-contenu de document actif
Relation contenant-contenu de document actif est une technologie qui fournit un frame unique permettant de travailler avec des documents, au lieu de vous obliger à créer et utiliser plusieurs frames d’application pour chaque type de document. Il diffère de technologie OLE de base dans la mesure où OLE fonctionne avec des objets incorporés dans un document composé dans lequel seule une partie du contenu peut être active. Avec la relation contenant-contenu de document actif, vous activez un document entier (autrement dit, une application entière, y compris les menus associés, les barres d’outils, etc.) dans le contexte d’un frame unique.  
  
 La technologie de relation contenant-contenu de document actif a été développée pour Microsoft Office doivent implémenter le classeur Office. Toutefois, la technologie est suffisamment flexible pour prendre en charge des conteneurs de documents actifs autres que le classeur Office et peut prendre en charge les serveurs de documents autres que les applications Office et compatible avec Office.  
  
 L’application qui héberge les documents actifs est appelée un [conteneur de documents actifs](../mfc/active-document-containers.md). Exemples de ces conteneurs sont le classeur Microsoft Office ou Microsoft Internet Explorer.  
  
 Relation contenant-contenu de document actif est implémenté comme un ensemble d’extensions vers OLE de documents, la technologie de document composé OLE. Les extensions sont des interfaces supplémentaires qui permettent à un objet incorporable, sur place représenter un document entier au lieu d’un seul élément de contenu incorporé. Comme avec les documents OLE, la relation contenant-contenu de document actif utilise un conteneur qui fournit l’espace d’affichage pour les documents actifs et les serveurs qui fournissent des fonctionnalités de manipulation et d’interface de l’utilisateur pour les documents actifs eux-mêmes.  
  
 Un [serveur de documents actifs](../mfc/active-document-servers.md) est une application (par exemple, Word, Excel ou PowerPoint) qui prend en charge un ou plusieurs classes de documents actifs, où chaque objet proprement dit prend en charge les interfaces d’extension qui permettent à l’objet à activer dans un conteneur approprié.  
  
 Un [document actif](../mfc/active-documents.md) (fourni à partir d’un serveur de documents actifs tels que Word ou Excel) est essentiellement un document à grande échelle, classique qui est incorporé en tant qu’objet dans un autre conteneur de documents actifs. Contrairement aux objets incorporés, les documents actifs ont un contrôle complet sur leurs pages, et l’interface complète de l’application (avec toutes ses sous-jacente commandes et outils) est disponible à l’utilisateur pour les modifier.  
  
 Un document actif de mieux comprendre distinguer un objet incorporé OLE standard. Selon la convention OLE, un objet incorporé est un qui s’affiche dans la page du document auquel il appartient, et le document est géré par un conteneur OLE. Le conteneur stocke les données de l’objet incorporé avec le reste du document. Toutefois, les objets incorporés sont limités dans la mesure où ils ne contrôlent pas la page sur laquelle ils apparaissent.  
  
 Les utilisateurs d’une application conteneur de documents actifs peuvent créer des documents actifs (appelés sections dans le classeur Office) à l’aide de leurs applications favorites (à condition que ces applications sont compatibles document actif), mais les utilisateurs peuvent gérer le projet résultant comme une une entité unique, qui permettre être nommée de manière unique, enregistré, impression, et ainsi de suite. De la même façon, un utilisateur d’un navigateur Internet peut traiter l’ensemble du réseau, ainsi que les systèmes de fichiers local, comme une entité de stockage de documents avec la possibilité de parcourir les documents que le stockage à partir d’un emplacement unique.  
  
## <a name="sample-programs"></a>Exemples de programmes  
  
-   Le [MFCBIND](../visual-cpp-samples.md) exemple illustre l’implémentation d’une application conteneur de documents actifs.  
  
## <a name="see-also"></a>Voir aussi  
 [MFC COM](../mfc/mfc-com.md)

