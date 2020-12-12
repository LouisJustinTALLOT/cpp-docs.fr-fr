---
description: 'En savoir plus sur : classes partagées par MFC et ATL'
title: Classes partagées par MFC et ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: df196f92b7b16742545a7d82320ef4fe8da77fe2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166783"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Classes partagées par MFC et ATL

Le tableau suivant répertorie les classes partagées entre MFC et ATL.

|Classe|Description|Fichier d’en-tête|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Fournit des méthodes pour gérer les valeurs de date et d’heure associées à un fichier.|atltime. h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Fournit des méthodes pour gérer les valeurs de date et d’heure relatives associées à un fichier.|atltime. h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Représente un objet String avec une mémoire tampon de caractères fixe.|CStringT. h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Offre une prise en charge améliorée des bitmaps, notamment la possibilité de charger et d’enregistrer des images au format JPEG, GIF, BMP et PNG (Portable Network Graphics).|atlimage. h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsule le type de données DATE utilisé dans OLE Automation.|atlcomtime. h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Représente une heure relative, un intervalle de temps.|atlcomtime. h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Classe similaire à la structure de [points](/windows/win32/api/windef/ns-windef-point) Windows qui comprend également des fonctions membres pour manipuler `CPoint` les `POINT` structures et.|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Classe similaire à une structure Windows [Rect](/windows/win32/api/windef/ns-windef-rect) qui comprend également des fonctions membres pour manipuler `CRect` des objets et des `RECT` structures Windows.|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Représente un objet `CSimpleStringT`.|atlsimpstr. h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Classe similaire à la structure de [taille](/windows/win32/api/windef/ns-windef-size) Windows, qui implémente une coordonnée ou une position relative.|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Fournit un nettoyage automatique des ressources pour `GetBuffer` et `ReleaseBuffer` appelle sur un `CStringT` objet existant.|atlsimpstr. h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Représente les données d’un objet String.|atlsimpstr. h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Représente un objet `CStringT`.|CStringT. h (dépendant de MFC) atlstr. h (indépendant MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Représente une date et une heure absolues.|atltime. h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Durée, qui est stockée en interne comme nombre de secondes dans l’intervalle de temps.|atltime. h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Représente l’interface pour un `CStringT` Gestionnaire de mémoire.|atlsimpstr. h|

## <a name="see-also"></a>Voir aussi

[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
