---
title: Classes de documents
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: eee8cf874230874b519bbd2cb3ebb34c7d4c5c80
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484628"
---
# <a name="document-classes"></a>Classes de documents

Objets de classe de document, créés par les objets de modèle de document, gérer les données de l’application. Vous serez dériver une classe pour vos documents à partir d’une de ces classes.

Les objets de classe de document interagissent avec les objets de vue. Afficher les objets représentent la zone cliente d’une fenêtre, affichent les données d’un document et permettent aux utilisateurs d’interagir avec lui. Documents et vues sont créées par un objet de modèle de document.

[CDocument](../mfc/reference/cdocument-class.md)<br/>
La classe de base pour les documents spécifiques à l’application. Dériver votre classe de document ou les classes de `CDocument`.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Utilisé pour l’implémentation de document composé, ainsi que la prise en charge du conteneur de base. Sert de conteneur pour les classes dérivées de [CDocItem](../mfc/reference/cdocitem-class.md). Cette classe peut être utilisée comme classe de base pour le conteneur de documents et est la classe de base pour `COleServerDoc`.

[COleLinkingDoc plutôt](../mfc/reference/colelinkingdoc-class.md)<br/>
Une classe dérivée de `COleDocument` qui fournit l’infrastructure de la liaison. Vous devez dériver les classes de document pour vos applications de conteneur à partir de cette classe au lieu de `COleDocument` si vous voulez qu’ils prennent en charge des liens vers des objets incorporés.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Gère la liste des éléments client OLE qui se trouvent dans le contrôle RichEdit. Utilisé avec [CRichEditView](../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Utilisé comme classe de base pour les classes de document de l’application serveur. `COleServerDoc` objets fournissent la majeure partie de la prise en charge de serveur par le biais des interactions avec [COleServerItem](../mfc/reference/coleserveritem-class.md) objets. Capacité d’édition Visual est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
Fournit, avec [CHtmlEditView](../mfc/reference/chtmleditview-class.md), les fonctionnalités de la plateforme d’édition WebBrowser HTML dans le contexte de l’architecture document / vue MFC.

## <a name="related-classes"></a>Classes connexes

Les objets de classe de document peuvent être persistants — en d’autres termes, ils peuvent écrire leur état dans un support de stockage et les lire. MFC fournit la `CArchive` classe afin de faciliter le transfert de données du document vers un support de stockage.

[CArchive](../mfc/reference/carchive-class.md)<br/>
Collabore avec un [CFile](../mfc/reference/cfile-class.md) objet pour implémenter le stockage persistant pour les objets via la sérialisation (consultez [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

Documents peuvent également contenir des objets OLE. `CDocItem` est la classe de base des éléments de serveur et client.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
De classe de base abstraite [COleClientItem](../mfc/reference/coleclientitem-class.md) et [COleServerItem](../mfc/reference/coleserveritem-class.md). Les objets des classes dérivées de `CDocItem` représentent des parties de documents.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

