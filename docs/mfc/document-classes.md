---
title: Classes de documents
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615801"
---
# <a name="document-classes"></a>Classes de documents

Les objets de classe de document, créés par des objets de modèle de document, gèrent les données de l’application. Vous allez dériver une classe pour vos documents à partir de l’une de ces classes.

Les objets de classe de document interagissent avec les objets de vue. Les objets de vue représentent la zone cliente d’une fenêtre, affichent les données d’un document et permettent aux utilisateurs d’interagir avec lui. Les documents et les vues sont créés par un objet de modèle de document.

[CDocument](reference/cdocument-class.md)<br/>
Classe de base pour les documents spécifiques à l’application. Dérivez votre classe de document ou vos classes à partir de `CDocument` .

[COleDocument](reference/coledocument-class.md)<br/>
Utilisé pour l’implémentation de document composite, ainsi que la prise en charge de conteneur de base. Sert de conteneur pour les classes dérivées de [CDocItem](reference/cdocitem-class.md). Cette classe peut être utilisée comme classe de base pour les documents de conteneur et est la classe de base pour `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Classe dérivée de `COleDocument` qui fournit l’infrastructure pour la liaison. Vous devez dériver les classes de document pour vos applications de conteneur à partir de cette classe plutôt que de `COleDocument` si vous souhaitez qu’elles prennent en charge des liens vers des objets incorporés.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Conserve la liste des éléments du client OLE qui se trouvent dans le contrôle Rich Edit. Utilisé avec [CRichEditView](reference/cricheditview-class.md) et [CRichEditCntrItem](reference/cricheditcntritem-class.md).

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Utilisé comme classe de base pour les classes de document de l’application serveur. `COleServerDoc`les objets fournissent l’essentiel de la prise en charge du serveur par le biais d’interactions avec les objets [COleServerItem](reference/coleserveritem-class.md) . La fonctionnalité d’édition visuelle est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
Fournit, avec [CHtmlEditView](reference/chtmleditview-class.md), les fonctionnalités de la plateforme d’édition HTML WebBrowser dans le contexte de l’architecture document/vue de MFC.

## <a name="related-classes"></a>Classes connexes

Les objets de classe de document peuvent être persistants, en d’autres termes, ils peuvent écrire leur état sur un support de stockage et le lire à nouveau. MFC fournit la `CArchive` classe pour faciliter le transfert des données du document sur un support de stockage.

[CArchive](reference/carchive-class.md)<br/>
Fonctionne avec un objet [CFile](reference/cfile-class.md) pour implémenter un stockage persistant pour les objets via la sérialisation (voir [CObject :: Serialize](reference/cobject-class.md#serialize)).

Les documents peuvent également contenir des objets OLE. `CDocItem`est la classe de base des éléments serveur et client.

[CDocItem](reference/cdocitem-class.md)<br/>
Classe de base abstraite de [COleClientItem](reference/coleclientitem-class.md) et [COleServerItem](reference/coleserveritem-class.md). Les objets de classes dérivés de `CDocItem` représentent des parties de documents.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
