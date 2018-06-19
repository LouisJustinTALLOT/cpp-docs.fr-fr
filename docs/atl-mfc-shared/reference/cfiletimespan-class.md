---
title: Classe de CFileTimeSpan | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: facf4abc01ed55ec7c6d84755530a776c68e166d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362736"
---
# <a name="cfiletimespan-class"></a>Classe de CFileTimeSpan
Cette classe fournit des méthodes pour la gestion des dates relatives et associés à un fichier de valeurs d’heure.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Appelez cette méthode pour récupérer l’intervalle de temps à partir de la `CFileTimeSpan` objet.|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Appelez cette méthode pour définir la durée de la `CFileTimeSpan` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|Effectue une soustraction sur un `CFileTimeSpan` objet.|  
|[CFileTimeSpan::operator ! =](#operator_neq)|Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.|  
|[CFileTimeSpan::operator +](#operator_add)|Exécute l’addition sur un `CFileTimeSpan` objet.|  
|[CFileTimeSpan::operator +=](#operator_add_eq)|Exécute l’addition sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.|  
|[CFileTimeSpan::operator &lt;](#operator_lt)|Compare deux `CFileTimeSpan` objets afin de déterminer le plus petit.|  
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Compare deux `CFileTimeSpan` objets afin de déterminer l’égalité ou le plus petit.|  
|[CFileTimeSpan::operator =](#operator_eq)|L’opérateur d’assignation.|  
|[CFileTimeSpan::operator =](#operator_-_eq)|Effectue une soustraction sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.|  
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.|  
|[CFileTimeSpan::operator &gt;](#operator_gt)|Compare deux `CFileTimeSpan` objets afin de déterminer le plus grand.|  
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Compare deux `CFileTimeSpan` objets afin de déterminer l’égalité ou le plus grand.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes pour la gestion des périodes relatives de temps souvent rencontrés lors des opérations relatives un fichier a été créé, dernier accès ou de dernière modification. Les méthodes de cette classe sont fréquemment utilisés conjointement avec [CFileTime classe](../../atl-mfc-shared/reference/cfiletime-class.md) objets.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atltime.h  
  
##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan  
 Constructeur.  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` existant.  
  
 `nSpan`  
 Une période de temps en millisecondes.  
  
### <a name="remarks"></a>Notes  
 Le `CFileTimeSpan` objet peut être créé en utilisant un existant `CFileTimeSpan` de l’objet ou exprimé comme une valeur 64 bits. Le constructeur par défaut définit l’intervalle de temps à 0.  
  
##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan  
 Appelez cette méthode pour récupérer l’intervalle de temps à partir de la `CFileTimeSpan` objet.  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie l’intervalle de temps en millisecondes.  
  
##  <a name="operator_-"></a>  CFileTimeSpan::operator-  
 Effectue une soustraction sur un **CFileTimeSpan** objet.  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CFileTimeSpan` objet représentant le résultat de la différence entre deux intervalles de temps.  
  
##  <a name="operator_neq"></a>  CFileTimeSpan::operator ! =  
 Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si l’élément en cours de comparaison n’est pas égale à la `CFileTimeSpan` de l’objet ; sinon **false**.  
  
##  <a name="operator_add"></a>  CFileTimeSpan::operator +  
 Exécute l’addition sur un `CFileTimeSpan` objet.  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `CFileTimeSpan` contenant la somme de l’heure à deux étendues de l’objet.  
  
##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=  
 Exécute l’addition sur un `CFileTimeSpan` de l’objet et assigne le résultat à l’objet actuel.  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CFileTimeSpan` contenant la somme de l’heure à deux étendues de l’objet.  
  
##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;  
 Compare deux `CFileTimeSpan` objets afin de déterminer le plus petit.  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est inférieur (autrement dit, représente une période plus courte) à la seconde, sinon **false**.  
  
##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=  
 Compare deux `CFileTimeSpan` objets afin de déterminer l’égalité ou le plus petit.  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est inférieur à (autrement dit, représente une période plus courte) ou égale à la seconde, sinon **false**.  
  
##  <a name="operator_eq"></a>  CFileTimeSpan::operator =  
 L’opérateur d’assignation.  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CFileTimeSpan` objet.  
  
##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator =  
 Effectue une soustraction sur un `CFileTimeSpan` de l’objet et assigne le résultat à l’objet actuel.  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CFileTimeSpan` objet.  
  
##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==  
 Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si les objets sont égaux, sinon **false**.  
  
##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;  
 Compare deux `CFileTimeSpan` objets afin de déterminer le plus grand.  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est supérieur à (autrement dit, représente une période plus longue) à la seconde, sinon **false**.  
  
##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=  
 Compare deux `CFileTimeSpan` objets afin de déterminer l’égalité ou le plus grand.  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `span`  
 Objet `CFileTimeSpan` à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le premier objet est supérieur à (autrement dit, représente une période plus longue) ou égale à la seconde, sinon **false**.  
  
##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan  
 Appelez cette méthode pour définir la durée de la `CFileTimeSpan` objet.  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nSpan`  
 La nouvelle valeur pour l’intervalle de temps en millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [Classe de CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


