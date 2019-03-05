---
title: 'Conteneurs : Éléments clients'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: 0c7f4a63cb9a31b52be2d3574ddad29313df6a4d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298280"
---
# <a name="containers-client-items"></a>Conteneurs : Éléments clients

Cet article décrit les éléments clients et que les classes votre application doit dériver ses éléments clients.

Éléments clients sont des éléments de données appartenant à une autre application qui sont contenues dans ou référencé par le document d’une application conteneur OLE. Éléments clients dont les données sont contenues dans le document sont incorporés ; ceux dont les données sont stockées dans un autre emplacement référencé par le document conteneur sont liés.

La classe de document dans une application OLE est dérivée de la classe [COleDocument](../mfc/reference/coledocument-class.md) plutôt qu’à partir `CDocument`. Le `COleDocument` hérite de la classe `CDocument` toutes les fonctionnalités nécessaires à l’utilisation de l’architecture document/vue sur le MFC sont basées les applications. `COleDocument` définit également une interface qui traite un document comme une collection de `CDocItem` objets. Plusieurs `COleDocument` des fonctions de membre sont fournies pour l’ajout, la récupération et la suppression d’éléments de cette collection.

Chaque application de conteneur doit dériver au moins une classe à partir de `COleClientItem`. Objets de cette classe représentent les éléments, incorporées ou liées, dans le document OLE. Ces objets existent pour la durée de vie du document qui les contient, sauf si elles sont supprimées du document.

`CDocItem` est la classe de base pour `COleClientItem` et `COleServerItem`. Objets de classes dérivées de ces deux agissent comme intermédiaire entre l’élément OLE et les applications clientes et serveur, respectivement. Chaque fois qu’un nouvel élément OLE est ajouté au document, l’infrastructure MFC ajoute un nouvel objet de votre application cliente `COleClientItem`-classe dérivée à la collection du document de `CDocItem` objets.

## <a name="see-also"></a>Voir aussi

[Conteneurs](../mfc/containers.md)<br/>
[Conteneurs : Fichiers composés](../mfc/containers-compound-files.md)<br/>
[Conteneurs : Problèmes d’Interface utilisateur](../mfc/containers-user-interface-issues.md)<br/>
[Conteneurs : Fonctionnalités avancées](../mfc/containers-advanced-features.md)<br/>
[COleClientItem, classe](../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem, classe](../mfc/reference/coleserveritem-class.md)
