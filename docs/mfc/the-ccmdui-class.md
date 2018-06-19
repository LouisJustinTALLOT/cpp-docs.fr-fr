---
title: CCmdUI, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dde8c31620f64e6201c59b7031c789caa16c4902
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379806"
---
# <a name="the-ccmdui-class"></a>CCmdUI, classe
Quand elle achemine une commande de mise à jour vers son gestionnaire, l’infrastructure transmet un pointeur vers le Gestionnaire d’un `CCmdUI` objet (ou un objet d’un `CCmdUI`-classe dérivée). Cet objet représente le bouton de barre d’outils ou élément de menu ou un autre objet d’interface utilisateur qui a généré la commande. Le Gestionnaire de mise à jour appelle les fonctions de membres le `CCmdUI` structure via le pointeur de la mise à jour de l’objet d’interface utilisateur. Voici, par exemple, un gestionnaire de mise à jour pour l’élément de menu Effacer tout :  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Ce gestionnaire appelle la **activer** fonction membre d’un objet avec un accès à l’élément de menu. **Activer** permet d’utiliser l’élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

