---
title: Création d’une Application de conteneur de documents actifs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1b20dd592e180122e119b08ab59babfdaae8d54
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052801"
---
# <a name="creating-an-active-document-container-application"></a>Création d'une application conteneur de documents actifs

La façon la plus simple et plus recommandée pour créer une application de conteneur de documents actifs consiste à créer une application de conteneur EXE MFC à l’aide de l’Assistant Application MFC, puis modifiez l’application pour prendre en charge de la relation contenant-contenu de document actif.

#### <a name="to-create-an-active-document-container-application"></a>Pour créer une application de conteneur de documents actifs

1. À partir de la **fichier** menu, cliquez sur **projet**à partir de la **New** sous-menu.

1. Dans le volet gauche, cliquez sur **Visual C++** type de projet.

1. Sélectionnez **Application MFC** dans le volet droit.

1. Nommez le projet *MyProj*, cliquez sur **OK**.

1. Sélectionnez le **prise en charge des documents composés** page.

1. Sélectionnez le **conteneur** ou **conteneur/serveur complet** option.

1. Sélectionnez le **conteneur de documents actifs** case à cocher.

1. Cliquez sur **Terminer**.

9. Lorsque l’Assistant Application MFC a terminé de générer l’application, ouvrez les fichiers suivants à l’aide de l’Explorateur de solutions :

   - *MyProjview.cpp*

10. Dans *MyProjview.cpp*, apportez les modifications suivantes :

   - Dans `CMyProjView::OnPreparePrinting`, remplacez le contenu de la fonction par le code suivant :

         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` prend en charge l’impression. Ce code remplace `DoPreparePrinting`, qui repose sur la préparation d’impression par défaut.

   Relation contenant-contenu de document actif fournit un schéma d’impression amélioré :

   - Vous pouvez tout d’abord appeler le document actif via son `IPrint` interface et lui dire s’imprime. Ceci diffère du précédent OLE relation contenant-contenu, dans lequel le conteneur devait restituer une image de l’élément de contenu sur l’imprimante `CDC` objet.

   - En cas d’échec, indiquer à l’élément de relation contenant-contenu pour imprimer lui-même via son `IOleCommandTarget` interface

   - Si cette tentative échoue, vérifiez votre propre rendu de l’élément.

   Les fonctions membres statiques `COleDocObjectItem::OnPrint` et `COleDocObjectItem::OnPreparePrinting`, tel qu’implémenté dans le code précédent, gèrent ce schéma d’impression amélioré.

11. Ajouter votre propre implémentation et générez l’application.

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](../mfc/active-document-containment.md)

