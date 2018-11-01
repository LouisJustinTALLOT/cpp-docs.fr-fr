---
title: Utilisation d'un contrôle commun en tant que fenêtre enfant
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 690b48cf50e95265aaf5bdd454e2881b8f5fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655128"
---
# <a name="using-a-common-control-as-a-child-window"></a>Utilisation d'un contrôle commun en tant que fenêtre enfant

Un des contrôles communs Windows peut servir d’une fenêtre enfant de n’importe quelle autre fenêtre. La procédure suivante décrit comment créer un contrôle commun de manière dynamique et puis les utiliser.

### <a name="to-use-a-common-control-as-a-child-window"></a>Pour utiliser un contrôle commun en tant que fenêtre enfant

1. Définissez le contrôle dans la classe connexe ou le gestionnaire.

1. Utilisez la substitution de la [CWnd::Create](../mfc/reference/cwnd-class.md#create) méthode pour créer le contrôle Windows.

1. Une fois que le contrôle a été créé (en même temps que le `OnCreate` gestionnaire si vous créez une sous-classe le contrôle), vous pouvez manipuler le contrôle à l’aide de ses fonctions membres. Consultez les descriptions des contrôles individuels à [contrôles](../mfc/controls-mfc.md) pour plus d’informations sur les méthodes.

1. Lorsque vous avez terminé avec le contrôle, utilisez [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) détruire le contrôle.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

