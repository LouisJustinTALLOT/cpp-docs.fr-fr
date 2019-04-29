---
title: CCmdUI, classe
ms.date: 11/04/2016
f1_keywords:
- CCmdUI
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 8e0af0703924d6fae626d3753b8523efe0c56652
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306299"
---
# <a name="the-ccmdui-class"></a>CCmdUI, classe

Lorsqu’il achemine une commande de mise à jour vers son gestionnaire, l’infrastructure transmet un pointeur vers le Gestionnaire d’un `CCmdUI` objet (ou à un objet d’un `CCmdUI`-classe dérivée). Cet objet représente le bouton de barre d’outils ou élément de menu ou un autre objet d’interface utilisateur qui a généré la commande. Le Gestionnaire de mise à jour appelle les fonctions de membres le `CCmdUI` structure via le pointeur pour mettre à jour de l’objet d’interface utilisateur. Par exemple, Voici un gestionnaire de mise à jour pour l’effacer tout élément de menu :

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ce gestionnaire appelle le `Enable` fonction membre d’un objet avec un accès à l’élément de menu. `Enable` rend l’élément disponible pour utilisation.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour Mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)
