---
title: Création d’un modèle de document | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1a9067929e96c6d3fd851168af079e7e825dcb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443630"
---
# <a name="document-template-creation"></a>Création de modèle de document

Lors de la création d’un nouveau document en réponse à une **New** ou **Open** commande à partir de la **fichier** menu, le modèle de document crée également une nouvelle fenêtre de frame par le biais duquel afficher le document.

Le constructeur de modèle de document spécifie les types de documents, windows et le modèle sera en mesure de créer des vues. Cela est déterminé par les arguments que vous passez au constructeur de modèle de document. Le code suivant illustre la création d’un [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) pour un exemple d’application :

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

Le pointeur vers une nouvelle `CMultiDocTemplate` objet est utilisé en tant qu’argument à [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Arguments à la `CMultiDocTemplate` constructeur incluent l’ID de ressource associé aux menus et les accélérateurs du type de document, et trois utilisations de la [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) macro. `RUNTIME_CLASS` Retourne le [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objet pour la classe C++ nommée comme argument. Les trois `CRuntimeClass` objets passés au constructeur de modèle de document fournissent les informations nécessaires pour créer de nouveaux objets des classes spécifiées pendant le processus de création de document. L’exemple illustre la création d’un modèle de document crée `CScribDoc` objets avec `CScribView` objets attachés. Les vues sont encadrées par des fenêtres frame enfants MDI standard.

## <a name="see-also"></a>Voir aussi

[Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création d’un document/vue](../mfc/document-view-creation.md)<br/>
[Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

