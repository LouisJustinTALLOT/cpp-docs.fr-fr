---
title: CCmdUI, classe
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447143"
---
# <a name="the-ccmdui-class"></a>CCmdUI, classe

Lorsqu’il achemine une commande de mise à jour vers son gestionnaire, le Framework passe au gestionnaire un pointeur vers un objet `CCmdUI` (ou vers un objet d’une classe dérivée de `CCmdUI`). Cet objet représente l’élément de menu ou le bouton de barre d’outils ou tout autre objet d’interface utilisateur qui a généré la commande. Le gestionnaire de mise à jour appelle les fonctions membres de la structure `CCmdUI` via le pointeur pour mettre à jour l’objet interface utilisateur. Par exemple, voici un gestionnaire de mise à jour pour l’élément de menu effacer tout :

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ce gestionnaire appelle la fonction membre `Enable` d’un objet ayant accès à l’élément de menu. `Enable` rend l’élément disponible.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)
