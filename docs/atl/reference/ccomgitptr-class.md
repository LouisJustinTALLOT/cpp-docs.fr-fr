---
title: CComGITPtr, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5707a7fd4ab83c8e3de3c4868ad41e3525621b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033951"
---
# <a name="ccomgitptr-class"></a>CComGITPtr, classe

Cette classe fournit des méthodes pour la gestion des pointeurs d’interface et la table d’interface globale (GIT).

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de pointeur d’interface à stocker dans le GIT.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Constructeur.|
|[CComGITPtr :: ~ CComGITPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Appelez cette méthode pour inscrire le pointeur d’interface dans la table d’interface globale (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) pour le pointeur passé.|
|[CComGITPtr::Detach](#detach)|Appelez cette méthode pour dissocier l’interface à partir de la `CComGITPtr` objet.|
|[CComGITPtr::GetCookie](#getcookie)|Appelez cette méthode pour retourner le cookie à partir de la `CComGITPtr` objet.|
|[CComGITPtr::Revoke](#revoke)|Appelez cette méthode pour supprimer l’interface à partir de la table d’interface globale (GIT).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Retourne le cookie à partir de la `CComGITPtr` objet.|
|[CComGITPtr::operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Le cookie.|

## <a name="remarks"></a>Notes

Les objets qui agrègent FTM et doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent suivre des étapes supplémentaires pour garantir que les interfaces sont correctement marshalées. En général, cela implique de stocker les pointeurs d’interface dans le GIT et le pointeur de la GIT chaque fois qu’il est utilisé. La classe `CComGITPtr` est fourni pour vous aider à utiliser des pointeurs d’interface stockés dans le GIT.

> [!NOTE]
>  La fonctionnalité de tableau global d’interface est uniquement disponible sur Windows 95 avec DCOM version 1.1 et versions ultérieures, Windows 98, Windows NT 4.0 avec Service Pack 3 et versions ultérieures et Windows 2000.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="attach"></a>  CComGITPtr::Attach

Appelez cette méthode pour inscrire le pointeur d’interface dans la table d’interface globale (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Le pointeur d’interface à ajouter à la GIT.

*dwCookie*<br/>
Le cookie est utilisé pour identifier le pointeur d’interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si le GIT n’est pas valide, ou si le cookie est égal à NULL.

##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr

Constructeur.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Un pointeur d’interface à stocker dans la table d’interface globale (GIT).

*GIT*<br/>
[in] Une référence à un existant `CComGITPtr` objet.

*dwCookie*<br/>
[in] Un cookie est utilisé pour identifier le pointeur d’interface.

*RV*<br/>
[in] La source `CComGITPtr` objet à déplacer des données à partir de.

### <a name="remarks"></a>Notes

Crée un `CComGITPtr` de l’objet, en utilisant éventuellement un existant `CComGITPtr` objet.

Le constructeur utilisant *rv* est un constructeur de déplacement. Les données sont déplacées à partir de la source, *rv*, puis *rv* est désactivée.

##  <a name="dtor"></a>  CComGITPtr :: ~ CComGITPtr

Destructeur.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Notes

Supprime l’interface à partir de la table d’interface globale (GIT), à l’aide de [CComGITPtr::Revoke](#revoke).

##  <a name="copyto"></a>  CComGITPtr::CopyTo

Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) pour le pointeur passé.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Paramètres

*PP*<br/>
Le pointeur qui doit recevoir l’interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

L’interface à partir du GIT est copié vers le pointeur passé. Le pointeur doit être libéré par l’appelant lorsqu’elle n’est plus nécessaire.

##  <a name="detach"></a>  CComGITPtr::Detach

Appelez cette méthode pour dissocier l’interface à partir de la `CComGITPtr` objet.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le cookie à partir de la `CComGITPtr` objet.

### <a name="remarks"></a>Notes

C’est à l’appelant de supprimer l’interface à partir de la GIT, à l’aide de [CComGITPtr::Revoke](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Appelez cette méthode pour retourner le cookie à partir de la `CComGITPtr` objet.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le cookie.

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

Le cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Notes

Le cookie est une variable de membre utilisée pour identifier une interface et son emplacement.

##  <a name="operator_eq"></a>  CComGITPtr::operator =

L’opérateur d’assignation.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers une interface.

*GIT*<br/>
[in] Une référence à un `CComGITPtr` objet.

*dwCookie*<br/>
[in] Un cookie est utilisé pour identifier le pointeur d’interface.

*RV*<br/>
[in] Le `CComGITPtr` pour déplacer des données à partir de.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CComGITPtr` objet.

### <a name="remarks"></a>Notes

Assigne une nouvelle valeur à un `CComGITPtr` objet, à partir d’un objet existant ou à partir d’une référence à un tableau global d’interface.

##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD

Retourne le cookie associé à la `CComGITPtr` objet.

```
operator DWORD() const;
```

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

##  <a name="revoke"></a>  CComGITPtr::Revoke

Appelez cette méthode pour supprimer l’interface actuelle à partir de la table d’interface globale (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Supprime l’interface à partir de la GIT.

## <a name="see-also"></a>Voir aussi

[FTM](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Accès aux Interfaces entre les cloisonnements](/windows/desktop/com/accessing-interfaces-across-apartments)<br/>
[Quand utiliser le tableau Global d’Interface](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
