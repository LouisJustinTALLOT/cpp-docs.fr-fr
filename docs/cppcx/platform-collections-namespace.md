---
title: Platform::Collections Namespace | Documents Microsoft
ms.custom: 
ms.date: 01/25/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections
dev_langs: C++
helpviewer_keywords: Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 04514a4d4ddbba8b6c28e35e964deb153803580f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollections-namespace"></a>Platform::Collections (espace de noms)
L'espace de noms Platform::Collection contient les classes `Map`, `MapView`, `Vector`et `VectorView` . Ces classes sont des implémentations concrètes des interfaces correspondantes qui sont définies dans l’espace de noms [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) . Les types de collection concrets ne sont pas portables à travers l'ABI (par exemple, lorsqu'un programme JavaScript ou C# fait appel au composant C++), mais ils sont implicitement convertibles en leurs types d'interface correspondants. Par exemple, si vous implémentez une méthode publique qui remplit et retourne une collection, utilisez [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) pour implémenter la collection en interne et utilisez [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) comme type de retour. Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md) et [création de composants Windows Runtime en C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 Vous pouvez construire un Platform::Collections::Vector à partir d'un [std::vector](../standard-library/vector-class.md) et un [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) à partir d'un [std::map](../standard-library/map-class.md).  
  
 En outre, l’espace de noms Platform::Collection prend en charge insert arrière et des itérateurs d’entrée, et `Vector` et `VectorView` itérateurs.  
  
 Vous devez inclure (`#include`) l'en-tête collection.h pour utiliser les types de l'espace de noms Platform::Collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collection;  
```  
  
### <a name="members"></a>Membres  
 Cet espace de noms contient les membres ci-dessous.  
  
|Nom|Description|  
|----------|-----------------|  
|[Platform::Collections::BackInsertIterator, classe](../cppcx/platform-collections-backinsertiterator-class.md)|Représente un itérateur qui insère un élément à la fin d'une collection.|  
|[Platform::Collections::InputIterator, classe](../cppcx/platform-collections-inputiterator-class.md)|Représente un itérateur qui insère un élément au début d'une collection.|  
|[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)|Représente une collection modifiable de paires clé/valeur accessibles par une clé. Semblable à [std::map](../standard-library/map-class.md).|  
|[classe Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)|Représente une collection en lecture seule de paires clé/valeur accessibles par une clé.|  
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|Représente une séquence d'éléments modifiable. Semblable à [std::vector](../standard-library/vector-class.md).|  
|[Platform::Collections::VectorIterator, classe](../cppcx/platform-collections-vectoriterator-class.md)|Représente un itérateur qui parcourt une collection `Vector` .|  
|[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)|Représente une séquence d'éléments en lecture seule.|  
|[Platform::Collections::VectorViewIterator, classe](../cppcx/platform-collections-vectorviewiterator-class.md)|Représente un itérateur qui parcourt une collection `VectorView` .|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)  
  
### <a name="requirements"></a>Spécifications  
 **Métadonnées :** platform.winmd  
  
 **Espace de noms :** Platform::Collections  
  
 **Option du compilateur :** /ZW  
  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](../cppcx/platform-namespace-c-cx.md)