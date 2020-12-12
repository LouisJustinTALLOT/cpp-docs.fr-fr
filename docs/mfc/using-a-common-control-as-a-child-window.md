---
description: 'En savoir plus sur : utilisation d’un contrôle commun en tant que fenêtre enfant'
title: Utilisation d'un contrôle commun en tant que fenêtre enfant
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 5a5fda2cbf8d0bf16ccb17f2766b31d24e5c0c67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263554"
---
# <a name="using-a-common-control-as-a-child-window"></a>Utilisation d'un contrôle commun en tant que fenêtre enfant

Les contrôles communs Windows peuvent être utilisés en tant que fenêtre enfant d’une autre fenêtre. La procédure suivante décrit comment créer dynamiquement un contrôle commun, puis l’utiliser.

### <a name="to-use-a-common-control-as-a-child-window"></a>Pour utiliser un contrôle commun en tant que fenêtre enfant

1. Définissez le contrôle dans la classe ou le gestionnaire associé.

1. Utilisez la substitution du contrôle de la méthode [CWnd :: Create](../mfc/reference/cwnd-class.md#create) pour créer le contrôle Windows.

1. Une fois que le contrôle a été créé (aussi tôt que le `OnCreate` Gestionnaire si vous sous-classez le contrôle), vous pouvez manipuler le contrôle à l’aide de ses fonctions membres. Pour plus d’informations sur les méthodes, consultez les descriptions des contrôles individuels dans [contrôles](../mfc/controls-mfc.md) .

1. Lorsque vous avez terminé avec le contrôle, utilisez [CWnd ::D estroywindow](../mfc/reference/cwnd-class.md#destroywindow) pour détruire le contrôle.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
