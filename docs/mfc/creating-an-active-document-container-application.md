---
title: Création d’une Application conteneur de documents actifs | Documents Microsoft
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
ms.openlocfilehash: 880c6953addd0ec7db3abf5864010bd472d2d5a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341347"
---
# <a name="creating-an-active-document-container-application"></a>Création d'une application conteneur de documents actifs
La façon la plus simple et plus recommandée pour créer une application conteneur de document actif consiste à créer une application de conteneur EXE MFC à l’aide de l’Assistant Application MFC, puis modifiez l’application pour prendre en charge de la relation contenant-contenu de document actif.  
  
#### <a name="to-create-an-active-document-container-application"></a>Pour créer une application conteneur de documents actifs  
  
1.  À partir de la **fichier** menu, cliquez sur **projet**à partir de la **nouveau** sous-menu.  
  
2.  Dans le volet gauche, cliquez sur **Visual C++** type de projet.  
  
3.  Sélectionnez **Application MFC** dans le volet droit.  
  
4.  Nommez le projet `MyProj`, cliquez sur **OK**.  
  
5.  Sélectionnez le **prise en charge des documents composés** page.  
  
6.  Sélectionnez le **conteneur** ou **conteneur/serveur complet** option.  
  
7.  Sélectionnez le **conteneur de documents actifs** case à cocher.  
  
8.  Cliquez sur **Terminer**.  
  
9. Lorsque l’Assistant Application MFC a terminé de générer l’application, ouvrez les fichiers suivants à l’aide de l’Explorateur de solutions :  
  
    -   MyProjview.cpp  
  
10. Dans MyProjview.cpp, apportez les modifications suivantes :  
  
    -   Dans `CMyProjView::OnPreparePrinting`, remplacez le contenu de la fonction par le code suivant :  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` prend en charge l’impression. Ce code remplace `DoPreparePrinting`, qui est la préparation de l’impression par défaut.  
  
     Relation contenant-contenu de document actif fournit un schéma d’impression amélioré :  
  
    -   Vous pouvez commencer par appeler le document actif via son `IPrint` interface et lui demander d’imprimer. Cela diffère de la précédente OLE relation contenant-contenu, dans lequel le conteneur a restituer une image de l’élément de contenu sur l’imprimante `CDC` objet.  
  
    -   En cas d’échec, indiquer à l’élément de contenu s’imprime via son `IOleCommandTarget` interface  
  
    -   En cas d’échec, vérifiez votre propre rendu de l’élément.  
  
     Les fonctions membres statiques `COleDocObjectItem::OnPrint` et `COleDocObjectItem::OnPreparePrinting`, tel qu’implémenté dans le code précédent, gèrent ce schéma d’impression amélioré.  
  
11. Ajouter votre propre implémentation et générez l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)

