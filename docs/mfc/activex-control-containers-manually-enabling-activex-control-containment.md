---
title: 'Conteneurs de contrôles ActiveX : Activation manuelle de la relation contenant-contenu de contrôle ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fde0ee4dc740826c9efdf7b86cd2f021699f8820
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339889"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX
Si vous n’avez pas activé la prise en charge du contrôle ActiveX lorsque vous avez utilisé l’Assistant Application MFC pour générer votre application, vous devez ajouter cette prise en charge manuellement. Cet article décrit le processus d’ajout manuel de contrôles ActiveX à une application de conteneur OLE existante. Si vous connaissez à l’avance que vous souhaitez prise en charge du contrôle ActiveX dans un conteneur OLE, consultez l’article [création d’un conteneur de contrôles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
> [!NOTE]
>  Cet article utilise un basée sur la boîte de dialogue conteneur projet de contrôle ActiveX nommé conteneur et un contrôle incorporé (nommé Circ) comme exemples dans les procédures et le code.  
  
 Pour prendre en charge les contrôles ActiveX, vous devez ajouter une ligne de code à deux des fichiers de votre projet.  
  
-   Modifier votre boîte de dialogue principale `InitInstance` (fonction) (figurant dans le conteneur. CPP) par l’Assistant Application MFC qui effectue un appel à [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), comme dans l’exemple suivant :  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Ajoutez le code suivant à votre fichier STDAFX. Fichier d’en-tête H :  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Une fois ces étapes terminées, régénérez votre projet en cliquant sur **générer** sur la **générer** menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

