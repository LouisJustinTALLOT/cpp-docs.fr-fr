---
title: ISupportErrorInfoImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3f912f7ba3a5455f7583ba2a5036548ac65df2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022173"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl, classe

Cette classe fournit une implémentation par défaut de la [ISupportErrorInfo Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```

#### <a name="parameters"></a>Paramètres

*piid*<br/>
Un pointeur vers l’IID d’une interface qui prend en charge [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indique si l’interface identifié par `riid` prend en charge la [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interface.|

## <a name="remarks"></a>Notes

Le [ISupportErrorInfo Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) garantit que les informations d’erreur peuvent être retournées au client. Objets qui utilisent `IErrorInfo` doit implémenter `ISupportErrorInfo`.

Classe `ISupportErrorInfoImpl` fournit une implémentation par défaut de `ISupportErrorInfo` et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet. Exemple :

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indique si l’interface identifié par `riid` prend en charge la [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interface.

```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Notes

Consultez [ISupportErrorInfo::InterfaceSupportsErrorInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) dans le Kit de développement logiciel Windows.

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

Appelez cette méthode pour obtenir le nombre de threads dans le pool.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Paramètres

*pnNumThreads*<br/>
[out] Adresse de la variable qui, en cas de réussite, reçoit le nombre de threads dans le pool.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

Appelez cette méthode pour obtenir la durée maximale en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Paramètres

*pdwMaxWait*<br/>
[out] Adresse de la variable recevant, en cas de réussite, la durée maximale en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

Appelez cette méthode pour définir le nombre de threads dans le pool.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Paramètres

*nNumThreads*<br/>
Le nombre demandé de threads dans le pool.

Si *nNumThreads* est négatif, sa valeur absolue sera multipliée par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.

Si *nNumThreads* est égal à zéro, ATLS_DEFAULT_THREADSPERPROC sera multiplié par le nombre de processeurs sur l’ordinateur pour obtenir le nombre total de threads.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

Appelez cette méthode pour définir le temps maximal en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Paramètres

*dwMaxWait*<br/>
La durée maximale demandée en millisecondes pendant lequel le pool de threads doit attendre un thread à arrêter.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="example"></a>Exemple

Consultez [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
