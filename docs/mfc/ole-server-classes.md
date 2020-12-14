---
description: 'En savoir plus sur : classes de serveur OLE'
title: Classes de serveur OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: a2f60f148d6a24323ca6546e633c30103b315ee2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243989"
---
# <a name="ole-server-classes"></a>Classes de serveur OLE

Ces classes sont utilisées par les applications serveur. Les documents serveur sont dérivés de `COleServerDoc` plutôt que de `CDocument` . Notez que étant donné que `COleServerDoc` est dérivé de `COleLinkingDoc` , les documents serveur peuvent également être des conteneurs qui prennent en charge la liaison.

La `COleServerItem` classe représente un document ou une partie d’un document qui peut être incorporé dans un autre document ou lié à.

`COleIPFrameWnd` et `COleResizeBar` prennent en charge la modification sur place lorsque l’objet se trouve dans un conteneur et `COleTemplateServer` prennent en charge la création de paires document/vue afin que les objets OLE d’autres applications puissent être modifiés.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Utilisé comme classe de base pour les classes de document de l’application serveur. `COleServerDoc` les objets fournissent l’essentiel de la prise en charge du serveur par le biais des interactions avec les `COleServerItem` objets. La fonctionnalité d’édition visuelle est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.

[CDocItem](reference/cdocitem-class.md)<br/>
Classe de base abstraite de `COleClientItem` et `COleServerItem` . Les objets de classes dérivés de `CDocItem` représentent des parties de documents.

[COleServerItem](reference/coleserveritem-class.md)<br/>
Utilisé pour représenter l’interface OLE aux `COleServerDoc` éléments. Il y a généralement un `COleServerDoc` objet, qui représente la partie incorporée d’un document. Dans les serveurs qui prennent en charge des liens vers des parties de documents, il peut y avoir de nombreux `COleServerItem` objets, chacun représentant un lien vers une partie du document.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est modifié sur place.

[COleResizeBar](reference/coleresizebar-class.md)<br/>
Fournit l’interface utilisateur standard pour le redimensionnement sur place. Les objets de cette classe sont toujours utilisés conjointement avec les `COleIPFrameWnd` objets.

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
Utilisé pour créer des documents à l’aide de l’architecture document/vue de l’infrastructure. Un `COleTemplateServer` objet délègue la majeure partie de son travail à un `CDocTemplate` objet associé.

[COleException](reference/coleexception-class.md)<br/>
Exception résultant d’un échec dans le traitement OLE. Cette classe est utilisée par les conteneurs et les serveurs.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
