---
title: Classes partagées par MFC et ATL | Documents Microsoft
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
ms.openlocfilehash: ea651297503210a78f3ee189c57e37bcc3e99c6a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356972"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Classes partagées par MFC et ATL
Le tableau suivant répertorie les classes partagées entre MFC et ATL.  
  
|Classe|Description|Fichier d'en-tête|  
|-----------|-----------------|-----------------|  
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Fournit des méthodes pour gérer les valeurs de date et l’heure associées à un fichier.|atltime.h|  
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Fournit des méthodes pour la gestion des dates relatives et associés à un fichier de valeurs d’heure.|atltime.h|  
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Représente un objet string avec une mémoire tampon de caractères fixe.|CStringT.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Fournit une prise en charge améliorée des images bitmap, y compris la possibilité de charger et enregistrer des images dans les formats JPEG, GIF, BMP et PNG Portable Network Graphics ().|atlimage.h|  
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Encapsule le **DATE** type de données utilisé dans OLE automation.|atlcomtime.h|  
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Représente une heure relative, un intervalle de temps.|atlcomtime.h|  
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Une classe similaire aux fenêtres [POINT](../../mfc/reference/point-structure1.md) structure comprend également des fonctions de membre pour manipuler `CPoint` et **POINT** structures.|atltypes.h|  
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Une classe semblable à un Windows [RECT](../../mfc/reference/rect-structure1.md) structure comprend également des fonctions de membre pour manipuler `CRect` Windows et les objets `RECT` structures.|atltypes.h|  
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Représente un `CSimpleStringT` objet.|atlsimpstr.h|  
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Une classe est similaire à la structure de la taille de Windows, qui implémente une coordonnée relative ou une position.|atltypes.h|  
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Fournit le nettoyage automatique des ressources des `GetBuffer` et `ReleaseBuffer` appelle un existant `CStringT` objet.|atlsimpstr.h|  
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Représente les données d’un objet string.|atlsimpstr.h|  
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Représente un `CStringT` objet.|CStringT.h (en fonction de MFC) atlstr.h (indépendante de MFC)|  
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|Représente une date et l’heure absolue.|atltime.h|  
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Un intervalle de temps, ce qui est stocké en interne en tant que le nombre de secondes dans l’intervalle de temps.|atltime.h|  
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Représente l’interface pour un `CStringT` Gestionnaire de mémoire.|atlsimpstr.h|  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


