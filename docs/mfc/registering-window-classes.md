---
description: 'En savoir plus sur : inscription des classes de fenêtres'
title: Inscription de classes de fenêtre
ms.date: 11/04/2016
f1_keywords:
- WndProc
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
ms.openlocfilehash: e31f83b691ad12d845afca6a3a5f18d9ba64b0e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218189"
---
# <a name="registering-window-classes"></a>Inscription de classes de fenêtre

Les « classes » de la fenêtre de programmation traditionnelle pour Windows définissent les caractéristiques d’une « classe » (et non d’une classe C++) à partir de laquelle plusieurs fenêtres peuvent être créées. Ce type de classe est un modèle ou un modèle pour la création de fenêtres.

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Inscription des classes de fenêtre dans les programmes traditionnels pour Windows

Dans un programme traditionnel pour Windows, sans MFC, vous traitez tous les messages dans une fenêtre de la « procédure de fenêtre » ou de «» `WndProc` . Un `WndProc` est associé à une fenêtre au moyen d’un processus d’inscription de classe de fenêtre. La fenêtre principale est enregistrée dans la `WinMain` fonction, mais d’autres classes de fenêtres peuvent être inscrites n’importe où dans l’application. L’inscription dépend d’une structure qui contient un pointeur vers la `WndProc` fonction ainsi que des spécifications pour le curseur, le pinceau d’arrière-plan, etc. La structure est passée comme paramètre, avec le nom de chaîne de la classe, dans un appel antérieur à la `RegisterClass` fonction. Par conséquent, une classe d’inscription peut être partagée par plusieurs fenêtres.

## <a name="window-class-registration-in-mfc-programs"></a>Inscription des classes de fenêtre dans les programmes MFC

En revanche, la plupart des activités d’inscription de classe de fenêtre sont effectuées automatiquement dans un programme d’infrastructure MFC. Si vous utilisez MFC, vous dérivez généralement une classe de fenêtre C++ d’une classe de bibliothèque existante à l’aide de la syntaxe C++ normale pour l’héritage de classe. L’infrastructure utilise toujours les « classes d’inscription » traditionnelles et en fournit plusieurs, inscrites pour vous si nécessaire. Vous pouvez inscrire des classes d’inscription supplémentaires en appelant la fonction globale [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) , puis en passant la classe inscrite à la `Create` fonction membre de `CWnd` . Comme décrit ici, la « classe d’inscription » traditionnelle dans Windows ne doit pas être confondue avec une classe C++.

Pour plus d’informations, consultez [Technical Note 1](../mfc/tn001-window-class-registration.md).

## <a name="see-also"></a>Voir aussi

[Création de fenêtres](../mfc/creating-windows.md)
