---
description: 'En savoir plus sur : classe CCmdUI'
title: CCmdUI, classe
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 5fae6d2dda948fd3720a29d502d7f050e388bceb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216130"
---
# <a name="the-ccmdui-class"></a>CCmdUI, classe

Lorsqu’il achemine une commande de mise à jour vers son gestionnaire, le Framework passe le gestionnaire à un pointeur vers un `CCmdUI` objet (ou à un objet d’une `CCmdUI` classe dérivée de). Cet objet représente l’élément de menu ou le bouton de barre d’outils ou tout autre objet d’interface utilisateur qui a généré la commande. Le gestionnaire de mise à jour appelle les fonctions membres de la `CCmdUI` structure par le biais du pointeur pour mettre à jour l’objet d’interface utilisateur. Par exemple, voici un gestionnaire de mise à jour pour l’élément de menu effacer tout :

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ce gestionnaire appelle la `Enable` fonction membre d’un objet ayant accès à l’élément de menu. `Enable` rend l’élément disponible.

## <a name="see-also"></a>Voir aussi

[Comment : mettre à jour des objets User-Interface](../mfc/how-to-update-user-interface-objects.md)
