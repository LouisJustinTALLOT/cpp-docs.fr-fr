---
title: 'Conteneurs : éléments clients'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: ad347c78fb6aa7af94b306a3edb538b9f740c305
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619016"
---
# <a name="containers-client-items"></a>Conteneurs : éléments clients

Cet article explique ce que sont les éléments client et à partir des classes que votre application doit dériver pour ses éléments clients.

Les éléments clients sont des éléments de données appartenant à une autre application, qui sont contenus dans le document d’une application conteneur OLE ou référencés par celui-ci. Les éléments clients dont les données sont contenues dans le document sont incorporés ; celles dont les données sont stockées dans un autre emplacement référencé par le document conteneur sont liées.

La classe de document dans une application OLE est dérivée de la classe [COleDocument](reference/coledocument-class.md) plutôt que de `CDocument` . La `COleDocument` classe hérite de `CDocument` toutes les fonctionnalités nécessaires à l’utilisation de l’architecture document/vue sur laquelle sont basées les applications MFC. `COleDocument`définit également une interface qui traite un document comme une collection d' `CDocItem` objets. Plusieurs `COleDocument` fonctions membres sont fournies pour ajouter, récupérer et supprimer des éléments de cette collection.

Chaque application conteneur doit dériver au moins une classe de `COleClientItem` . Les objets de cette classe représentent des éléments, incorporés ou liés, dans le document OLE. Ces objets existent pendant la durée de vie du document qui les contient, sauf s’ils sont supprimés du document.

`CDocItem`est la classe de base pour `COleClientItem` et `COleServerItem` . Les objets de classes dérivés de ces deux jouent le rôle d’intermédiaires entre l’élément OLE et les applications clientes et serveur, respectivement. Chaque fois qu’un nouvel élément OLE est ajouté au document, l’infrastructure MFC ajoute un nouvel objet de la classe dérivée de votre application cliente `COleClientItem` à la collection d' `CDocItem` objets du document.

## <a name="see-also"></a>Voir aussi

[Containers](containers.md)<br/>
[Conteneurs : fichiers composés](containers-compound-files.md)<br/>
[Conteneurs : problèmes d'interface utilisateur](containers-user-interface-issues.md)<br/>
[Conteneurs : fonctionnalités avancées](containers-advanced-features.md)<br/>
[COleClientItem (classe)](reference/coleclientitem-class.md)<br/>
[COleServerItem, classe](reference/coleserveritem-class.md)
