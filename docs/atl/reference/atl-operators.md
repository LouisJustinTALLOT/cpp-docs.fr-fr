---
title: Les opérateurs ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75c9ffb8c918cce70ad1e150dd80cb07ebdd7b34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360934"
---
# <a name="atl-operators"></a>Opérateurs d’ATL
Cette section contient les rubriques de référence pour les opérateurs globaux ATL.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[opérateur ==](#operator_eq_eq)|Compare deux `CSid` objets ou `SID` structures sont égales.|  
|[opérateur ! =](#operator_neq)|Compare deux `CSid` objets ou `SID` structures d’inégalité.|  
|[opérateur <](#operator_lt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieure à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|  
|[opérateur >](#operator_gt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|  
|[opérateur < =](#operator_lt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|  
|[opérateur > =](#operator_gt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h.  
  
##  <a name="operator_eq_eq"></a>  opérateur ==  
 Compare `CSid` objets ou `SID` l’égalité des structures (identificateur de sécurité).  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si les objets sont égaux, **false** s’ils ne sont pas égaux.  
  
##  <a name="operator_neq"></a>  opérateur ! =  
 Compare `CSid` objets ou `SID` inégalité des structures (identificateur de sécurité).  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si les objets ne sont pas égaux, **false** s’ils sont égaux.  
  
##  <a name="operator_lt"></a>  opérateur <  
 Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieure à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’adresse de la `lhs` objet est inférieur à l’adresse de la `rhs` objet, **false** dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` de la structure et est implémenté pour assurer la compatibilité avec les classes de collection de bibliothèque C++ Standard.  
  
##  <a name="operator_gt"></a>  opérateur >  
 Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’adresse de la `lhs` est supérieure à l’adresse de la `rhs`, **false** dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` de la structure et est implémenté pour assurer la compatibilité avec les classes de collection de bibliothèque C++ Standard.  
  
##  <a name="operator_lt__eq"></a>  opérateur < =  
 Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’adresse de la `lhs` est inférieur ou égal à l’adresse de la `rhs`, **false** dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` de la structure et est implémenté pour assurer la compatibilité avec les classes de collection de bibliothèque C++ Standard.  
  
##  <a name="operator_gt__eq"></a>  opérateur > =  
 Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première `CSid` objet ou `SID` structure à comparer.  
  
 `rhs`  
 La seconde `CSid` objet ou `SID` structure à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’adresse de la `lhs` est supérieur ou égal à l’adresse de la `rhs`, **false** dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` de la structure et est implémenté pour assurer la compatibilité avec les classes de collection de bibliothèque C++ Standard.



