---
title: 'Conteneurs de contrôles ActiveX : Activation manuelle de la contenance de contrôles ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 845ad544b83f3f73c31eebd00218945c6028a622
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534974"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX
Si vous n’avez pas activé la prise en charge du contrôle ActiveX lorsque vous avez utilisé l’Assistant Application MFC pour générer votre application, vous devez ajouter cette prise en charge manuellement. Cet article décrit le processus d’ajout manuel de contrôles ActiveX à une application de conteneur OLE existante. Si vous connaissez à l’avance que vous souhaitez prise en charge du contrôle ActiveX dans un conteneur OLE, consultez l’article [création d’un conteneur de contrôles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).  
  
> [!NOTE]
>  Cet article utilise un boîte de dialogue ActiveX conteneur projet de contrôle nommé conteneur et un contrôle incorporé nommé CERC comme exemples dans les procédures et le code.  
  
 Pour prendre en charge les contrôles ActiveX, vous devez ajouter une ligne de code à deux des fichiers de votre projet.  
  
-   Modifier votre boîte de dialogue principale `InitInstance` (fonction) (figurant dans le conteneur. (CPP) par l’Assistant Application MFC qu’un appel à [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), comme dans l’exemple suivant :  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Ajoutez le code suivant à votre fichier STDAFX. Fichier d’en-tête H :  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Une fois ces étapes terminées, régénérez votre projet en cliquant sur **Build** sur le **Build** menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

