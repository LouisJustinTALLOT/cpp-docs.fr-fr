---
title: Cautorevertimpersonation, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45a14f8c742393c60a026f7c58217407715ef282
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052735"
---
# <a name="cautorevertimpersonation-class"></a>Cautorevertimpersonation, classe

Cette classe rétablit [CAccessToken](../../atl/reference/caccesstoken-class.md) objets à un état nonimpersonating lorsqu’il devient hors de portée.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construit un `CAutoRevertImpersonation` objet|
|[CAutoRevertImpersonation :: ~ CAutoRevertImpersonation](#dtor)|Détruit l’objet et rétablit le jeton d’emprunt d’identité de l’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatise le rétablissement de l’emprunt d’identité d’un jeton d’accès.|
|[CAutoRevertImpersonation::Detach](#detach)|Annule le rétablissement de l’emprunt d’identité automatique.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Récupère l’actuel jeton accès associé à cet objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/desktop/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou un thread et est alloué à chaque utilisateur connecté à un système Windows NT ou Windows 2000. Ces jetons d’accès peuvent être représentées avec la `CAccessToken` classe.

Il est parfois nécessaire d’emprunter l’identité des jetons d’accès. Cette classe est fournie pour des raisons pratiques, mais il n’effectue pas l’emprunt d’identité des jetons d’accès ; Il effectue uniquement le rétablissement automatique à un état nonimpersonated. Il s’agit, car l’emprunt d’identité du jeton d’accès peut être effectuée de différentes manières.

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

##  <a name="attach"></a>  CAutoRevertImpersonation::Attach

Automatise le rétablissement de l’emprunt d’identité d’un jeton d’accès.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*PAT*<br/>
L’adresse de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objet à être rétablis automatiquement

### <a name="remarks"></a>Notes

Cette méthode doit uniquement être utilisée si le [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objet a été créé avec une valeur NULL `CAccessToken` pointeur, ou si [détachement](#detach) a été appelée précédemment. Pour les cas simples, il n’est pas nécessaire d’utiliser cette méthode.

##  <a name="cautorevertimpersonation"></a>  CAutoRevertImpersonation::CAutoRevertImpersonation

Construit un objet `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*PAT*<br/>
L’adresse de la [CAccessToken](../../atl/reference/caccesstoken-class.md) objet à être restauré automatiquement.

### <a name="remarks"></a>Notes

L’emprunt d’identité réelle du jeton d’accès doit s’effectuer séparément à partir d’et de préférence avant la création d’un `CAutoRevertImpersonation` objet. Cet emprunt d’identité est automatiquement restauré lorsque la `CAutoRevertImpersonation` objet est hors de portée.

##  <a name="dtor"></a>  CAutoRevertImpersonation :: ~ CAutoRevertImpersonation

Détruit l’objet et rétablit le jeton d’emprunt d’identité de l’accès.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Notes

Annule un emprunt d’identité actuellement en vigueur pour le [CAccessToken](../../atl/reference/caccesstoken-class.md) objet fourni à la construction ou via le [attacher](#attach) (méthode). Si aucun `CAccessToken` est associé, le destructeur n’a aucun effet.

##  <a name="detach"></a>  CAutoRevertImpersonation::Detach

Annule le rétablissement de l’emprunt d’identité automatique.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

L’adresse associé précédemment [CAccessToken](../../atl/reference/caccesstoken-class.md), ou NULL si aucune association n’existe.

### <a name="remarks"></a>Notes

Appel **détachement** empêche le `CAutoRevertImpersonation` objet possible de rétrograder un emprunt d’identité actuellement en vigueur pour le [CAccessToken](../../atl/reference/caccesstoken-class.md) objet associé à cet objet. `CAutoRevertImpersonation` peut être détruit sans aucune incidence ou réassociés à la même ou un autre `CAccessToken` à l’aide de l’objet [attacher](#attach).

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

Récupère l’actuel jeton accès associé à cet objet.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valeur de retour

L’adresse associé précédemment [CAccessToken](../../atl/reference/caccesstoken-class.md), ou NULL si aucune association n’existe.

### <a name="remarks"></a>Notes

Si cette méthode est appelée dans le cadre qui incluent le rétablissement d’un emprunt d’identité de le `CAccessToken` objet, le [détachement](#detach) méthode doit être utilisée à la place.

## <a name="see-also"></a>Voir aussi

[Exemple ATLSecurity](../../visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
