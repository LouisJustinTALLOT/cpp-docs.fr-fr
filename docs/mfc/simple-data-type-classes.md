---
title: Classes de Type de données simple | Documents Microsoft
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
ms.openlocfilehash: 54d7f200ee35489f37256023d28bdd3260bf48ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382474"
---
# <a name="simple-data-type-classes"></a>Classes de type de données simple
Les classes suivantes encapsulent dessin coordonnées, des chaînes de caractères et heure et les informations de date, ce qui permet de pratique utiliser de syntaxe C++. Ces objets sont utilisés largement en tant que paramètres pour les fonctions membres de classes de fenêtres dans la bibliothèque de classes. Étant donné que `CPoint`, `CSize`, et `CRect` correspondent à la **POINT**, **taille**, et `RECT` structures, respectivement, dans le Kit de développement, vous pouvez utiliser des objets de ces Les classes C++, partout où vous pouvez utiliser ces structures en langage C. Les classes fournissent des interfaces utiles via les fonctions membres. `CStringT` Fournit des chaînes de caractères dynamique très flexible. `CTime`, `COleDateTime`, `CTimeSpan`, et **COleTimeSpan** représentent les valeurs de date et heure. Pour plus d’informations sur ces classes, consultez l’article [Date et heure](../atl-mfc-shared/date-and-time.md).  
  
 Les classes qui commencent par «**COle**» sont encapsulations des types de données fournis par OLE. Ces types de données peuvent être utilisés dans les programmes de Windows, même si les autres fonctionnalités OLE sont utilisées.  
  
 [CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)  
 Contient les chaînes de caractères.  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 Contient des valeurs de date et heure absolues.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Wrapper pour le type d’automatisation OLE **DATE**. Représente les valeurs de date et d’heure.  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 Contient des valeurs de date et heure relatives.  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 Sa valeur est relatif `COleDateTime` valeurs, telles que la différence entre deux `COleDateTime` valeurs.  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Contient les paires de coordonnées (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Contient la distance, les positions relatives ou les paires de valeurs.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Contient les coordonnées de zones rectangulaires.  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Fournit les fonctionnalités de la liste d’images Windows. Listes d’images sont utilisées avec les contrôles de liste et les contrôles d’arborescence. Ils peuvent également servir à stocker et archiver un ensemble de bitmaps de même taille.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Wrapper pour le type d’automatisation OLE **variante**. Données de **VARIANT**s peuvent être stockées dans de nombreux formats.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Wrapper pour le type d’automatisation OLE **devise**, un type arithmétique à virgule fixe avec 15 chiffres avant la virgule décimale et 4 chiffres après.  
  
> [!NOTE]
>  `CRect`, `CSize`, et `CPoint` sont utilisables dans les applications ATL ou MFC. En outre, `CStringT` fournit MFC indépendant `CString`-comme classe. Pour plus d’informations sur les classes d’utilitaire partagé, consultez [Classes partagées](../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

