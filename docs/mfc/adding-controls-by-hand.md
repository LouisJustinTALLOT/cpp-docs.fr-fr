---
title: Ajout de contrôles à la main | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39f2d7803630aaaef6e803e90bf332c74937a71
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930613"
---
# <a name="adding-controls-by-hand"></a>Ajout de contrôles manuellement
Vous pouvez soit [ajouter des contrôles à une boîte de dialogue avec l’éditeur de boîte de dialogue](../mfc/using-the-dialog-editor-to-add-controls.md) ou les ajouter vous-même, avec le code.  
  
 Pour créer un objet de contrôle vous-même, vous incorporez généralement l’objet de contrôle C++ dans une boîte de dialogue C++ ou un objet fenêtre frame. Comme de nombreux autres objets dans le framework, les contrôles requièrent construction en deux étapes. Vous devez appeler du contrôle **créer** fonction membre dans le cadre de la création de la fenêtre boîte ou le cadre de la boîte de dialogue parent. Pour les boîtes de dialogue, cela s’effectue habituellement dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)et pour les fenêtres frames, dans [OnCreate](../mfc/reference/cwnd-class.md#oncreate).  
  
 L’exemple suivant montre comment vous pouvez déclarer un `CEdit` de l’objet dans la déclaration de classe d’une classe dérivée de boîte de dialogue, puis appelez le `Create` fonction membre dans `OnInitDialog`. Étant donné que la `CEdit` objet est déclaré en tant qu’objet incorporé, il est construit automatiquement lorsque l’objet de la boîte de dialogue est construit, mais il doit toujours être initialisé avec son propre `Create` fonction membre.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 Les éléments suivants `OnInitDialog` fonction définit un rectangle, puis appelle `Create` pour créer le contrôle d’édition Windows et l’attacher à la sans être initialisé `CEdit` objet.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 Après avoir créé l’objet à modifier, vous pouvez également définir le focus d’entrée au contrôle en appelant le `SetFocus` fonction membre. Enfin, de retour de 0 à partir de `OnInitDialog` pour montrer que vous définissez le focus. Si vous retournez une valeur différente de zéro, le Gestionnaire de boîte de dialogue définit le focus sur le premier élément de contrôle dans la liste d’éléments de boîte de dialogue. Dans la plupart des cas, vous souhaiterez ajouter des contrôles à vos boîtes de dialogue avec l’éditeur de boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation de contrôles](../mfc/making-and-using-controls.md)   
 [Contrôles](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

