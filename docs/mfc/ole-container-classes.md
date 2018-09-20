---
title: Classes de conteneur OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e17161340881bb53601bc04dce6f5e375f746b02
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404707"
---
# <a name="ole-container-classes"></a>Classes de conteneur OLE

Ces classes sont utilisées par les applications de conteneur. Les deux `COleLinkingDoc` et `COleDocument` gérer des collections de `COleClientItem` objets. Au lieu de dériver votre classe de document à partir de `CDocument`, vous allez dérivez-le de `COleLinkingDoc` ou `COleDocument`, selon que vous souhaitez la prise en charge pour des liens vers des objets incorporés dans votre document.

Utilisez un `COleClientItem` objet pour représenter chaque élément OLE dans votre document qui est incorporé à partir d’un autre document ou un lien vers un autre document.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Prend en charge de la relation contenant-contenu de document actif.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Utilisé pour l’implémentation de document composé, ainsi que la prise en charge du conteneur de base. Sert de conteneur pour les classes dérivées de `CDocItem`. Cette classe peut être utilisée comme classe de base pour le conteneur de documents et est la classe de base pour `COleServerDoc`.

[COleLinkingDoc plutôt](../mfc/reference/colelinkingdoc-class.md)<br/>
Une classe dérivée de `COleDocument` qui fournit l’infrastructure de la liaison. Vous devez dériver les classes de document pour vos applications de conteneur à partir de cette classe au lieu de `COleDocument` si vous voulez qu’ils prennent en charge des liens vers des objets incorporés.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Gère la liste des éléments client OLE qui se trouvent dans le contrôle RichEdit. Utilisé avec [CRichEditView](../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
De classe de base abstraite `COleClientItem` et `COleServerItem`. Les objets des classes dérivées de `CDocItem` représentent des parties de documents.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Une classe d’élément client qui représente le côté client de la connexion à un élément OLE incorporé ou lié. Dériver les éléments de votre client de cette classe.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Fournit un accès côté client à l’élément stocké dans un contrôle RichEdit lorsqu’il est utilisé avec OLE `CRichEditView` et `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Une exception résultant d’une défaillance lors du traitement de OLE. Cette classe est utilisée par les conteneurs et les serveurs.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

