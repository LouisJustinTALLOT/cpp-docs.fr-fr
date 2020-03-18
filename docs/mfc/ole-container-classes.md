---
title: Classes de conteneur OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447656"
---
# <a name="ole-container-classes"></a>Classes de conteneur OLE

Ces classes sont utilisées par les applications de conteneur. `COleLinkingDoc` et `COleDocument` gérer des collections d’objets `COleClientItem`. Plutôt que de dériver votre classe de document de `CDocument`, vous la dériverez de `COleLinkingDoc` ou `COleDocument`, selon que vous souhaitez ou non prendre en charge des liens vers des objets incorporés dans votre document.

Utilisez un objet `COleClientItem` pour représenter chaque élément OLE dans votre document qui est incorporé à partir d’un autre document ou qui est un lien vers un autre document.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Prend en charge la relation contenant-contenu de document actif.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Utilisé pour l’implémentation de document composite, ainsi que la prise en charge de conteneur de base. Sert de conteneur pour les classes dérivées de `CDocItem`. Cette classe peut être utilisée comme classe de base pour les documents de conteneur et est la classe de base pour `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Classe dérivée de `COleDocument` qui fournit l’infrastructure pour la liaison. Vous devez dériver les classes de document pour vos applications de conteneur à partir de cette classe au lieu de `COleDocument` si vous souhaitez qu’elles prennent en charge des liens vers des objets incorporés.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Conserve la liste des éléments du client OLE qui se trouvent dans le contrôle Rich Edit. Utilisé avec [CRichEditView](../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Classe de base abstraite de `COleClientItem` et `COleServerItem`. Les objets de classes dérivés de `CDocItem` représentent des parties de documents.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Classe d’élément client qui représente le côté client de la connexion à un élément OLE incorporé ou lié. Dérivez vos éléments clients à partir de cette classe.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Fournit un accès côté client à un élément OLE stocké dans un contrôle RichEdit lorsqu’il est utilisé avec `CRichEditView` et `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Exception résultant d’un échec dans le traitement OLE. Cette classe est utilisée par les conteneurs et les serveurs.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
