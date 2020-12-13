---
description: 'En savoir plus sur : classe CAutoRevertImpersonation'
title: CAutoRevertImpersonation, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 48009a4d146866d36eebc75ada8f9ae12058287a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147080"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation, classe

Cette classe restaure les objets [caccesstoken,](../../atl/reference/caccesstoken-class.md) à un État sans emprunt d’identité lorsqu’ils sont hors de portée.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construit un `CAutoRevertImpersonation` objet|
|[CAutoRevertImpersonation :: ~ CAutoRevertImpersonation](#dtor)|Détruit l’objet et rétablit l’emprunt d’identité du jeton d’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation :: Attach](#attach)|Automatise la reconversion d’emprunt d’identité d’un jeton d’accès.|
|[CAutoRevertImpersonation ::D Etach](#detach)|Annule la réversion automatique de l’emprunt d’identité.|
|[CAutoRevertImpersonation :: GetAccessToken](#getaccesstoken)|Récupère le jeton d’accès actuel associé à cet objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est alloué à chaque utilisateur connecté à un système Windows NT ou Windows 2000. Ces jetons d’accès peuvent être représentés avec la `CAccessToken` classe.

Il est parfois nécessaire d’emprunter l’identité des jetons d’accès. Cette classe est fournie à des fins pratiques, mais elle n’effectue pas l’emprunt d’identité des jetons d’accès ; il effectue uniquement la reconversion automatique vers un État sans emprunt d’identité. Cela est dû au fait que l’emprunt d’identité d’accès au jeton peut être effectué de plusieurs façons différentes.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a> CAutoRevertImpersonation :: Attach

Automatise la reconversion d’emprunt d’identité d’un jeton d’accès.

```cpp
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*Brevets*<br/>
Adresse de l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) à rétablir automatiquement

### <a name="remarks"></a>Notes

Cette méthode doit être utilisée uniquement si l’objet [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) a été créé avec un `CAccessToken` pointeur null ou si [Detach](#detach) a été appelé précédemment. Pour les cas simples, il n’est pas nécessaire d’utiliser cette méthode.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a> CAutoRevertImpersonation::CAutoRevertImpersonation

Construit un objet `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*Brevets*<br/>
Adresse de l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) à rétablir automatiquement.

### <a name="remarks"></a>Notes

L’emprunt d’identité réel du jeton d’accès doit être effectué séparément de et de préférence avant la création d’un `CAutoRevertImpersonation` objet. Cet emprunt d’identité est rétabli automatiquement lorsque l' `CAutoRevertImpersonation` objet est hors de portée.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a> CAutoRevertImpersonation :: ~ CAutoRevertImpersonation

Détruit l’objet et rétablit l’emprunt d’identité du jeton d’accès.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Notes

Rétablit les emprunts d’identité actuellement appliqués pour l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) fourni à la construction ou via la méthode d' [attachement](#attach) . Si aucun `CAccessToken` n’est associé, le destructeur n’a aucun effet.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a> CAutoRevertImpersonation ::D Etach

Annule la réversion automatique de l’emprunt d’identité.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse du [caccesstoken,](../../atl/reference/caccesstoken-class.md)précédemment associé, ou null si aucune association n’existait.

### <a name="remarks"></a>Notes

L’appel de **Detach** empêche l' `CAutoRevertImpersonation` objet de rétablir un emprunt d’identité actuellement en vigueur pour l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) associé à cet objet. `CAutoRevertImpersonation` peut ensuite être détruit sans effet ni réassocié au même objet ou à un autre `CAccessToken` objet à l’aide de l' [attachement](#attach).

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a> CAutoRevertImpersonation :: GetAccessToken

Récupère le jeton d’accès actuel associé à cet objet.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse du [caccesstoken,](../../atl/reference/caccesstoken-class.md)précédemment associé, ou null si aucune association n’existait.

### <a name="remarks"></a>Notes

Si cette méthode est appelée à des fins qui incluent la réversion d’un emprunt d’identité de l' `CAccessToken` objet, la méthode de [détachement](#detach) doit être utilisée à la place.

## <a name="see-also"></a>Voir aussi

[ATLSecurity, exemple](../../overview/visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/win32/SecAuthZ/access-tokens)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
