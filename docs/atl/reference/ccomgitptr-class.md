---
description: 'En savoir plus sur : classe CComGITPtr'
title: CComGITPtr, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: a457c0dea1679b177b72318d636c856334c85e36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146638"
---
# <a name="ccomgitptr-class"></a>CComGITPtr, classe

Cette classe fournit des méthodes pour traiter les pointeurs d’interface et la table d’interface globale (GIT).

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type du pointeur d’interface à stocker dans la GIT.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Constructeur.|
|[CComGITPtr :: ~ CComGITPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComGITPtr :: Attach](#attach)|Appelez cette méthode pour inscrire le pointeur d’interface dans la table GIT (Global Interface Table).|
|[CComGITPtr :: CopyTo](#copyto)|Appelez cette méthode pour copier l’interface de la table GIT (Global Interface Table) vers le pointeur passé.|
|[CComGITPtr ::D Etach](#detach)|Appelez cette méthode pour dissocier l’interface de l' `CComGITPtr` objet.|
|[CComGITPtr :: GetCookie](#getcookie)|Appelez cette méthode pour retourner le cookie de l' `CComGITPtr` objet.|
|[CComGITPtr :: Revoke](#revoke)|Appelez cette méthode pour supprimer l’interface de la table GIT (Global Interface Table).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr :: Operator DWORD](#operator_dword)|Retourne le cookie de l' `CComGITPtr` objet.|
|[CComGITPtr :: Operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr :: m_dwCookie](#m_dwcookie)|Cookie.|

## <a name="remarks"></a>Notes

Les objets qui agrègent le marshaleur de thread libre et doivent utiliser des pointeurs d’interface obtenus à partir d’autres objets doivent effectuer des étapes supplémentaires pour garantir que les interfaces sont correctement marshalées. En général, cela implique le stockage des pointeurs d’interface dans le GIT et l’obtention du pointeur de la GIT à chaque fois qu’il est utilisé. La classe `CComGITPtr` est fournie pour vous aider à utiliser des pointeurs d’interface stockés dans le git.

> [!NOTE]
> La fonction table d’interface globale est disponible uniquement sur Windows 95 avec DCOM version 1,1 et ultérieure, Windows 98, Windows NT 4,0 avec Service Pack 3 et versions ultérieures et Windows 2000.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomgitptrattach"></a><a name="attach"></a> CComGITPtr :: Attach

Appelez cette méthode pour inscrire le pointeur d’interface dans la table GIT (Global Interface Table).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur d’interface à ajouter à GIT.

*dwCookie*<br/>
Cookie utilisé pour identifier le pointeur d’interface.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si le GIT n’est pas valide ou si le cookie est égal à NULL.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a> CComGITPtr::CComGITPtr

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
dans Pointeur d’interface à stocker dans la table d’interface globale (GIT).

*git*<br/>
dans Référence à un objet existant `CComGITPtr` .

*dwCookie*<br/>
dans Cookie utilisé pour identifier le pointeur d’interface.

*v*<br/>
dans Objet source à `CComGITPtr` partir duquel déplacer des données.

### <a name="remarks"></a>Notes

Crée un `CComGITPtr` objet, éventuellement à l’aide d’un `CComGITPtr` objet existant.

Le constructeur qui utilise *RV* est un constructeur de déplacement. Les données sont déplacées à partir de la source, *RV*, puis *RV* est effacé.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a> CComGITPtr :: ~ CComGITPtr

Destructeur.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Notes

Supprime l’interface de la table GIT (Global Interface Table) à l’aide de [CComGITPtr :: Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a> CComGITPtr :: CopyTo

Appelez cette méthode pour copier l’interface de la table GIT (Global Interface Table) vers le pointeur passé.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur qui doit recevoir l’interface.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

L’interface du GIT est copiée vers le pointeur passé. Le pointeur doit être libéré par l’appelant lorsqu’il n’est plus nécessaire.

## <a name="ccomgitptrdetach"></a><a name="detach"></a> CComGITPtr ::D Etach

Appelez cette méthode pour dissocier l’interface de l' `CComGITPtr` objet.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le cookie de l' `CComGITPtr` objet.

### <a name="remarks"></a>Notes

Il revient à l’appelant de supprimer l’interface du GIT, à l’aide de [CComGITPtr :: Revoke](#revoke).

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a> CComGITPtr :: GetCookie

Appelez cette méthode pour retourner le cookie de l' `CComGITPtr` objet.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le cookie.

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a> CComGITPtr :: m_dwCookie

Cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Notes

Le cookie est une variable membre utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a> CComGITPtr :: Operator =

Opérateur d’assignation.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers une interface.

*git*<br/>
dans Référence à un `CComGITPtr` objet.

*dwCookie*<br/>
dans Cookie utilisé pour identifier le pointeur d’interface.

*v*<br/>
dans À `CComGITPtr` partir duquel déplacer des données.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CComGITPtr` .

### <a name="remarks"></a>Notes

Assigne une nouvelle valeur à un `CComGITPtr` objet, soit à partir d’un objet existant, soit à partir d’une référence à une table d’interface globale.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a> CComGITPtr :: Operator DWORD

Retourne le cookie associé à l' `CComGITPtr` objet.

```
operator DWORD() const;
```

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a> CComGITPtr :: Revoke

Appelez cette méthode pour supprimer l’interface actuelle de la table GIT (Global Interface Table).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Supprime l’interface du GIT.

## <a name="see-also"></a>Voir aussi

[Marshaleur libre de threads](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Accès aux interfaces à travers les Apartments](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Quand utiliser la table d’interface globale](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
