---
description: 'En savoir plus sur : séquence de création de fenêtre générale'
title: Séquence de création d'une fenêtre générale
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 78a27114ebe3ac309ea8afdc6e04df65f1df1df8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189260"
---
# <a name="general-window-creation-sequence"></a>Séquence de création d'une fenêtre générale

Lorsque vous créez une fenêtre de votre choix, telle qu’une fenêtre enfant, l’infrastructure utilise quasiment le même processus que celui décrit dans [création de document/vue](document-view-creation.md).

Toutes les classes de fenêtres fournies par MFC utilisent la [construction en deux étapes](one-stage-and-two-stage-construction-of-objects.md). Autrement dit, au cours d’un appel de l' **`new`** opérateur c++, le constructeur alloue et initialise un objet c++, mais ne crée pas de fenêtre Windows correspondante. Cette opération est effectuée par la suite en appelant la fonction membre [Create](reference/cwnd-class.md#create) de l’objet Window.

La `Create` fonction membre crée la fenêtre Windows et stocke son `HWND` dans la [m_hWnd](reference/cwnd-class.md#m_hwnd)membre de données publiques de l’objet C++. `Create` offre une flexibilité totale sur les paramètres de création. Avant d’appeler `Create` , vous souhaiterez peut-être inscrire une classe de fenêtre avec la fonction globale [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass) afin de définir les styles de l’icône et de la classe pour le frame.

Pour les fenêtres Frame, vous pouvez utiliser la fonction membre [LoadFrame](reference/cframewnd-class.md#loadframe) à la place de `Create` . `LoadFrame` Convertit la fenêtre Windows en utilisant moins de paramètres. Elle obtient de nombreuses valeurs par défaut à partir des ressources, notamment la légende, l’icône, la table d’accélérateur et le menu du frame.

> [!NOTE]
> Votre icône, votre table d’accélérateurs et vos ressources de menu doivent avoir un ID de ressource commun, tel que **IDR_MAINFRAME**, pour qu’elles soient chargées par LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Objets de fenêtre](window-objects.md)

- [Inscription de la fenêtre « classes »](registering-window-classes.md)

- [Destruction d’objets fenêtres](destroying-window-objects.md)

- [Création de fenêtres d’image de document](creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Création de fenêtres](creating-windows.md)
