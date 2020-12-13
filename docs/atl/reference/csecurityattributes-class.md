---
description: 'En savoir plus sur : classe vue'
title: Vue, classe
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 8cb772e574aef4ad941feef1cb838fb91d937576
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140814"
---
# <a name="csecurityattributes-class"></a>Vue, classe

Cette classe est un wrapper léger pour la structure des attributs de sécurité.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Vue :: vue](#csecurityattributes)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Vue :: Set](#set)|Appelez cette méthode pour définir les attributs de l' `CSecurityAttributes` objet.|

## <a name="remarks"></a>Notes

La `SECURITY_ATTRIBUTES` structure contient un [descripteur de sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor) utilisé pour la création d’un objet et spécifie si le handle récupéré en spécifiant cette structure peut être hérité.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a> Vue :: vue

Constructeur.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor*<br/>
Référence à un descripteur de sécurité.

*bInheritsHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

## <a name="csecurityattributesset"></a><a name="set"></a> Vue :: Set

Appelez cette méthode pour définir les attributs de l' `CSecurityAttributes` objet.

```cpp
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor*<br/>
Référence à un descripteur de sécurité.

*bInheritHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

### <a name="remarks"></a>Notes

Cette méthode est utilisée par le constructeur pour initialiser l' `CSecurityAttributes` objet.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descripteur de sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
