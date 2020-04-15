---
title: Classe CAutoRevertImpersonation
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
ms.openlocfilehash: 813b6f0dd33bdfa85476b816086217a7892f4476
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318792"
---
# <a name="cautorevertimpersonation-class"></a>Classe CAutoRevertImpersonation

Cette classe retourne les objets [CAccessToken](../../atl/reference/caccesstoken-class.md) à un état non-personnel quand il sort de portée.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Construit un `CAutoRevertImpersonation` objet|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#dtor)|Détruit l’objet et retourne l’imitation symbolique d’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatise le retour d’imitation d’un jeton d’accès.|
|[CAutoRevertImpersonation::Detach](#detach)|Annule le retour automatique de l’usurpation d’identité.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Récupère le courant symbolique d’accès associé à cet objet.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et est attribué à chaque utilisateur connecté à un système Windows NT ou Windows 2000. Ces jetons d’accès peuvent `CAccessToken` être représentés avec la classe.

Il est parfois nécessaire de se faire passer pour des jetons d’accès. Cette classe est fournie comme commodité, mais elle n’effectue pas l’usurpation d’identité des jetons d’accès; il n’effectue que le retour automatique à un état non-personnel. C’est parce que l’imitation d’accès symbolique peut être effectuée plusieurs façons différentes.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>CAutoRevertImpersonation::Attach

Automatise le retour d’imitation d’un jeton d’accès.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*Pat*<br/>
L’adresse de l’objet [CAccessToken](../../atl/reference/caccesstoken-class.md) à revenir automatiquement

### <a name="remarks"></a>Notes

Cette méthode ne doit être utilisée que si [l’objet CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) a été créé avec un pointeur NULL, `CAccessToken` ou si [Detach](#detach) a été appelé précédemment. Pour les cas simples, il n’est pas nécessaire d’utiliser cette méthode.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Construit un objet `CAutoRevertImpersonation`.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Paramètres

*Pat*<br/>
L’adresse de l’objet [CAccessToken](../../atl/reference/caccesstoken-class.md) doit être retournée automatiquement.

### <a name="remarks"></a>Notes

L’usurpation d’identité réelle du jeton d’accès doit `CAutoRevertImpersonation` être effectuée séparément et de préférence avant la création d’un objet. Cette usurpation d’identité sera `CAutoRevertImpersonation` automatiquement retournée lorsque l’objet sortira de portée.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Détruit l’objet et retourne l’imitation symbolique d’accès.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Notes

Retourne toute usurpation d’identité actuellement en vigueur pour [l’objet CAccessToken](../../atl/reference/caccesstoken-class.md) fourni soit à la construction, soit par la méthode [Attach.](#attach) Si `CAccessToken` aucun n’est associé, le destructeur n’a aucun effet.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>CAutoRevertImpersonation::Detach

Annule le retour automatique de l’usurpation d’identité.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du [CAccessToken](../../atl/reference/caccesstoken-class.md)précédemment associé , ou NULL si aucune association n’existait.

### <a name="remarks"></a>Notes

Appeler **Detach** empêche `CAutoRevertImpersonation` l’objet de revenir à toute usurpation d’identité actuellement en vigueur pour [l’objet CAccessToken](../../atl/reference/caccesstoken-class.md) associé à cet objet. `CAutoRevertImpersonation`peut alors être détruit sans effet ou réassocié au même objet ou à l’aide `CAccessToken` d’Attache . [Attach](#attach)

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Récupère le courant symbolique d’accès associé à cet objet.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du [CAccessToken](../../atl/reference/caccesstoken-class.md)précédemment associé , ou NULL si aucune association n’existait.

### <a name="remarks"></a>Notes

Si cette méthode est appelée aux fins qui comprennent le `CAccessToken` retour d’une imitation de l’objet, la méthode [de dépôt](#detach) doit être utilisée à la place.

## <a name="see-also"></a>Voir aussi

[Échantillon d’ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Jetons d’accès](/windows/win32/SecAuthZ/access-tokens)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
