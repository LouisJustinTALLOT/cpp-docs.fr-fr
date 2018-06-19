---
title: Classe de CComPtrBase | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea90c1394da9b6a202b121a0e521f99acaba8264
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366365"
---
# <a name="ccomptrbase-class"></a>Classe de CComPtrBase
Cette classe fournit une base pour les classes de pointeur intelligent à l’aide des routines basé sur COM de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type d’objet d’être référencées par le pointeur intelligent.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPtrBase :: ~ CComPtrBase](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|Appelez cette méthode pour créer une connexion entre le `CComPtrBase`du point de connexion et le récepteur d’un client.|  
|[CComPtrBase::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Appelez cette méthode pour créer un objet de la classe associée à un ID de classe ou ID de programme.|  
|[CComPtrBase::CopyTo](#copyto)|Appelez cette méthode pour copier le `CComPtrBase` pointeur vers une autre variable de pointeur.|  
|[CComPtrBase::Detach](#detach)|Appelez cette méthode pour libérer la possession d’un pointeur.|  
|[CComPtrBase::IsEqualObject](#isequalobject)|Appeler cette méthode pour vérifier si le texte spécifié **IUnknown** pointe vers le même objet associé à la `CComPtrBase` objet.|  
|[CComPtrBase::QueryInterface](#queryinterface)|Appelez cette méthode pour retourner un pointeur vers une interface spécifiée.|  
|[CComPtrBase::Release](#release)|Appelez cette méthode pour libérer de l’interface.|  
|[CComPtrBase::SetSite](#setsite)|Appelez cette méthode pour définir le site de la `CComPtrBase` de l’objet à la **IUnknown** de l’objet parent.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|L’opérateur de cast.|  
|[CComPtrBase::operator !](#operator_not)|L’opérateur NOT.|  
|[CComPtrBase::operator &](#operator_amp)|Le & (opérateur).|  
|[CComPtrBase::operator *](#operator_star)|Le * (opérateur).|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Moins-que l’opérateur.|  
|[CComPtrBase::operator ==](#operator_eq_eq)|L’opérateur d’égalité.|  
|[CComPtrBase::operator ->](#operator_ptr)|L’opérateur de pointeur de membre.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|La variable de membre de données de pointeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit la base d’autres pointeurs intelligents qui utilisent des routines de gestion de mémoire COM, tel que [CComQIPtr](../../atl/reference/ccomqiptr-class.md) et [CComPtr](../../atl/reference/ccomptr-class.md). Les classes dérivées ajouter leurs propres constructeurs et des opérateurs, mais s’appuient sur les méthodes fournies par `CComPtrBase`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcomcli.h  
  
##  <a name="advise"></a>  CComPtrBase::Advise  
 Appelez cette méthode pour créer une connexion entre le `CComPtrBase`du point de connexion et le récepteur d’un client.  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 Un pointeur vers du client **IUnknown**.  
  
 `iid`  
 Le GUID du point de connexion. En règle générale, cela est identique à l’interface sortante gérée par le point de connexion.  
  
 `pdw`  
 Pointeur vers le cookie qui identifie de façon unique la connexion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Consultez [AtlAdvise](connection-point-global-functions.md#atladvise) pour plus d’informations.  
  
##  <a name="attach"></a>  CComPtrBase::Attach  
 Appelez cette méthode pour prendre possession d’un pointeur existant.  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p2`  
 Le `CComPtrBase` objet prendra possession de ce pointeur.  
  
### <a name="remarks"></a>Notes  
 **Attacher** appelle [CComPtrBase::Release](#release) sur le serveur existant [CComPtrBase::p](#p) variable membre, puis assigne `p2` à `CComPtrBase::p`. Lorsqu’un `CComPtrBase` objet prend possession du pointeur, il appelle automatiquement `Release` sur le pointeur qui va supprimer le pointeur et tout allouée données si le décompte de références sur l’objet passe à 0.  
  
##  <a name="dtor"></a>  CComPtrBase :: ~ CComPtrBase  
 Destructeur.  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère l’interface désignée par `CComPtrBase`.  
  
##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance  
 Appelez cette méthode pour créer un objet de la classe associée à un ID de classe ou ID de programme.  
  
```
HRESULT CoCreateInstance(  
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(  
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `szProgID`  
 Pointeur vers un ProgID, utilisé pour récupérer le CLSID.  
  
 `pUnkOuter`  
 Si **NULL**, indique que l’objet n’est pas créée en tant que partie d’un agrégat. Si non - **NULL**, est un pointeur vers l’objet d’agrégation **IUnknown** interface (le contrôle **IUnknown**).  
  
 `dwClsContext`  
 Contexte dans lequel s’exécutera le code qui gère l’objet nouvellement créé.  
  
 `rclsid`  
 CLSID associé avec les données et le code permettant de créer l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas d’échec, retourne S_OK sur les cas de réussite, REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING ou E_NOINTERFACE. Consultez [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) et [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) pour obtenir une description de ces erreurs.  
  
### <a name="remarks"></a>Notes  
 Si la première forme de la méthode est appelée, [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) est utilisé pour récupérer le CLSID. Les deux formes puis appellent [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
 Dans les versions debug, une erreur d’assertion se produit si [CComPtrBase::p](#p) n’est pas égal à NULL.  
  
##  <a name="copyto"></a>  CComPtrBase::CopyTo  
 Appelez cette méthode pour copier le `CComPtrBase` pointeur vers une autre variable de pointeur.  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *ppT*  
 Adresse de la variable qui recevra le `CComPtrBase` pointeur.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, E_POINTER en cas d’échec, retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Copie le `CComPtrBase` pointeur vers *ppT*. Le nombre de références le [CComPtrBase::p](#p) variable membre est incrémentée.  
  
 Une erreur HRESULT sera retournée si *ppT* est égal à NULL. Dans les versions debug, une erreur d’assertion se produit si *ppT* est égal à NULL.  
  
##  <a name="detach"></a>  CComPtrBase::Detach  
 Appelez cette méthode pour libérer la possession d’un pointeur.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une copie du pointeur.  
  
### <a name="remarks"></a>Notes  
 Libère la propriété d’un pointeur, définit le [CComPtrBase::p](#p) variable de membre de données avec la valeur NULL et retourne une copie du pointeur.  
  
##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject  
 Appeler cette méthode pour vérifier si le texte spécifié **IUnknown** pointe vers le même objet associé à la `CComPtrBase` objet.  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pOther`  
 Le **IUnknown \***  à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les objets sont identiques, false dans le cas contraire.  
  
##  <a name="operator_not"></a>  CComPtrBase::operator !  
 L’opérateur NOT.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si le `CComHeapPtr` pointeur est égal à NULL, false dans le cas contraire.  
  
##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;  
 Le & (opérateur).  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’adresse de l’objet vers lequel pointé le `CComPtrBase` objet.  
  
##  <a name="operator_star"></a>  CComPtrBase::operator *  
 Le * (opérateur).  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de [CComPtrBase::p](#p); autrement dit, un pointeur vers l’objet référencé par le `CComPtrBase` objet.  
  
 Si les versions debug, une erreur d’assertion se produira si [CComPtrBase::p](#p) n’est pas égal à NULL.  
  
##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==  
 L’opérateur d’égalité.  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pT*  
 Pointeur vers un objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne true si `CComPtrBase` et *pT* pointent vers le même objet, false dans le cas contraire.  
  
##  <a name="operator_ptr"></a>  CComPtrBase::operator-&gt;  

 Opérateur pointeur vers membre.  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la [CComPtrBase::p](#p) variable de membre de données.  
  
### <a name="remarks"></a>Notes  
 Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointée le `CComPtrBase` objet. Dans les versions debug, un échec d’assertion se produit si le `CComPtrBase` membre de données pointe sur la valeur NULL.  
  
##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;  
 Moins-que l’opérateur.  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pT*  
 Pointeur vers un objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si le pointeur est géré par l’objet actuel est inférieure à celle du pointeur auquel il est comparé.  
  
##  <a name="operator_t_star"></a>  CComPtrBase::operator T *  
 L’opérateur de cast.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne un pointeur vers le type de données d’objet défini dans le modèle de classe.  
  
##  <a name="p"></a>  CComPtrBase::p  
 La variable de membre de données de pointeur.  
  
```
T* p;
```  
  
### <a name="remarks"></a>Notes  
 Cette variable membre conserve les informations de pointeur.  
  
##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface  
 Appelez cette méthode pour retourner un pointeur vers une interface spécifiée.  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `Q`  
 Le type d’objet dont pointeur d’interface est requis.  
  
 `pp`  
 Adresse de variable de sortie qui reçoit le pointeur d’interface demandé.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas d’échec, retourne S_OK sur la réussite ou E_NOINTERFACE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [IUnknown::QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Dans les versions debug, une erreur d’assertion se produit si *pp* n’est pas égal à NULL.  
  
##  <a name="release"></a>  CComPtrBase::Release  
 Appelez cette méthode pour libérer de l’interface.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’interface est publié, et [CComPtrBase::p](#p) a la valeur NULL.  
  
##  <a name="setsite"></a>  CComPtrBase::SetSite  
 Appelez cette méthode pour définir le site de la `CComPtrBase` de l’objet à la **IUnknown** de l’objet parent.  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `punkParent`  
 Un pointeur vers le **IUnknown** interface du parent.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
