---
title: Classes de serveur OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 99dd7f58b862fadc86ee2515bb8ef2008bc538fa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289577"
---
# <a name="ole-server-classes"></a>Classes de serveur OLE

Ces classes sont utilisées par les applications serveur. Documents de serveur sont dérivés de `COleServerDoc` plutôt qu’à partir `CDocument`. Étant donné que `COleServerDoc` est dérivée de `COleLinkingDoc`, documents de serveur peuvent également être des conteneurs qui prennent en charge la liaison.

Le `COleServerItem` classe représente un document ou une partie d’un document qui peut être incorporé dans un autre document ou lié à.

`COleIPFrameWnd` et `COleResizeBar` prennent en charge la modification sur place alors que l’objet est dans un conteneur, et `COleTemplateServer` prend en charge de la création de paires de document/vue de manière à pouvoir modifier les objets OLE à partir d’autres applications.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Utilisé comme classe de base pour les classes de document de l’application serveur. `COleServerDoc` objets fournissent la majeure partie de la prise en charge de serveur par le biais des interactions avec `COleServerItem` objets. Capacité d’édition Visual est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
De classe de base abstraite `COleClientItem` et `COleServerItem`. Les objets des classes dérivées de `CDocItem` représentent des parties de documents.

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Utilisé pour représenter l’interface OLE à `COleServerDoc` éléments. Il existe généralement un `COleServerDoc` objet qui représente la partie intégrante d’un document. Dans les serveurs qui prennent en charge des liens vers des parties de documents, il peut y avoir plusieurs `COleServerItem` objets, chacun d’eux représente un lien vers une partie du document.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est en cours de modification en place.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Fournit l’interface utilisateur standard pour le redimensionnement en place. Objets de cette classe sont toujours utilisés conjointement avec `COleIPFrameWnd` objets.

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Utilisé pour créer des documents à l’aide de l’architecture document/vue de l’infrastructure. Un `COleTemplateServer` objet délègue la majorité de son travail à associé à un `CDocTemplate` objet.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Une exception résultant d’une défaillance lors du traitement de OLE. Cette classe est utilisée par les conteneurs et les serveurs.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
