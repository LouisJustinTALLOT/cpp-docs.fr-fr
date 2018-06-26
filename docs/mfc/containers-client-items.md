---
title: 'Conteneurs : Éléments clients | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a7b498ed1ddc3a3d040abde6ebcb7e27615b801
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929341"
---
# <a name="containers-client-items"></a>Conteneurs : éléments clients
Cet article décrit les éléments clients et à partir de quelles classes votre application doit dériver ses éléments clients.  
  
 Éléments clients sont des éléments de données appartenant à une autre application qui sont contenues dans ou référencé par document d’une application conteneur OLE. Éléments clients dont les données sont contenues dans le document sont incorporés ; ceux dont les données sont stockées dans un autre emplacement référencé par le document conteneur sont liés.  
  
 La classe de document dans une application OLE est dérivée de la classe [COleDocument](../mfc/reference/coledocument-class.md) plutôt qu’à partir de `CDocument`. Le `COleDocument` hérite de la classe `CDocument` toutes les fonctionnalités nécessaires à l’utilisation de l’architecture document/vue dans le MFC sont basées les applications. `COleDocument` définit également une interface qui traite un document comme une collection de `CDocItem` objets. Plusieurs `COleDocument` des fonctions de membre sont fournies pour l’ajout, de la récupération et de suppression d’éléments de cette collection.  
  
 Chaque application de conteneur doit dériver au moins une classe à partir de `COleClientItem`. Objets de cette classe représentent les éléments, incorporées ou liées, dans le document OLE. Ces objets existent pour la durée de vie du document qui les contiennent, sauf si elles sont supprimées du document.  
  
 `CDocItem` est la classe de base pour `COleClientItem` et `COleServerItem`. Objets de classes dérivées de ces deux agissent comme intermédiaires entre l’élément OLE et les applications clientes et serveur, respectivement. Chaque fois qu’un nouvel élément OLE est ajouté au document, l’infrastructure MFC ajoute un nouvel objet de votre application cliente `COleClientItem`-classe dérivée à la collection du document de `CDocItem` objets.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs](../mfc/containers.md)   
 [Conteneurs : Fichiers composés](../mfc/containers-compound-files.md)   
 [Conteneurs : Problèmes d’Interface utilisateur](../mfc/containers-user-interface-issues.md)   
 [Conteneurs : Fonctionnalités avancées](../mfc/containers-advanced-features.md)   
 [Classe de COleClientItem](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem, classe](../mfc/reference/coleserveritem-class.md)
