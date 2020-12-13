---
description: 'En savoir plus sur : création d’un modèle de document'
title: Création de modèle de document
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 60f85cf0a1c16e1aaa6057160c5b986001e18d84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330255"
---
# <a name="document-template-creation"></a>Création de modèle de document

Lorsque vous créez un nouveau document en réponse à une commande **nouveau** ou **ouvrir** à partir du menu **fichier** , le modèle de document crée également une nouvelle fenêtre frame par le biais de laquelle afficher le document.

Le constructeur de modèle de document spécifie les types de documents, fenêtres et vues que le modèle sera en mesure de créer. Cela est déterminé par les arguments passés au constructeur de modèle de document. Le code suivant illustre la création d’une [CMultiDocTemplate](reference/cmultidoctemplate-class.md) pour un exemple d’application :

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

Le pointeur vers un nouvel `CMultiDocTemplate` objet est utilisé en tant qu’argument pour [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate). Les arguments du `CMultiDocTemplate` constructeur incluent l’ID de ressource associé aux menus et accélérateurs du type de document, ainsi que trois utilisations de la macro [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) . `RUNTIME_CLASS` retourne l’objet [CRuntimeClass](reference/cruntimeclass-structure.md) pour la classe C++ nommée comme son argument. Les trois `CRuntimeClass` objets passés au constructeur de modèle de document fournissent les informations nécessaires pour créer de nouveaux objets des classes spécifiées pendant le processus de création de document. L’exemple montre la création d’un modèle de document qui crée des `CScribDoc` objets avec des `CScribView` objets attachés. Les vues sont encadrées par des fenêtres Frame enfants MDI standard.

## <a name="see-also"></a>Voir aussi

[Modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md)<br/>
[Création de document/vue](document-view-creation.md)<br/>
[Relations entre les objets MFC](relationships-among-mfc-objects.md)<br/>
[Création de documents, fenêtres et vues](creating-new-documents-windows-and-views.md)
