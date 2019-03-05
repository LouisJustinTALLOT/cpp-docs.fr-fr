---
title: Dériver des contrôles d'un contrôle standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: 5abdcc87dba937938ffa3643d19ff69431f62af4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300373"
---
# <a name="deriving-controls-from-a-standard-control"></a>Dériver des contrôles d'un contrôle standard

Comme avec n’importe quel [CWnd](../mfc/reference/cwnd-class.md)-classe dérivée, vous pouvez modifier le comportement d’un contrôle en dérivant une classe nouvelle à partir d’une classe de contrôle existante.

### <a name="to-create-a-derived-control-class"></a>Pour créer une classe dérivée de contrôle

1. Dérivez votre classe à partir d’une classe de contrôle existante et éventuellement remplacer le `Create` membre de fonction pour qu’elle fournisse les arguments nécessaires à la classe de base `Create` (fonction).

1. Fournir des fonctions membres de gestionnaire de messages et les entrées de table des messages pour modifier le comportement du contrôle en réponse à des messages Windows spécifiques. Consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

1. Offrir de nouvelles fonctions de membre pour étendre les fonctionnalités du contrôle (facultatif).

À l’aide d’un contrôle dérivé dans une boîte de dialogue nécessite un travail supplémentaire. Les types et les positions des contrôles dans une boîte de dialogue sont normalement spécifiées dans une ressource de modèle de boîte de dialogue. Si vous créez une classe dérivée de contrôle, vous ne pouvez pas le spécifier dans un modèle de boîte de dialogue dans la mesure où le compilateur de ressources ne connaît rien de votre classe dérivée.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Pour placer votre contrôle dérivé dans une boîte de dialogue

1. Incorporer un objet de la classe de contrôle dérivée dans la déclaration de votre classe de boîte de dialogue dérivée.

1. Remplacer le `OnInitDialog` fonction membre dans votre classe de boîte de dialogue pour appeler le `SubclassDlgItem` fonction membre pour le contrôle dérivé.

`SubclassDlgItem` « sous-classe dynamiquement » un contrôle créé à partir d’un modèle de boîte de dialogue. Quand un contrôle sous-classé de façon dynamique, vous raccorder à Windows, traiter des messages au sein de votre propre application, puis transmettez les messages restants à Windows. Pour plus d’informations, consultez le [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) fonction membre de classe `CWnd` dans le *référence MFC*. L’exemple suivant montre comment vous pouvez écrire une substitution de `OnInitDialog` pour appeler `SubclassDlgItem`:

[!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Étant donné que le contrôle dérivé est incorporé dans la classe de boîte de dialogue, elle sera construite lors de la construction de la boîte de dialogue et il sera détruit lorsque la boîte de dialogue est détruite. Comparez ce code à l’exemple dans [Ajout de contrôles By main](../mfc/adding-controls-by-hand.md).

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
