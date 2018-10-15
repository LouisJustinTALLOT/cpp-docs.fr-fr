---
title: Classes partagées par MFC et ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50295c9d296449e36ed4a305b568d2e0aaed10a3
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327906"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Classes partagées par MFC et ATL

Le tableau suivant répertorie les classes partagées entre MFC et ATL.

|Classe|Description|Fichier d'en-tête|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Fournit des méthodes pour gérer les valeurs de date et heure associées à un fichier.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Fournit des méthodes pour la gestion relatif valeurs de date et heure associées à un fichier.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Représente un objet de chaîne avec une mémoire tampon de caractères fixe.|CStringT.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Fournit une prise en charge améliorée des images bitmap, y compris la possibilité de charger et enregistrer des images dans les formats JPEG, GIF, BMP et PNG Portable Network Graphics ().|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsule le type de données DATE utilisé dans OLE automation.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Représente une heure relative, un intervalle de temps.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Une classe similaire à la Windows [POINT](../../mfc/reference/point-structure.md) structure qui comprend également des fonctions de membre pour manipuler `CPoint` et `POINT` structures.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Une classe similaire à un Windows [RECT](../../mfc/reference/rect-structure.md) structure qui comprend également des fonctions de membre pour manipuler `CRect` objets et Windows `RECT` structures.|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Représente un `CSimpleStringT` objet.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Une classe similaire à la structure de taille de Windows, qui implémente une coordonnée relative ou une position.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Fournit le nettoyage automatique des ressources des `GetBuffer` et `ReleaseBuffer` appelle sur un existant `CStringT` objet.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Représente les données d’un objet string.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Représente un `CStringT` objet.|CStringT.h (MFC dépendant) atlstr.h (indépendante de MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Représente une date et l’heure absolue.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Un laps de temps, ce qui est stocké en interne en tant que le nombre de secondes dans l’intervalle de temps.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Représente l’interface pour un `CStringT` Gestionnaire de mémoire.|atlsimpstr.h|

## <a name="see-also"></a>Voir aussi

[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

