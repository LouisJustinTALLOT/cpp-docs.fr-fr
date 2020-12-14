---
description: 'En savoir plus sur : classes de type de données simple'
title: Classes de type de données simple
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: 4ce6e799cc30dddde18a50802e01c872c54d1d3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216962"
---
# <a name="simple-data-type-classes"></a>Classes de type de données simple

Les classes suivantes encapsulent les coordonnées de dessin, les chaînes de caractères et les informations d’heure et de date, ce qui permet une utilisation pratique de la syntaxe C++. Ces objets sont utilisés de façon très large comme paramètres des fonctions membres des classes Windows dans la bibliothèque de classes. Étant donné que `CPoint` , `CSize` et `CRect` correspondent respectivement aux structures **point**, **SIZE** et **Rect** , dans le SDK Windows, vous pouvez utiliser les objets de ces classes C++ partout où vous pouvez utiliser ces structures de langage C. Les classes fournissent des interfaces utiles via leurs fonctions membres. `CStringT` fournit des chaînes de caractères dynamiques très flexibles. `CTime`, `COleDateTime` , `CTimeSpan` et `COleTimeSpan` représentent les valeurs d’heure et de date. Pour plus d’informations sur ces classes, consultez l’article [date et heure](../atl-mfc-shared/date-and-time.md).

Les classes qui commencent par « `COle` » sont des encapsulations des types de données fournis par OLE. Ces types de données peuvent être utilisés dans les programmes Windows, que d’autres fonctionnalités OLE soient utilisées ou non.

[CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Contient des chaînes de caractères.

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Contient des valeurs de date et d’heure absolues.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper pour la **Date** de type OLE Automation. Représente les valeurs de date et d’heure.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Contient les valeurs de date et d’heure relatives.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Contient des `COleDateTime` valeurs relatives, telles que la différence entre deux `COleDateTime` valeurs.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contient des paires de coordonnées (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contient la distance, les positions relatives ou les valeurs jumelées.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contient les coordonnées des zones rectangulaires.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Fournit les fonctionnalités de la liste d’images Windows. Les listes d’images sont utilisées avec les contrôles de liste et les contrôles d’arborescence. Ils peuvent également être utilisés pour stocker et archiver un ensemble de bitmaps de même taille.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper pour la **variante** de type OLE Automation. Les données de la **variante** peuvent être stockées dans de nombreux formats.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper pour la **devise** de type OLE Automation, un type arithmétique à virgule fixe, avec 15 chiffres avant la virgule décimale et 4 chiffres après.

> [!NOTE]
> `CRect`, `CSize` et `CPoint` sont utilisables dans les applications ATL ou MFC. En outre, `CStringT` fournit une classe de type indépendant des MFC `CString` . Pour plus d’informations sur les classes d’utilitaire partagées, consultez [classes partagées](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../mfc/class-library-overview.md)
