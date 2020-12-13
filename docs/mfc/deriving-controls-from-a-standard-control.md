---
description: 'En savoir plus sur : dérivation des contrôles d’un contrôle standard'
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
ms.openlocfilehash: 80e63464a7ad6d869582c66d5047a255e303a6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327870"
---
# <a name="deriving-controls-from-a-standard-control"></a>Dériver des contrôles d'un contrôle standard

Comme avec toute classe dérivée de [CWnd](reference/cwnd-class.md), vous pouvez modifier le comportement d’un contrôle en dérivant une nouvelle classe d’une classe de contrôle existante.

### <a name="to-create-a-derived-control-class"></a>Pour créer une classe de contrôle dérivée

1. Dérivez votre classe d’une classe de contrôle existante et remplacez éventuellement la `Create` fonction membre afin qu’elle fournisse les arguments nécessaires à la fonction de la classe de base `Create` .

1. Fournissez les fonctions membres du gestionnaire de messages et les entrées de la table des messages pour modifier le comportement du contrôle en réponse à des messages Windows spécifiques. Consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md).

1. Fournissez de nouvelles fonctions membres pour étendre les fonctionnalités du contrôle (facultatif).

L’utilisation d’un contrôle dérivé dans une boîte de dialogue nécessite un travail supplémentaire. Les types et les positions des contrôles dans une boîte de dialogue sont normalement spécifiés dans une ressource de modèle de boîte de dialogue. Si vous créez une classe de contrôle dérivée, vous ne pouvez pas la spécifier dans un modèle de boîte de dialogue, car le compilateur de ressources ne connaît rien de votre classe dérivée.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Pour placer votre contrôle dérivé dans une boîte de dialogue

1. Incorporez un objet de la classe de contrôle dérivée dans la déclaration de votre classe de boîte de dialogue dérivée.

1. Substituez la `OnInitDialog` fonction membre dans votre classe de boîte de dialogue pour appeler la `SubclassDlgItem` fonction membre du contrôle dérivé.

`SubclassDlgItem` « sous-classe dynamiquement » un contrôle créé à partir d’un modèle de boîte de dialogue. Lorsqu’un contrôle est sous-classé de manière dynamique, vous vous connectez à Windows, traitez certains messages dans votre propre application, puis transmettez les messages restants à Windows. Pour plus d’informations, consultez la fonction membre [SubclassDlgItem](reference/cwnd-class.md#subclassdlgitem) de `CWnd` la classe dans la *référence MFC*. L’exemple suivant montre comment vous pouvez écrire une substitution de `OnInitDialog` pour appeler `SubclassDlgItem` :

[!code-cpp[NVC_MFCControlLadenDialog#3](codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Étant donné que le contrôle dérivé est incorporé dans la classe Dialog, il sera construit lors de la construction de la boîte de dialogue et il sera détruit lors de la destruction de la boîte de dialogue. Comparez ce code à l’exemple de la façon d' [Ajouter des contrôles manuellement](adding-controls-by-hand.md).

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](making-and-using-controls.md)<br/>
[Contrôles](controls-mfc.md)
