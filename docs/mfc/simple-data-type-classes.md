---
title: Classes de type de données simple
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365399"
---
# <a name="simple-data-type-classes"></a>Classes de type de données simple

Les classes suivantes résument les coordonnées de dessin, les chaînes de caractères et les informations sur l’heure et la date, ce qui permet une utilisation pratique de la syntaxe CMD. Ces objets sont largement utilisés comme paramètres pour les fonctions membres des classes Windows dans la bibliothèque de classe. Parce `CPoint` `CSize`que, `CRect` , et correspondent aux structures **POINT**, **SIZE**, et **RECT,** respectivement, dans le SDK Windows, vous pouvez utiliser des objets de ces classes C 'partout où vous pouvez utiliser ces structures en langue C. Les classes fournissent des interfaces utiles à travers leurs fonctions de membre. `CStringT`fournit des chaînes de caractère dynamiques très flexibles. `CTime`, `COleDateTime` `CTimeSpan`, `COleTimeSpan` et représentent les valeurs d’heure et de date. Pour plus d’informations sur ces classes, voir l’article [Date et Temps](../atl-mfc-shared/date-and-time.md).

Les classes qui`COle`commencent par " sont des encapsulations des types de données fournies par OLE. Ces types de données peuvent être utilisés dans les programmes Windows, peu importe si d’autres fonctionnalités OLE sont utilisées.

[Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Tient des cordes de caractère.

[Ctime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Détient des valeurs absolues d’heure et de date.

[COleDateTime (en anglais)](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Emballage pour le type d’automatisation OLE **DATE**. Représente les valeurs de date et d’heure.

[CTimeSpan (en anglais seulement)](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Détient des valeurs relatives d’heure et de date.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Détient `COleDateTime` des valeurs relatives, telles `COleDateTime` que la différence entre deux valeurs.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Maintient les paires de coordonnées (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Maintient la distance, les positions relatives ou les valeurs appariées.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Détient les coordonnées des zones rectangulaires.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Fournit la fonctionnalité de la liste d’images Windows. Les listes d’images sont utilisées avec des commandes de liste et des commandes d’arbres. Ils peuvent également être utilisés pour stocker et archiver un ensemble de bitmaps de même taille.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Emballage pour le type d’automatisation OLE **VARIANT**. Les données de **VARIANT**peuvent être stockées dans de nombreux formats.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Emballage pour le type d’automatisation OLE **CURRENCY**, un type arithmétique à point fixe, avec 15 chiffres avant le point décimal et 4 chiffres après.

> [!NOTE]
> `CRect`, `CSize`et `CPoint` sont utilisables dans les applications ATL ou MFC. En outre, `CStringT` fournit une `CString`classe MFC-indépendante-comme. Pour plus d’informations sur les cours d’utilité partagée, voir [Classes partagées](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../mfc/class-library-overview.md)
