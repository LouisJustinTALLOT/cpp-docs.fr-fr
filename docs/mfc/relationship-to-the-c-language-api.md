---
title: Relation avec l'API du langage C
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: fe83af2d05af8e3b9da8d0c62f6974b0a5410bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308979"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C

Cette caractéristique unique qui différencie des autres bibliothèques de classes pour Windows dans la bibliothèque Microsoft Foundation classes (MFC) est le mappage très proche à l’API Windows écrits en langage C. En outre, vous pouvez généralement mélanger les appels à la bibliothèque de classes de librement avec des appels directs à l’API Windows. Cet accès direct n’implique pas, toutefois, que les classes sont un remplacement complet pour cette API. Les développeurs doivent se néanmoins occasionnellement les appels directs à certaines fonctions de Windows, tel que [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) et [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics), par exemple. Une fonction de Windows est encapsulée par une fonction membre de classe uniquement s’il existe un avantage NET à cet effet.

Étant donné que vous devez parfois effectuer des appels de fonction Windows natives, vous devez avoir accès à la documentation de l’API de Windows en langage C. Cette documentation est incluse dans Microsoft Visual C++.

> [!NOTE]
>  Pour une vue d’ensemble du fonctionne de l’infrastructure de la bibliothèque MFC, consultez [utilisation des Classes pour écrire des Applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception des classes](../mfc/general-class-design-philosophy.md)
