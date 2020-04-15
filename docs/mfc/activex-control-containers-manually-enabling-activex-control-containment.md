---
title: "Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX"
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322064"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Conteneurs de contrôles ActiveX : activation manuelle d'une relation contenant-contenu de contrôle ActiveX

Si vous n’avez pas permis le support de contrôle ActiveX lorsque vous avez utilisé l’assistant d’application MFC pour générer votre application, vous devrez ajouter ce support manuellement. Cet article décrit le processus d’ajout manuel du confinement de contrôle ActiveX à une application de conteneurs OLE existante. Si vous savez à l’avance que vous voulez une prise de contrôle ActiveX dans votre conteneur OLE, consultez [l’article Créer un conteneur de contrôle MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

> [!NOTE]
> Cet article utilise un projet de conteneurs de contrôle ActiveX basé sur le dialogue nommé Container et un contrôle intégré nommé Circ comme exemples dans les procédures et le code.

Pour prendre en charge les contrôles ActiveX, vous devez ajouter une ligne de code à deux des fichiers de votre projet.

- Modifiez la fonction `InitInstance` de votre dialogue principal (dans CONTAINER. CPP) par le MFC Application Wizard faisant un appel à [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), comme dans l’exemple suivant:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Ajoutez ce qui suit au STDAFX de votre projet. Fichier d’en-tête H:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Une fois que vous avez terminé ces étapes, reconstruisez votre projet en cliquant sur **Build** sur le menu **Build.**

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôle ActiveX](../mfc/activex-control-containers.md)
