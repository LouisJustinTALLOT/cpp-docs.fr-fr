---
title: Classe CComGITPtr
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
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327836"
---
# <a name="ccomgitptr-class"></a>Classe CComGITPtr

Cette classe fournit des méthodes pour traiter les pointeurs d’interface et la table d’interface globale (GIT).

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
|[CComGITPtr: :CComGITPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Appelez cette méthode pour enregistrer le pointeur d’interface dans la table d’interface globale (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) au pointeur passé.|
|[CComGITPtr::Detach](#detach)|Appelez cette méthode pour dissocier `CComGITPtr` l’interface de l’objet.|
|[CComGITPtr::GetCookie](#getcookie)|Appelez cette méthode pour retourner `CComGITPtr` le cookie de l’objet.|
|[CComGITPtr::Revoke](#revoke)|Appelez cette méthode pour supprimer l’interface de la table d’interface globale (GIT).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::opérateur DWORD](#operator_dword)|Renvoie le `CComGITPtr` cookie de l’objet.|
|[CComGITPtr::opérateur](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie.|

## <a name="remarks"></a>Notes

Les objets qui agrégent le maréchal fileté gratuit et doivent utiliser des indications d’interface obtenues à partir d’autres objets doivent prendre des mesures supplémentaires pour s’assurer que les interfaces sont correctement marshaled. Typiquement, cela implique le stockage des pointeurs d’interface dans le GIT et obtenir le pointeur de la GIT chaque fois qu’il est utilisé. La `CComGITPtr` classe est fournie pour vous aider à utiliser des indications d’interface stockées dans le GIT.

> [!NOTE]
> L’installation globale de table d’interface n’est disponible que sur Windows 95 avec la version 1.1 DCOM et plus tard, Windows 98, Windows NT 4.0 avec Service Pack 3 et plus tard, et Windows 2000.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::Attach

Appelez cette méthode pour enregistrer le pointeur d’interface dans la table d’interface globale (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Le pointeur d’interface à ajouter au GIT.

*dwCookie*<br/>
Le cookie utilisé pour identifier le pointeur d’interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si le GIT n’est pas valide, ou si le cookie est égal à NULL.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

Constructeur.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Un pointeur d’interface à stocker dans la table d’interface globale (GIT).

*Git*<br/>
[dans] Une référence à `CComGITPtr` un objet existant.

*dwCookie*<br/>
[dans] Un cookie utilisé pour identifier le pointeur d’interface.

*Rv*<br/>
[dans] La `CComGITPtr` source s’oppose à déplacer les données.

### <a name="remarks"></a>Notes

Crée un `CComGITPtr` nouvel objet, en `CComGITPtr` option à l’aide d’un objet existant.

Le constructeur utilisant le *rv* est un constructeur de mouvement. Les données sont déplacées à partir de la source, *rv*, puis *rv* est effacé.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr: :CComGITPtr

Destructeur.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Notes

Supprime l’interface de la table d’interface globale (GIT), à l’aide [de CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr::CopyTo

Appelez cette méthode pour copier l’interface à partir de la table d’interface globale (GIT) au pointeur passé.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Paramètres

*Pp*<br/>
Le pointeur qui est de recevoir l’interface.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

L’interface du GIT est copiée sur le pointeur passé. Le pointeur doit être libéré par l’appelant lorsqu’il n’est plus nécessaire.

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::Detach

Appelez cette méthode pour dissocier `CComGITPtr` l’interface de l’objet.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie le `CComGITPtr` cookie de l’objet.

### <a name="remarks"></a>Notes

C’est à l’appelant de supprimer l’interface du GIT, à l’aide de [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr::GetCookie

Appelez cette méthode pour retourner `CComGITPtr` le cookie de l’objet.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le cookie.

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

Cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Notes

Le cookie est une variable de membre utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::opérateur

L’opérateur de l’affectation.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Un pointeur à une interface.

*Git*<br/>
[dans] Une référence `CComGITPtr` à un objet.

*dwCookie*<br/>
[dans] Un cookie utilisé pour identifier le pointeur d’interface.

*Rv*<br/>
[dans] Le `CComGITPtr` déplacement des données à partir de.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CComGITPtr`

### <a name="remarks"></a>Notes

Attribue une nouvelle valeur `CComGITPtr` à un objet, soit à partir d’un objet existant, soit à partir d’une référence à une table d’interface globale.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::opérateur DWORD

Retourne le cookie `CComGITPtr` associé à l’objet.

```
operator DWORD() const;
```

### <a name="remarks"></a>Notes

Le cookie est une variable utilisée pour identifier une interface et son emplacement.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr::Revoke

Appelez cette méthode pour supprimer l’interface actuelle de la table d’interface globale (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Supprime l’interface du GIT.

## <a name="see-also"></a>Voir aussi

[Marshaler filé gratuit](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Accès aux interfaces à travers les appartements](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Quand utiliser la table d’interface mondiale](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
