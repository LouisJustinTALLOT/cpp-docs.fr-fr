---
title: Dériver des contrôles d’un contrôle Standard | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ae7fb09e1f453b6d7bc82a7fb038567809f872
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932245"
---
# <a name="deriving-controls-from-a-standard-control"></a>Dériver des contrôles d'un contrôle standard
Comme avec n’importe quelle [CWnd](../mfc/reference/cwnd-class.md)-classe dérivée, vous pouvez modifier le comportement d’un contrôle en dérivant une classe nouvelle à partir d’une classe de contrôle existante.  
  
### <a name="to-create-a-derived-control-class"></a>Pour créer une classe dérivée de contrôle  
  
1.  Dérivez votre classe à partir d’une classe de contrôle existante et substituez éventuellement la `Create` pour qu’elle fournisse les arguments nécessaires à la classe de base de fonction membre `Create` (fonction).  
  
2.  Fournir des fonctions membres de gestionnaire de messages et les entrées de table des messages pour modifier le comportement du contrôle en réponse à des messages Windows spécifiques. Consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).  
  
3.  Fournir de nouvelles fonctions membres pour étendre les fonctionnalités du contrôle (facultatif).  
  
 À l’aide d’un contrôle dérivé dans une boîte de dialogue nécessite un travail supplémentaire. Les types et les positions des contrôles dans une boîte de dialogue sont normalement spécifiées dans une ressource de modèle de boîte de dialogue. Si vous créez une classe dérivée de contrôle, vous ne pouvez pas le spécifier dans un modèle de boîte de dialogue, car le compilateur de ressources ne sait rien sur votre classe dérivée.  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Pour placer votre contrôle dérivé dans une boîte de dialogue  
  
1.  Incorporez un objet de la classe de contrôle dérivée dans la déclaration de votre classe dérivée de boîte de dialogue.  
  
2.  Remplacer la `OnInitDialog` fonction membre dans votre classe de boîte de dialogue pour appeler le `SubclassDlgItem` fonction membre pour le contrôle dérivé.  
  
 `SubclassDlgItem` « sous-classe dynamiquement » un contrôle créé à partir d’un modèle de boîte de dialogue. Lorsqu’un contrôle sous-classé de façon dynamique, vous raccordez à Windows, traiter des messages au sein de votre propre application, puis passez les messages restants à Windows. Pour plus d’informations, consultez la [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) fonction membre de classe `CWnd` dans les *référence MFC*. L’exemple suivant montre comment vous pouvez écrire une substitution de `OnInitDialog` pour appeler `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 Étant donné que le contrôle dérivé est incorporé dans la classe de boîte de dialogue, il est construit lors de la construction de la boîte de dialogue et il sera détruit lors de la destruction de la boîte de dialogue. Comparez ce code à l’exemple dans [Ajout de contrôles à main](../mfc/adding-controls-by-hand.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation de contrôles](../mfc/making-and-using-controls.md)   
 [Contrôles](../mfc/controls-mfc.md)

