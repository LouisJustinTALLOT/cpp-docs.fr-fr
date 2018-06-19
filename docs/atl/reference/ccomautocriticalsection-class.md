---
title: Classe de CComAutoCriticalSection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae0c3cd1d00ce83a4e952d60a978663bfa76f814
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357227"
---
# <a name="ccomautocriticalsection-class"></a>Classe de CComAutoCriticalSection
`CComAutoCriticalSection` Fournit des méthodes pour obtenir et de libérer la possession d’un objet de section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Constructeur.|  
|[CComAutoCriticalSection :: ~ CComAutoCriticalSection](#dtor)|Destructeur.|  
  
## <a name="remarks"></a>Notes  
 `CComAutoCriticalSection` est semblable à la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), à l’exception `CComAutoCriticalSection` initialise automatiquement l’objet de section critique dans le constructeur.  
  
 En général, vous utilisez `CComAutoCriticalSection` via la `typedef` nom [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ce nom fait référence à `CComAutoCriticalSection` lorsque [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) est utilisé.  

  
 Le `Init` et `Term` méthodes à partir de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ne sont pas disponibles lors de l’utilisation de cette classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection  
 Constructeur.  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>Notes  
 Appelle la fonction Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), qui initialise l’objet de section critique.  
  
##  <a name="dtor"></a>  CComAutoCriticalSection :: ~ CComAutoCriticalSection  
 Destructeur.  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur appelle [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), ce qui libère toutes les ressources système utilisées par l’objet de section critique.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)
