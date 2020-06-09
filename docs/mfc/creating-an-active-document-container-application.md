---
title: Création d'une application conteneur de documents actifs
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616353"
---
# <a name="creating-an-active-document-container-application"></a>Création d'une application conteneur de documents actifs

La méthode la plus simple et la plus recommandée pour créer une application de conteneur de documents actifs consiste à créer une application de conteneur EXE MFC à l’aide de l’Assistant Application MFC, puis à modifier l’application pour prendre en charge la relation contenant-contenu de document actif.

#### <a name="to-create-an-active-document-container-application"></a>Pour créer une application de conteneur de documents actifs

1. Dans le menu **fichier** , cliquez sur **projet**dans le sous-menu **nouveau** .

1. Dans le volet gauche, cliquez sur **Visual C++** type de projet.

1. Sélectionnez **application MFC** dans le volet droit.

1. Nommez le projet *MyProj*, puis cliquez sur **OK**.

1. Sélectionnez la page **prise en charge des documents composés** .

1. Sélectionnez l’option **conteneur** ou **conteneur/serveur complet** .

1. Activez la case à cocher **conteneur de documents actifs** .

1. Cliquez sur **Terminer**.

1. Lorsque l’Assistant Application MFC termine la génération de l’application, ouvrez les fichiers suivants à l’aide de Explorateur de solutions :

   - *MyProjview. cpp*

1. Dans *MyProjview. cpp*, apportez les modifications suivantes :

   - Dans `CMyProjView::OnPreparePrinting` , remplacez le contenu de la fonction par le code suivant :

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting`fournit la prise en charge de l’impression. Ce code remplace `DoPreparePrinting` , qui est la préparation d’impression par défaut.

   La relation contenant-contenu de document actif fournit un schéma d’impression amélioré :

   - Vous pouvez d’abord appeler le document actif par le biais de son `IPrint` interface et lui demander de s’imprimer lui-même. Cela diffère de la relation contenant-contenu OLE précédente, dans laquelle le conteneur devait restituer une image de l’élément contenu sur l' `CDC` objet Printer.

   - En cas d’échec, indique à l’élément contenu de s’imprimer par le biais de son `IOleCommandTarget` interface

   - En cas d’échec, effectuez votre propre rendu de l’élément.

   Les fonctions membres statiques `COleDocObjectItem::OnPrint` et `COleDocObjectItem::OnPreparePrinting` , telles qu’elles sont implémentées dans le code précédent, gèrent ce schéma d’impression amélioré.

1. Ajoutez les implémentations de votre choix et générez l’application.

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](active-document-containment.md)
