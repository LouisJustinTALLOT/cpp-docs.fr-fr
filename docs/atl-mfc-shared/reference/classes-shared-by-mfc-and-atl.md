---
title: Classes partagées par MFC et ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491458"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Classes partagées par MFC et ATL

Le tableau suivant répertorie les classes partagées entre MFC et ATL.

|Classe|Description|Fichier d’en-tête|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Fournit des méthodes pour gérer les valeurs de date et d’heure associées à un fichier.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Fournit des méthodes pour gérer les valeurs de date et d’heure relatives associées à un fichier.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Représente un objet String avec une mémoire tampon de caractères fixe.|CStringT. h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Offre une prise en charge améliorée des bitmaps, notamment la possibilité de charger et d’enregistrer des images au format JPEG, GIF, BMP et PNG (Portable Network Graphics).|atlimage. h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsule le type de données DATE utilisé dans OLE Automation.|atlcomtime. h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Représente une heure relative, un intervalle de temps.|atlcomtime. h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Classe similaire à la structure de [points](/windows/win32/api/windef/ns-windef-point) Windows qui comprend également des fonctions membres pour `CPoint` manipuler `POINT` les structures et.|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Classe similaire à une structure Windows [Rect](/windows/win32/api/windef/ns-windef-rect) qui comprend également des fonctions membres pour manipuler `CRect` des objets et `RECT` des structures Windows.|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Représente un `CSimpleStringT` objet.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Classe similaire à la structure de [taille](/windows/win32/api/windef/ns-windef-size) Windows, qui implémente une coordonnée ou une position relative.|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Fournit un nettoyage automatique des `GetBuffer` ressources `ReleaseBuffer` pour et appelle sur `CStringT` un objet existant.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Représente les données d’un objet String.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Représente un `CStringT` objet.|CStringT. h (dépendant de MFC) atlstr. h (indépendant MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Représente une date et une heure absolues.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Durée, qui est stockée en interne comme nombre de secondes dans l’intervalle de temps.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Représente l’interface pour un `CStringT` gestionnaire de mémoire.|atlsimpstr.h|

## <a name="see-also"></a>Voir aussi

[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
