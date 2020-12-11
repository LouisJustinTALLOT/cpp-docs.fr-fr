---
description: 'En savoir plus sur : utilisation d’une fenêtre'
title: Utilisation d’une fenêtre (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: fb9f1e03a27ad8b637da30eacbd100daf920cdb4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157278"
---
# <a name="using-a-window"></a>Utilisation d’une fenêtre

La classe [CWindow](../atl/reference/cwindow-class.md) vous permet d’utiliser une fenêtre. Une fois que vous avez attaché une fenêtre à un `CWindow` objet, vous pouvez appeler `CWindow` des méthodes pour manipuler la fenêtre. `CWindow` contient également un opérateur HWND pour convertir un `CWindow` objet en HWND. Vous pouvez donc passer un `CWindow` objet à toute fonction qui requiert un handle vers une fenêtre. Vous pouvez facilement mélanger `CWindow` les appels de méthode et les appels de fonction Win32, sans créer d’objets temporaires.

Étant donné que n' `CWindow` a que deux données membres (un handle de fenêtre et les dimensions par défaut), il n’impose aucune surcharge sur votre code. De plus, la plupart des `CWindow` méthodes encapsulent simplement les fonctions API Win32 correspondantes. À l’aide de `CWindow` , le membre HWND est passé automatiquement à la fonction Win32.

En plus d’utiliser `CWindow` directement, vous pouvez également le dériver pour ajouter des données ou du code à votre classe. ATL lui-même dérive trois classes de `CWindow` : [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md)et [CContainedWindowT](../atl/using-contained-windows.md).

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
