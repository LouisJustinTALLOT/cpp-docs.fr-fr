---
title: Classes de serveur OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 92dec514611dcce7d6c666fdd271843e69561637
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447588"
---
# <a name="ole-server-classes"></a>Classes de serveur OLE

Ces classes sont utilisées par les applications serveur. Les documents serveur sont dérivés de `COleServerDoc` plutôt que de `CDocument`. Notez que, étant donné que `COleServerDoc` est dérivée de `COleLinkingDoc`, les documents serveur peuvent également être des conteneurs qui prennent en charge la liaison.

La classe `COleServerItem` représente un document ou une partie d’un document qui peut être incorporé dans un autre document ou lié à.

`COleIPFrameWnd` et `COleResizeBar` prennent en charge la modification sur place lorsque l’objet se trouve dans un conteneur, et `COleTemplateServer` prend en charge la création de paires document/vue afin que les objets OLE d’autres applications puissent être modifiés.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Utilisé comme classe de base pour les classes de document de l’application serveur. les objets `COleServerDoc` fournissent l’essentiel de la prise en charge du serveur par le biais des interactions avec les objets `COleServerItem`. La fonctionnalité d’édition visuelle est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Classe de base abstraite de `COleClientItem` et `COleServerItem`. Les objets de classes dérivés de `CDocItem` représentent des parties de documents.

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Utilisé pour représenter l’interface OLE pour `COleServerDoc` éléments. Il y a généralement un objet `COleServerDoc`, qui représente la partie incorporée d’un document. Dans les serveurs qui prennent en charge des liens vers des parties de documents, il peut y avoir de nombreux objets `COleServerItem`, chacun représentant un lien vers une partie du document.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fournit la fenêtre frame pour une vue lorsqu’un document serveur est modifié sur place.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Fournit l’interface utilisateur standard pour le redimensionnement sur place. Les objets de cette classe sont toujours utilisés conjointement avec les objets `COleIPFrameWnd`.

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Utilisé pour créer des documents à l’aide de l’architecture document/vue de l’infrastructure. Un objet `COleTemplateServer` délègue la majeure partie de son travail à un objet `CDocTemplate` associé.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Exception résultant d’un échec dans le traitement OLE. Cette classe est utilisée par les conteneurs et les serveurs.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
