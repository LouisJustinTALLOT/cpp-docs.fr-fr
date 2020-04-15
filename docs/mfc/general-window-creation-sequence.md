---
title: Séquence de création d'une fenêtre générale
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364274"
---
# <a name="general-window-creation-sequence"></a>Séquence de création d'une fenêtre générale

Lorsque vous créez votre propre fenêtre, comme une fenêtre pour enfants, le cadre utilise à peu près le même processus que celui décrit dans [Document/View Creation](../mfc/document-view-creation.md).

Toutes les classes de fenêtre fournies par MFC emploient [la construction en deux étapes.](../mfc/one-stage-and-two-stage-construction-of-objects.md) C’est-à-dire, lors d’une invocation du **nouvel** opérateur C, le constructeur alloue et initialise un objet C, mais ne crée pas de fenêtre Windows correspondante. Cela se fait par la suite en appelant la fonction membre [Créer](../mfc/reference/cwnd-class.md#create) de l’objet de fenêtre.

La `Create` fonction membre rend la `HWND` fenêtre Windows et la stocke dans le membre public des données de l’objet [Cmd m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create`donne une flexibilité totale sur les paramètres de création. Avant `Create`d’appeler, vous pouvez enregistrer une classe de fenêtre avec la fonction globale [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) afin de définir l’icône et les styles de classe pour le cadre.

Pour les fenêtres de cadre, vous pouvez `Create`utiliser la fonction de membre [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) au lieu de . `LoadFrame`rend la fenêtre Windows en utilisant moins de paramètres. Il obtient de nombreuses valeurs par défaut à partir des ressources, y compris la légende du cadre, icône, table d’accélérateur, et le menu.

> [!NOTE]
> Vos ressources d’icône, de table d’accélérateur et de menu doivent avoir un identifiant commun de ressource, tel que **IDR_MAINFRAME,** pour qu’elles soient chargées par LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Objets de fenêtre](../mfc/window-objects.md)

- [Enregistrement des "classes" de fenêtre](../mfc/registering-window-classes.md)

- [Détruire des objets de fenêtre](../mfc/destroying-window-objects.md)

- [Création de fenêtres d’image de document](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Création de fenêtres](../mfc/creating-windows.md)
