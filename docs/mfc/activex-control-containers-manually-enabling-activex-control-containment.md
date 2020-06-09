---
title: "Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX"
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625113"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX

Si vous n’avez pas activé la prise en charge du contrôle ActiveX lorsque vous avez utilisé l’Assistant Application MFC pour générer votre application, vous devez ajouter cette prise en charge manuellement. Cet article décrit le processus d’ajout manuel d’une relation contenant-contenu de contrôle ActiveX à une application conteneur OLE existante. Si vous savez à l’avance que vous souhaitez la prise en charge des contrôles ActiveX dans votre conteneur OLE, consultez l’article [création d’un conteneur de contrôles ActiveX MFC](reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

> [!NOTE]
> Cet article utilise un projet de conteneur de contrôles ActiveX basé sur des boîtes de dialogue nommé conteneur et un contrôle incorporé nommé CIRC comme exemples dans les procédures et le code.

Pour prendre en charge les contrôles ActiveX, vous devez ajouter une ligne de code à deux des fichiers de votre projet.

- Modifiez la fonction de la boîte de dialogue principale `InitInstance` (située dans le conteneur. CPP) par l’Assistant Application MFC, en effectuant un appel à [AfxEnableControlContainer (](reference/ole-initialization.md#afxenablecontrolcontainer), comme dans l’exemple suivant :

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Ajoutez le code suivant au STDAFX de votre projet. Fichier d’en-tête H :

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Une fois ces étapes terminées, régénérez votre projet en cliquant sur **générer** dans le menu **générer** .

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](activex-control-containers.md)
