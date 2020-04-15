---
title: Relation avec l'API du langage C
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 1fbd4d332f5ade1cb9415448b138ac5bc838307d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372828"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C

La seule caractéristique qui distingue la bibliothèque microsoft Foundation Class (MFC) des autres bibliothèques de classe pour Windows est la cartographie très proche de l’API Windows écrit dans la langue C. En outre, vous pouvez généralement mélanger les appels à la bibliothèque de classe librement avec des appels directs vers l’API Windows. Cet accès direct n’implique toutefois pas que les classes remplacent complètement cette API. Les développeurs doivent encore occasionnellement passer des appels directs vers certaines fonctions Windows, telles que [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) et [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), par exemple. Une fonction Windows n’est enveloppée par une fonction de membre de la classe que lorsqu’il y a un avantage évident à le faire.

Parce que vous avez parfois besoin de faire des appels de fonction Windows natif, vous devriez avoir accès à la documentation en langue C Windows API. Cette documentation est incluse avec Microsoft Visual C.

> [!NOTE]
> Pour un aperçu de la façon dont le cadre de la bibliothèque MFC fonctionne, voir [utiliser les classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception de classe](../mfc/general-class-design-philosophy.md)
