---
title: Inscrire des Classes de fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WndProc
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca6b7753ad3fd4024cadb899652336fa2f860b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403095"
---
# <a name="registering-window-classes"></a>Inscription de classes de fenêtre

Fenêtre « classes » dans la programmation traditionnelle pour Windows définissent les caractéristiques d’une « classe » (pas une classe C++) à partir duquel un nombre quelconque de windows peut être créé. Ce type de classe est un modèle ou un modèle pour la création de fenêtres.

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Inscription de classe de fenêtre dans les programmes traditionnels pour Windows

Dans un programme traditionnel pour Windows, sans MFC, vous traitez tous les messages à une fenêtre dans sa procédure de fenêtre « » ou «`WndProc`. » Un `WndProc` est associé à une fenêtre au moyen d’un processus de « inscription de classe de fenêtre ». La fenêtre principale est enregistrée dans le `WinMain` (fonction), mais autres classes de windows peuvent être enregistrées n’importe où dans l’application. L’enregistrement dépend d’une structure qui contient un pointeur vers le `WndProc` fonction ainsi que des spécifications pour le curseur, le pinceau d’arrière-plan et ainsi de suite. La structure est passée en tant que paramètre, ainsi que le nom de chaîne de la classe, dans un appel antérieur à la `RegisterClass` (fonction). Par conséquent, une classe d’enregistrement peut être partagée par plusieurs fenêtres.

## <a name="window-class-registration-in-mfc-programs"></a>Inscription de classe de fenêtre dans les programmes MFC

En revanche, la plupart des activités de l’inscription de classe de fenêtre est effectuée automatiquement dans un programme de framework MFC. Si vous utilisez MFC, vous dérivez généralement une classe de fenêtre C++ à partir d’une classe existante à l’aide de la syntaxe C++ normale pour l’héritage de classes. L’infrastructure utilise toujours traditionnel « classes d’enregistrement » et il fournit plusieurs classes standard enregistrées pour vous si nécessaire. Vous pouvez inscrire des classes d’enregistrement supplémentaires en appelant le [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) fonction globale, puis en passant la classe inscrite pour le `Create` fonction membre de `CWnd`. Comme décrit ici, le traditionnel « classe de l’inscription » dans Windows ne doit ne pas être confondue avec une classe C++.

Pour plus d’informations, consultez [Technical Note 1](../mfc/tn001-window-class-registration.md).

## <a name="see-also"></a>Voir aussi

[Création de fenêtres](../mfc/creating-windows.md)

