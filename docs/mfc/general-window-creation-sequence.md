---
title: Séquence de création d'une fenêtre générale
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 949cf72910654b502ca4b57be72bedc2db63c315
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219562"
---
# <a name="general-window-creation-sequence"></a>Séquence de création d'une fenêtre générale

Lorsque vous créez une fenêtre de votre choix, comme un enfant de fenêtre, l’infrastructure utilise beaucoup le même processus que celui décrit dans [création de Document/vue](../mfc/document-view-creation.md).

Toutes les classes de fenêtre fournis par emploient des MFC [construction en deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md). Autrement dit, lors d’un appel de C++ **nouveau** opérateur, le constructeur alloue et initialise un objet C++ mais ne crée pas une fenêtre Windows correspondante. Cette opération effectuée par la suite en appelant le [créer](../mfc/reference/cwnd-class.md#create) fonction membre de l’objet window.

Le `Create` fonction membre rend la fenêtre Windows et stocke son `HWND` dans le C++ membre de données publiques de l’objet [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create` donne complètes de flexibilité sur les paramètres de création. Avant d’appeler `Create`, vous souhaiterez enregistrer une classe de fenêtre avec la fonction globale [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) afin de définir les styles d’icône et de classe pour le frame.

Pour les fenêtres frame, vous pouvez utiliser la [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) fonction membre au lieu de `Create`. `LoadFrame` rend la fenêtre de Windows en utilisant moins de paramètres. Il obtient le nombre de valeurs par défaut à partir de ressources, y compris la légende du frame, icône, table d’accélérateurs et menu.

> [!NOTE]
>  Votre icône, table d’accélérateurs et les ressources de menu doivent être un ID de ressource courants, tels que **IDR_MAINFRAME**, pour qu’ils puissent être chargés par LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Objets fenêtres](../mfc/window-objects.md)

- [Inscrire des classes de fenêtre « »](../mfc/registering-window-classes.md)

- [Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)

- [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Création de fenêtres](../mfc/creating-windows.md)
