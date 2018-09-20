---
title: Classes de Type de données simple | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca6eb22ea596b39f417813ad5072dd1a72e270e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418773"
---
# <a name="simple-data-type-classes"></a>Classes de type de données simple

Les classes suivantes encapsulent dessin coordonnées, les chaînes de caractères et les temps et utiliser des informations de date, ce qui permet de pratique de syntaxe C++. Ces objets sont largement utilisées en tant que paramètres aux fonctions membres de classes de Windows dans la bibliothèque de classes. Étant donné que `CPoint`, `CSize`, et `CRect` correspondent à la **POINT**, **taille**, et **RECT** structures, respectivement, dans le Kit de développement Windows Vous pouvez utiliser des objets de ces classes C++ partout où vous pouvez utiliser ces structures de langage C. Les classes fournissent des interfaces utiles via leurs fonctions membres. `CStringT` fournit les chaînes de caractères dynamique très flexible. `CTime`, `COleDateTime`, `CTimeSpan`, et `COleTimeSpan` représentent les valeurs de date et heure. Pour plus d’informations sur ces classes, consultez l’article [Date et heure](../atl-mfc-shared/date-and-time.md).

Les classes qui commencent par «`COle`» sont encapsulations des types de données fournis par OLE. Ces types de données peuvent être utilisés dans les programmes de Windows, quel que soit le si les autres fonctionnalités OLE sont utilisées.

[CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Contient des chaînes de caractères.

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Contient les valeurs de date et l’heure absolues.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper pour le type d’automation OLE **DATE**. Représente les valeurs de date et d’heure.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Contient des valeurs de date et heure relatives.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Contient relatif `COleDateTime` valeurs, telles que la différence entre deux `COleDateTime` valeurs.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contient les paires de coordonnées (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contient la distance positions relatives, valeurs ou associés.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contient les coordonnées de zones rectangulaires.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Fournit les fonctionnalités de la liste d’images Windows. Listes d’images sont utilisées avec les contrôles de liste et contrôles d’arborescence. Ils peuvent également être utilisés pour stocker et archiver un ensemble de bitmaps de même taille.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper pour le type d’automation OLE **VARIANT**. Données dans **VARIANT**s peuvent être stockées dans de nombreux formats.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper pour le type d’automation OLE **devise**, un type arithmétique à virgule fixe, avec 15 chiffres avant la virgule décimale et 4 chiffres après.

> [!NOTE]
>  `CRect`, `CSize`, et `CPoint` sont utilisables dans les applications ATL ou MFC. En outre, `CStringT` fournit un indépendants des MFC `CString`-comme classe. Pour plus d’informations sur les classes d’utilitaire partagé, consultez [Classes partagées](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

